---
name: gujarat-govt-schemes
description: >
  Gujarat government schemes navigator for the Rangpur Natural Farm, Keshod,
  Junagadh, Gujarat. Trigger for: government scheme, subsidy for farmer, solar
  pump subsidy, PM-KUSUM, organic farming scheme, PKVY, Paramparagat Krishi
  Vikas Yojana, Mukhyamantri Prakrutik Kheti, ZBNF scheme Gujarat, Kisan Credit
  Card, KCC loan, soil health card, ATMA scheme, NHM horticulture subsidy, MIDH,
  i-Khedut, ikhedut.gujarat.gov.in, apply for subsidy, what schemes am I eligible
  for, government help for organic farming, free soil test government, farm pond
  subsidy, drip irrigation subsidy, how to apply government scheme Gujarat, which
  scheme for natural farming, RKVY, agri subsidy Junagadh, scheme application
  documents, new farming scheme Gujarat 2025 2026. Calibrated for a 3-Vigha
  solar pump for borewell subsidy, Kisan Credit Card apply, smallholder natural
  farming transition in Keshod Taluka, Junagadh district. Always performs live
  web search to verify current scheme status before responding.
---

# Gujarat Government Schemes Navigator
## Keshod Farm -- Find, Verify, and Apply for Active Schemes

Government schemes in India change every year. Benefit amounts are revised in Union
and State budgets. Application windows open and close. Some schemes lapse; new ones
are announced. This skill always searches the web before presenting scheme details
to ensure you are acting on current information, not stale data.

---

## LIVE VERIFICATION PROTOCOL

**Every time this skill is invoked, Claude runs these steps before presenting any scheme information:**

**Step 1 -- Verify the specific scheme asked about (or top 3 priority schemes if general query):**
Run web search using the query template from each scheme profile in `references/01-scheme-details.md`.
Standard query format: `[scheme name] Gujarat 2026 farmer eligibility benefit`

**Step 2 -- Check for new schemes (run once per session, on any government scheme query):**
Search: `Gujarat government new farming scheme 2025 2026 organic natural`
Search: `ikhedut.gujarat.gov.in new scheme 2025 2026`
If results mention a scheme not in this skill's reference files: present it with a note
that it is newly identified and not yet in the permanent skill record.

**Step 3 -- Apply the staleness signals:**
Each scheme profile in ref01 lists specific "Change Indicator" signals.
If search results show any of these signals, present the updated information and
flag the change explicitly: "Terms have changed since this skill was last updated."

**Step 4 -- Lapsed scheme detection:**
If a web search for a scheme returns no results from the past 18 months, or if
official sources describe the scheme in past tense, flag it:
"This scheme may have lapsed or been restructured. Verify at i-Khedut portal
(ikhedut.gujarat.gov.in) or with your Taluka Agriculture Officer before applying."

**Trusted sources (in order of reliability):**
1. ikhedut.gujarat.gov.in (Gujarat's official scheme portal -- ground truth)
2. agricoop.nic.in (Central Ministry of Agriculture)
3. pib.gov.in (Press Information Bureau -- scheme announcements)
4. agri.gujarat.gov.in (Gujarat Agriculture Department)
5. kvk.icar.gov.in (KVK network announcements)
6. eauction.apmc.in (for any APMC-linked scheme updates)

---

## QUICK SCHEME LOOKUP TABLE

Use this to identify which schemes apply to your situation right now.

| Scheme | What It Pays | Your Status | When to Apply |
|---|---|---|---|
| PM-KUSUM (B) | 60-90% solar pump cost | Eligible from Year 1 -- borewell exists | Apply before Kharif (Mar-May window typical) |
| Soil Health Card | Free soil test | Eligible any time | Apply before April 2026 baseline test |
| PKVY | Rs 50,000/ha over 3 years | Eligible from Year 1 -- organic transition | Apply with group of 20+ farmers |
| Mukhyamantri Prakrutik Kheti | Rs 2,500-5,000/Vigha | Eligible Year 1 if registered | Verify current budget allocation first |
| ATMA | Free training, exposure visits | Eligible any time | Register with Taluka Agriculture Office |
| Kisan Credit Card | Rs 3L loan at 4% interest | Eligible with land record | Apply at any nationalised bank before sowing |
| NHM / MIDH | 50% drip irrigation cost | Eligible Year 3+ (after vegetables) | Apply Oct-Nov before Rabi planting |

---

## PRIORITY SEQUENCE -- WHAT TO APPLY FOR FIRST

**Why sequence matters:** Some schemes require PGS certificate (get that first).
Some have application windows that close (miss them and wait a full year).
Some require a farmer group (form group first, then apply).

```
IMMEDIATE (April-May 2026, before Kharif sowing):
  1. Soil Health Card -- free, fast, no group needed, baseline documentation
  2. Kisan Credit Card -- working capital for Year 1 inputs
  3. ATMA registration -- free training, opens door to other scheme access

BEFORE KHARIF 2026 SOWING:
  4. PM-KUSUM Component B -- solar pump subsidy application window
  5. Mukhyamantri Prakrutik Kheti Yojana -- Year 1 ZBNF registration

AFTER FIRST PGS CERTIFICATE (March 2027):
  6. PKVY -- requires organic group and documentation; PGS certificate strengthens application

YEAR 3+ (after vegetable/horticulture crops established):
  7. NHM / MIDH -- drip irrigation, horticulture infrastructure
```

---

## WHAT REQUIRES A PGS CERTIFICATE

Several scheme benefits specifically recognise or require organic certification:
- PKVY: organic cluster scheme -- PGS documentation is central evidence
- Premium price support at APMC: PGS certificate required to claim organic premium
- Some NHM components: certified organic farms get priority scoring

This means completing pgs-india-roadmap work (targeting March 2027 certificate)
directly unlocks additional scheme eligibility in Year 2 and beyond.

---

## WHAT REQUIRES A FARMER GROUP

Three schemes require a group formation before applying:
- **PKVY**: minimum 20 farmers in an organic cluster (50 acres aggregate minimum)
- **ATMA**: farmer interest groups for training programmes
- **Mukhyamantri Prakrutik Kheti Yojana**: district-level registration often done through groups

Your PGS peer group (5 members minimum, formed for certification) is a starting point
but will likely need to expand to meet PKVY's 20-farmer requirement.
KVK Junagadh maintains lists of interested natural farming practitioners in the district.

---

## CROSS-SKILL LINKS

| Need | Skill |
|---|---|
| PGS certification (required for several schemes) | `pgs-india-roadmap` |
| Solar pump upgrade path and borewell backup planning | `water-irrigation-emergency` -> `references/01-crop-water-tolerance.md` (Prevention section) |
| Soil test results for Soil Health Card comparison | `soil-test-interpreter` |
| ZBNF farming records that satisfy PKVY documentation | `vedic-farming` + `farm-journal` |
| Farm Calendar logs that serve as scheme evidence | `agstack-farming` -> `references/04-farm-calendar.md` |

---

## REFERENCE FILES

| File | When to Read |
|---|---|
| `references/01-scheme-details.md` | Full profile of each scheme: benefit amount, eligibility, documents needed, application deadline, where to apply, live search query, change indicators |
| `references/02-ikhedut-application-guide.md` | i-Khedut portal step-by-step guide, master documents checklist, how to find new schemes, offline application fallback |
