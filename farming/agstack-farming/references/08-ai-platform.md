# AI Platform -- Pancake & Palefire

## Pancake -- AI-Native Agriculture Core
**Repo**: https://github.com/agstack/pancake  
**Announced**: December 1, 2025 (OpenAgri + AgStack + Linux Foundation partnership)

### What It Does
Pancake is the "Linux kernel for digital agriculture" -- a unified AI-native core that composes all OpenAgri microservices into coherent workflows.

**Key capabilities:**
| Feature | Description |
|---------|-------------|
| RAG (Retrieval-Augmented Generation) | Query your farm data in natural language |
| Natural Language Queries | "What was my average ETo in July?" instead of API calls |
| Spatio-Temporal Search | "Show all pest events within 5km of my field in August" |
| Automatic Embeddings | Farm data automatically vectorized for AI search |
| Polyglot Data Support | Works with JSON-LD, CSV, shapefiles, images |
| GeoID Integration | All queries anchored to field-level GeoIDs |
| Unified Authentication | Single login via GateKeeper across all services |

### Architecture (What Pancake Connects)
```
┌─────────────────────────────────────────────────┐
│                    PANCAKE                       │
│  (Authentication + Semantics + Orchestration)    │
├──────────┬──────────┬──────────┬────────────────┤
│ Weather  │Irrigation│  Pest &  │  Farm Calendar │
│ Service  │  Service │ Disease  │   Service      │
├──────────┴──────────┴──────────┴────────────────┤
│         Asset Registry (GeoID Foundation)        │
└─────────────────────────────────────────────────┘
```

### Natural Language Query Examples
Once Pancake is deployed, you can ask questions like:
```
"What was my irrigation schedule last month?"
"Which parcels had pest risk above 0.7 this season?"
"Show me all Jeevamrut applications and their timing relative to rainfall"
"Compare my ETo this kharif vs last kharif"
"What organic inputs did I use in 2025?"
"Which of my fields has the best GPP trend?"
```

### Setup
```bash
git clone https://github.com/agstack/pancake.git
cd pancake
# Currently in active development -- see README for latest setup
docker compose up -d
```

---

## Palefire -- LLMs + Agricultural Knowledge Graphs
**Repo**: https://github.com/agstack/palefire  
**License**: MIT

### What It Does
Framework for integrating Large Language Models with agricultural knowledge graphs. Enables AI that "knows" about agronomy, crops, pests, soil science, and can reason over your specific farm data.

**Use cases:**
- "Given my soil type and this season's weather, what cover crop should I plant?"
- "What are the best intercropping combinations for groundnut in Saurashtra?"
- "My cumin is showing yellowing leaves after rain -- what's the likely cause?"
- "Design a 3-year soil improvement plan for my 1.2-acre organic farm"

### How It Works
```
Farm Data (GeoID + FarmCalendar + Sensors)
    ↓
Knowledge Graph (crop science + agronomy + local conditions)
    ↓
LLM (reasoning layer -- Claude, GPT, Gemini, etc.)
    ↓
Actionable recommendations with citations
```

### Setup
```bash
git clone https://github.com/agstack/palefire.git
cd palefire
pip install -r requirements.txt
# Configure LLM API key in .env
python app.py
```

---

## Arias -- Agricultural AI Assistant
**Repo**: https://github.com/agstack/arias  
AI assistant specifically designed for the agricultural domain. Minimal documentation currently -- check repo for latest status.

---

## Using AI for Your Natural Farming Project

### Immediate Use (No Setup Required)
Ask Claude (this conversation) using the AgStack skill:
- "What is the optimal Jeevamrut application schedule for groundnut in Keshod?"
- "How do I calculate water requirements for my 1.2-acre intercropped field?"
- "Build a monthly crop calendar for organic farming in Junagadh district"
- "What pest risks should I monitor in September for groundnut?"

### With Pancake Deployed (Full AI Stack)
- All your logged farm data becomes queryable in natural language
- Historical patterns surface automatically
- Recommendations improve as your data grows
- Seasonal performance comparisons across years

### With Palefire
- Deep agronomic reasoning: "Why is my yield lower than expected this season?"
- Crop planning that accounts for your specific soil, microclimate, and history
- Knowledge graph includes FAO crop calendars, ICAR recommendations, local variety data
