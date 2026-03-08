---
name: agstack-farming
description: >
  Digital agriculture advisor for the Rangpur Natural Farm, Keshod, Junagadh, Gujarat -- powered
  by the AgStack Foundation (Linux Foundation) and OpenAgri ecosystem. Trigger for: farm planning,
  crop scheduling, irrigation management, ETo calculation, soil improvement tracking, pest risk,
  weather for crops, field GeoID registration, farm calendar logging, ZBNF input logging,
  Jeevamrut application records, PGS-India certification documentation, organic produce
  traceability, APMC Keshod market prices, selling produce, crop price Junagadh, demonstration
  farm data, carbon tracking, Kharif planning, Rabi planning, Bajra, Cumin, Sesame, Cowpea,
  Guar, Methi, supply chain traceability, INATrace, seasonal PDF report, soil carbon model,
  borewell emergency cross-link, AgStack tools, OpenAgri, asset-registry, field boundary.
  Calibrated for 3-Vigha smallholder natural farming in Saurashtra, Gujarat.
---

# AgStack Farming -- Open Digital Agriculture Advisor

Built on the **AgStack Foundation** (Linux Foundation) open-source ecosystem -- 41 repositories
covering field registration, weather, irrigation, pest management, farm calendars, supply chain
traceability, carbon modelling, and AI-native farm analytics.

---

## QUICK ORIENTATION

| Goal | Tool | Reference |
|------|------|-----------|
| Register your field boundary, get a GeoID | Asset Registry | `references/01-field-registry.md` |
| Get weather forecasts with crop indicators | OpenAgri Weather Service | `references/02-weather-service.md` |
| Calculate water needs (ETo), soil moisture | OpenAgri Irrigation Management | `references/03-irrigation.md` |
| Log farm operations and observations | OpenAgri Farm Calendar | `references/04-farm-calendar.md` |
| Assess pest/disease risk | OpenAgri Pest & Disease Management | `references/05-pest-disease.md` |
| Trace produce from farm to consumer | INATrace / TraceFood | `references/06-supply-chain.md` |
| Measure field-level carbon / soil health | field-carbon-model | `references/07-carbon-soil.md` |
| Build AI queries over farm knowledge graph | Pancake / Palefire | `references/08-ai-platform.md` |
| Deploy the full OpenAgri stack locally | Bootstrap Deployment | `references/09-deployment.md` |

---

## THE AGSTACK ECOSYSTEM -- 41 REPOS AT A GLANCE

### Core Infrastructure
- **asset-registry** -- Register any field polygon → receive a unique 16-char GeoID. Foundation for all field-level data.
- **user-registry** -- Account management at `user-registry.agstack.org`
- **OpenAgri-GateKeeper** -- JWT-based auth proxy for all OpenAgri microservices
- **OpenAgri-OCSM** -- Common Semantic Model: linked-data (JSON-LD) schema ensuring all services speak the same language

### Farm Management Services (OpenAgri)
- **OpenAgri-WeatherService** -- 5-day agricultural weather forecasts (temperature, humidity, wind, THI heat-stress index, rainfall probability)
- **OpenAgri-IrrigationManagement** -- ETo (Penman-Monteith, FAO-56), soil moisture analysis, irrigation scheduling
- **OpenAgri-FarmCalendar** -- Record farm operations (planting, spraying, harvesting), observations, parcel data, assets
- **OpenAgri-PestAndDiseaseManagement** -- Rule-based probabilistic pest/disease risk engine using weather + crop stage inputs
- **OpenAgri-ReportingService** -- Auto-generates PDF reports from any farm data module
- **OpenAgri-UserDashboard** -- Web UI exposing all OpenAgri services
- **OpenAgri-Bootstrap-Deployment** -- One-command Docker Compose setup of the entire stack

### Traceability
- **inatrace** (+ frontend / backend / mobile / coffee-network) -- Blockchain-based farm-to-consumer supply chain traceability
- **tracefoodchain** -- Flutter app/webapp for food chain tracing
- **TerraTrac-field-app** -- Mobile app for EUDR compliance, captures plot boundaries and deforestation risk
- **TerraTrac-validator-portal** -- Validates EUDR geolocation data

### Intelligence & AI
- **pancake** -- AI-native unified core: RAG, natural language queries, spatio-temporal search, automatic embeddings
- **palefire** -- Integrate LLMs with agricultural knowledge graphs
- **arias** -- AI assistant for agriculture
- **autogeobound** -- Automatic geo-boundary detection from satellite imagery
- **field-carbon-model** -- Field-specific carbon model using NASA SMAP L4C satellite data

### Infrastructure Modules
- **asset-registry-fe** -- Frontend for asset registry
- **OpenAgri-OCSM** -- Semantic model / ontology for interoperability
- **LF-europe** -- EU subproject for AgStack
- **governance**, **meetings** -- Community governance docs

---

## PRACTICAL FARMING WORKFLOWS

### Workflow 1 -- Set Up a New Farm (Start Here)
1. Create account at `user-registry.agstack.org`
2. Register field boundary at `asset-registry.agstack.org` → receive your GeoID
3. Deploy OpenAgri stack (see `references/09-deployment.md`)
4. Create your farm, parcels, and crops in Farm Calendar
5. Link GeoID to parcels for all future data

### Workflow 2 -- Monthly Crop Planning Cycle
```
[Weather Forecast] → [ETo/Water Budget] → [Pest Risk Check] → [Farm Calendar Entry]
         ↓                    ↓                   ↓                    ↓
  Plan field work      Schedule irrigation    Scout for pests      Log all actions
```
1. Pull 5-day weather forecast from Weather Service for your coordinates
2. Calculate ETo for the week → determine irrigation schedule
3. Run pest risk check for current crop stage and weather
4. Log planned operations in Farm Calendar
5. After harvest: run Reporting Service to generate field performance PDF

### Workflow 3 -- Natural/Organic Farm Soil Improvement Cycle
```
Season 1 → Record baseline: soil type, organic matter, water retention
Season 2 → Apply amendments → log in Farm Calendar → track ETo changes
Season 3 → Compare carbon model output → measure soil improvement
```
Tools: Farm Calendar (logs all interventions), field-carbon-model (tracks carbon), Reporting Service (documents progress for demonstration)

### Workflow 4 -- Supply Chain & Certification
1. Register each harvest batch in INATrace
2. Record inputs used (what, when, how much) in Farm Calendar
3. Generate traceability QR code → attach to produce
4. Buyers can scan and verify origin + chemical-free status
5. EUDR compliance: use TerraTrac to record and validate field boundaries

---

## KEY APIS -- QUICK REFERENCE

### Asset Registry API
```bash
# Register a field polygon
POST https://api.agstack.org/register-asset
{
  "type": "Feature",
  "geometry": {
    "type": "Polygon",
    "coordinates": [[[lon, lat], [lon, lat], ...]]
  }
}
# Returns: { "geo_id": "XXXXXXXXXXXXXXXX" }  (16-char alphanumeric)

# Fetch by lat/lon
GET https://api.agstack.org/fetch-field?lat=21.6&lon=70.2
```

### Weather Service API
```bash
# Get agricultural weather forecast
GET /api/v1/weather/forecast?lat={lat}&lon={lon}&days=5
# Returns JSON-LD with: temperature, humidity, wind, rainfall, THI, ETo estimate
```

### Irrigation Management API
```bash
# Calculate ETo (Penman-Monteith FAO-56)
POST /api/v1/irrigation/eto
{
  "date": "2025-03-01",
  "tmax": 35.0, "tmin": 22.0,
  "humidity": 60, "wind_speed": 2.5,
  "sunshine_hours": 8, "altitude": 50,
  "latitude": 21.6
}
# Returns: { "eto": 6.2 }  (mm/day)

# Soil moisture analysis
POST /api/v1/irrigation/soil-moisture
{
  "geo_id": "XXXXXXXXXXXXXXXX",
  "soil_type": "loamy",
  "recent_rainfall_mm": 12,
  "eto_mm_day": 6.2
}
```

### Farm Calendar API
```bash
# Create a farm operation record
POST /api/v1/farmcalendar/activities
{
  "@context": "https://openagri.eu/ocsm/",
  "type": "CropProtectionApplication",
  "parcel": "{geo_id}",
  "date": "2025-03-01",
  "product": "Neem oil",
  "quantity": "2L/ha",
  "notes": "Aphid control, organic"
}
```

### Pest & Disease API
```bash
# Run pest risk assessment
POST /api/v1/pest/risk-assessment
{
  "crop": "wheat",
  "growth_stage": "tillering",
  "temperature_avg": 28,
  "humidity_avg": 75,
  "rainfall_last_7days_mm": 15,
  "geo_id": "XXXXXXXXXXXXXXXX"
}
# Returns: risk score 0-1 per pest, recommended actions
```

---

## DECISION GUIDE -- WHICH TOOL FOR WHICH QUESTION

| Farmer's Question | AgStack Tool | Action |
|-------------------|--------------|--------|
| "When should I irrigate?" | IrrigationManagement | Calculate daily ETo, compare to soil moisture |
| "Will there be rain this week?" | WeatherService | Fetch 5-day forecast with crop indicators |
| "Is my crop at pest risk?" | PestDisease + Weather | Run risk assessment with current temp/humidity |
| "How do I prove my produce is chemical-free?" | INATrace + FarmCalendar | Log all inputs, generate traceability QR |
| "How is my soil carbon improving?" | field-carbon-model | Run SMAP L4C model on registered field |
| "How much water did I use this season?" | FarmCalendar + Reporting | Log all irrigation events, generate PDF report |
| "How do I register my field boundary?" | asset-registry | Draw polygon at asset-registry.agstack.org |
| "What crop should I plant next?" | FarmCalendar + Weather | Review seasonal forecast + past performance data |
| "How do I track my farm over 100 years?" | All modules + GeoID | GeoID is permanent; all data indexed to it |
| "How do I sell my produce / APMC prices?" | APMC Market + PGS logging | `references/10-apmc-pgs.md` |
| "How do I get PGS organic certification?" | Farm Calendar + PGS-India | `references/10-apmc-pgs.md` |
| "Borewell failed, irrigation emergency?" | Cross-skill: water-irrigation-emergency | Immediate crop triage + sourcing protocol |

---

## FOR YOUR NATURAL FARMING PROJECT (KESHOD, GUJARAT)

Your 1.2-acre model farm in Keshod Taluka, Junagadh is ideal for the AgStack stack:

**Phase 1 -- Register and Baseline (Week 1)**
- Register your 3-Vigha field at `asset-registry.agstack.org` (draw polygon, get GeoID)
- Link GeoID to Keshod location coordinates (~21.3 N, 70.25 E)
- Set up Farm Calendar with your 3 parcels, soil type (record baseline: loamy/clay mix, Saurashtra)
- Take baseline soil test and log results -- cross-reference with `soil-test-interpreter` skill

**Phase 2 -- Seasonal Operations (Ongoing)**
- Pull daily weather for Keshod from Weather Service API
- Calculate daily ETo -- critical for Gujarat summers (ETo often 7-9 mm/day May-June)
- Log every intervention (Jeevamrut, Beejamrut, green manure, mulching, composting) in Farm Calendar
- Run weekly pest risk checks: groundnut leaf miner, whitefly, and stem borer common in Junagadh district
- Log all inputs in PGS-India format from Day 1 -- see `references/10-apmc-pgs.md`
- Any irrigation emergency: trigger `water-irrigation-emergency` skill immediately

**Phase 3 -- Demonstration and Documentation**
- Use Reporting Service to auto-generate seasonal PDFs showing yield, water use, inputs
- Use INATrace to generate traceability certificates for your chemical-free produce
- Share GeoID with visitors so your demonstration farm data is verifiable and reproducible
- Submit PGS peer group review documentation compiled from Farm Calendar logs

**APMC Market Context (Keshod / Junagadh)**
- Primary market: APMC Keshod for daily vegetables and pulses
- Secondary market: APMC Junagadh for Cumin, Sesame, Groundnut (higher volume, better price discovery)
- Seasonal price peaks: Cumin (Feb-March Rabi harvest), Sesame (Oct-Nov post-Kharif)
- For crop price reference, mandi rate sources, and selling workflow: `references/10-apmc-pgs.md`

**Typical Junagadh crop calendar for reference:**
- Kharif (Jun-Oct): Groundnut, Bajra, Cotton, Sesame, Cowpea, Cluster Bean
- Rabi (Nov-Mar): Cumin, Methi, Coriander, Chickpea, Isabgol
- Summer (Mar-May): Vegetables, Watermelon, Fodder

---

## NATURAL FARMING PRINCIPLES + AGSTACK INTEGRATION

| Natural Farming Practice | How AgStack Helps |
|--------------------------|-------------------|
| Jeevamrut / Beejamrut preparation | Log in Farm Calendar; track crop response |
| Mulching for moisture retention | Compare ETo before/after via IrrigationManagement |
| Intercropping | Record multi-crop parcels in Farm Calendar |
| Composting cycle | Log application dates/quantities; measure carbon model trend |
| Zero chemical use | Document in FarmCalendar; generate INATrace certificate |
| Soil observation rounds | Log as "observations" in Farm Calendar |
| Rainwater harvesting | Record rainfall events; integrate with soil moisture model |

---

## CROSS-SKILL LINKS

| When you need | Go to skill |
|---|---|
| Interpret a soil test lab report, get organic amendment prescription | `soil-test-interpreter` |
| ZBNF preparations: Jeevamrut, Beejamrut, Panchgavya, lunar calendar timing | `vedic-farming` |
| Borewell failed, motor stopped, power cut, crop triage, emergency water | `water-irrigation-emergency` |
| Log a farm observation, activity, irrigation event, pest sighting | `farm-journal` |

---

## REFERENCE FILES

Read these when deeper detail is needed on a specific module:

- `references/01-field-registry.md` -- Asset Registry setup, GeoID API, TerraTrac mobile
- `references/02-weather-service.md` -- Weather API, agricultural indicators, JSON-LD format
- `references/03-irrigation.md` -- ETo calculation (Penman-Monteith), soil moisture, irrigation scheduling
- `references/04-farm-calendar.md` -- Recording operations, observations, assets, REST API
- `references/05-pest-disease.md` -- Risk rules, common pests by crop, notification setup
- `references/06-supply-chain.md` -- INATrace blockchain, EUDR compliance, QR traceability
- `references/07-carbon-soil.md` -- field-carbon-model, SMAP L4C, soil health metrics
- `references/08-ai-platform.md` -- Pancake AI core, Palefire knowledge graphs, natural language queries
- `references/09-deployment.md` -- Docker Compose full stack setup, GateKeeper auth, OCSM
- `references/10-apmc-pgs.md` -- APMC Keshod/Junagadh market context, crop price reference, PGS-India certification logging

---

## GITHUB REPOSITORIES

All code: **https://github.com/orgs/agstack/repositories**
Licenses: Apache 2.0 or EUPL 1.2 (open source, free to use and deploy)
Governance: Linux Foundation -- vendor-neutral, community-driven
