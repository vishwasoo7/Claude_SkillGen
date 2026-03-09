---
name: github-connect
description: >
  GitHub connector skill for Claude. Use whenever the user wants to push files,
  push a skill, update a README, create a folder, sync all skills, or inspect a
  GitHub repository. Triggers on: GitHub token, PAT, personal access token,
  push to GitHub, connect GitHub, git push, git commit, sync repo, clone repo,
  update repo, github-connect, ghp_, github_pat_, repo URL, .git URL, push skill,
  push files, create branch, commit files, inspect repository. Works across all
  platforms: claude.ai, Claude Code, Claude Desktop, API, any environment with
  bash and git available.
---

# GitHub Connect

A structured, safe GitHub operations skill. The user declares a token, repo URL,
and intended action upfront. Claude executes, verifies, and reports.

---

## Platform Detection

Run this at the start of every session to confirm the environment is ready:

```bash
git --version && echo "git: OK" || echo "git: NOT AVAILABLE"
bash --version | head -1 && echo "bash: OK" || echo "bash: NOT AVAILABLE"
```

**If git is not available:** Inform the user that this skill requires a Claude
environment with bash and git access (claude.ai with computer use, Claude Code,
or a self-hosted API setup). Pure chat-only interfaces without computer access
cannot execute git commands.

**If git is available:** Proceed with the session protocol below.

---

## Required Inputs (Every Session)

Ask for all three if not already provided:

| Input | Format | Example |
|-------|--------|---------|
| Token | `ghp_...` or `github_pat_...` | `ghp_abc123...` |
| Repo URL | HTTPS `.git` URL | `https://github.com/user/repo.git` |
| Intended action | One of the 6 actions below | `push-skill` |

**Token validation:**
```bash
# Check format before proceeding
if [[ "$TOKEN" =~ ^ghp_[a-zA-Z0-9]{36}$ ]] || [[ "$TOKEN" =~ ^github_pat_ ]]; then
  echo "Token format: valid"
else
  echo "Token format: unrecognized - check for typos or expired token"
fi
```

**Repo URL validation:**
```bash
if [[ "$REPO_URL" =~ ^https://github\.com/.+/.+\.git$ ]]; then
  echo "URL format: valid"
else
  echo "URL format: expected https://github.com/user/repo.git"
fi
```

---

## Supported Actions

| Action | What it does |
|--------|-------------|
| `push-files` | Copy specified local files or folders into the repo and push |
| `push-skill` | Copy a named skill from `/mnt/skills/user/` into the correct category folder and push |
| `update-readme` | Edit a specific README in the repo and push |
| `create-folder` | Create a new categorized folder with a README stub and push |
| `sync-all` | Re-sync all skills from `/mnt/skills/user/` to the repo (full refresh) |
| `inspect` | Clone and report current repo structure without making any changes |

---

## Execution Protocol

Apply this sequence for every action without exception.

### Stage 1: Setup

```bash
# Embed token in URL for authentication
REPO_AUTH="${REPO_URL/https:\/\//https:\/\/$TOKEN@}"

# Clone into a clean working directory
WORKDIR="/tmp/ghconnect_$(date +%s)"
git clone "$REPO_AUTH" "$WORKDIR"
cd "$WORKDIR"

# Set identity (required for commits)
git config user.name "Claude GitHub Connect"
git config user.email "claude-skill@noreply.github.com"

echo "Setup complete. Working in: $WORKDIR"
git log --oneline -3
```

### Stage 2: Execute Action

**push-files**
```bash
# USER PROVIDES: list of source paths
cp -r "$SOURCE_PATH" "$WORKDIR/$DEST_PATH"
```

**push-skill**
```bash
# USER PROVIDES: skill name and target category folder
SKILL_SRC="/mnt/skills/user/$SKILL_NAME"
SKILL_DEST="$WORKDIR/$CATEGORY/$SKILL_NAME"
mkdir -p "$SKILL_DEST"
cp -r "$SKILL_SRC/." "$SKILL_DEST/"
```

**update-readme**
```bash
# Edit the target README directly
# Then stage: git add "$TARGET_README"
```

**create-folder**
```bash
mkdir -p "$WORKDIR/$CATEGORY/$FOLDER_NAME"
cat > "$WORKDIR/$CATEGORY/$FOLDER_NAME/README.md" << 'EOF'
# Folder Name

Description placeholder. Update before pushing to production.
EOF
```

**sync-all**
```bash
# For each skill in /mnt/skills/user/ with a known category mapping:
for SKILL in /mnt/skills/user/*/; do
  SKILL_NAME=$(basename "$SKILL")
  CATEGORY=$(map_to_category "$SKILL_NAME")  # see category map below
  mkdir -p "$WORKDIR/$CATEGORY/$SKILL_NAME"
  cp -r "$SKILL/." "$WORKDIR/$CATEGORY/$SKILL_NAME/"
done
```

**inspect**
```bash
echo "=== Repository structure ==="
find "$WORKDIR" -not -path '*/.git/*' | sort
echo ""
echo "=== Recent commits ==="
git log --oneline -10
echo ""
echo "=== Current branch ==="
git branch --show-current
# No changes made. Stop here.
```

### Stage 3: Verify Before Committing

**This stage is mandatory. Never skip.**

```bash
echo "=== Changed files ==="
git diff --stat

echo "=== Staged files ==="
git status --short

echo "=== Em dash check ==="
grep -rPn "\xe2\x80\x94" . --exclude-dir=.git && echo "FAIL: em dashes found" || echo "PASS"

echo "=== Personal info check ==="
# Add project-specific personal info terms to this pattern before use
grep -rn "PERSONAL_TERM_1\|PERSONAL_TERM_2" . --exclude-dir=.git \
  && echo "WARN: review before committing" || echo "PASS"
```

Read the diff output. Confirm the changes match what was intended. If anything
is unexpected, stop and report to the user before proceeding.

### Stage 4: Commit and Push

```bash
# Commit with a descriptive message
git add -A
git commit -m "$COMMIT_MESSAGE"

# Push to main
git push origin main

# Report result
echo "=== Push complete ==="
git log --oneline -1
echo "Commit hash: $(git rev-parse HEAD)"
```

### Stage 5: Report

Always report the following after every successful push:

- Action taken
- Files changed (from git diff --stat)
- Commit message used
- Commit hash
- Token reminder (see Security section)

---

## Category Map (for push-skill and sync-all)

```
farming:          agstack-farming, vedic-farming, soil-test-interpreter,
                  farm-journal, water-irrigation-emergency, pgs-india-roadmap,
                  seasonal-crop-rotation-planner, gujarat-govt-schemes
ai-agents:        brainstorming, dispatching-parallel-agents, parallel-agents,
                  memory-systems, loki-mode, using-superpowers, skill-router
skill-management: skill-developer, verification-before-completion, github-connect
engineering:      kaizen, rag-engineer, prompt-engineer, prompt-engineering-patterns
startup-business: startup-analyst, startup-business-analyst-business-case,
                  startup-business-analyst-financial-projections,
                  startup-financial-modeling, startup-metrics-framework,
                  team-composition-analysis, competitive-landscape,
                  market-sizing-analysis, pricing-strategy
```

For any skill not in this map, ask the user which category folder to use before proceeding.

---

## Error Reference

| Error | Cause | Response |
|-------|-------|----------|
| `exit code 128 / not found` | Repo URL wrong or repo is private with wrong token | Check URL spelling. Confirm token has `repo` scope. |
| `403 Forbidden` | Token invalid, expired, or missing `repo` scope | Ask user to regenerate PAT with `repo` scope at github.com/settings/tokens |
| `nothing to commit` | Files unchanged since last push | Report cleanly. Do not claim a push occurred. |
| `CONFLICT` | Remote has changes not in local clone | Report conflict. Do not force push. Ask user to resolve manually. |
| `host_not_allowed` on api.github.com | Anthropic proxy blocks REST API | Only git operations work. Do not attempt REST API calls. |
| `git: command not found` | Environment has no git | Inform user this skill needs a computer-use enabled environment. |

---

## Security Rules

These rules are non-negotiable and apply to every session:

1. Never print the token to any file, log, or output that could be committed.
2. Never commit a file that contains the token string.
3. Never force push (`git push --force`).
4. Always use `https://TOKEN@github.com/...` format, never store in `.git/config`.
5. After every session, remind the user:

```
Security reminder: if this token was shared in a chat interface, regenerate it at
github.com/settings/tokens before your next session. Tokens shared in chat are
visible in conversation history.
```

---

## Commit Message Templates

Use these as the base, then append specifics:

| Action | Template |
|--------|----------|
| push-files | `Add [filename/folder]: [brief description]` |
| push-skill | `Add skill: [skill-name] to [category]/` |
| update-readme | `Update README: [category or folder name]` |
| create-folder | `Create folder: [category/folder-name] with README stub` |
| sync-all | `Sync all skills from /mnt/skills/user/ - [date]` |

---

## Quick Start (Copy-Paste)

```
Token:  ghp_yourtoken
Repo:   https://github.com/username/reponame.git
Action: push-skill
Skill:  github-connect
Category: skill-management
```

Claude will handle setup, execution, verification, commit, push, and report.
