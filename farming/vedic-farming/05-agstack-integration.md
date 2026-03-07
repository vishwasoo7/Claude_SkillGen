# 05 - AgStack Integration
## Logging Every Vedic Practice in the AgStack Farm Calendar

This file bridges the `vedic-farming` skill with the `agstack-farming` skill.
Every traditional preparation you make should be logged in AgStack's Farm Calendar to build your demonstration farm's verifiable data trail.

---

## TABLE OF CONTENTS
1. [Why Log Vedic Practices in AgStack](#1-why-log-vedic-practices-in-agstack)
2. [Activity Type Mapping](#2-activity-type-mapping)
3. [Farm Calendar Entry Templates](#3-farm-calendar-entry-templates)
4. [Seasonal Report - What to Include](#4-seasonal-report--what-to-include)
5. [Building Your Demonstration Record](#5-building-your-demonstration-record)

---

## 1. WHY LOG VEDIC PRACTICES IN AGSTACK

Your Rangpur farm is a **demonstration model** - its purpose is to inspire other farmers. Every intervention needs to be:
- Timestamped and traceable
- Verifiable by visitors and interested farmers
- Comparable across seasons (did Jeevamrut improve yields? By how much?)
- Shareable as a chemical-free record via INATrace QR code

AgStack Farm Calendar stores all this permanently linked to your GeoID. Future visitors can audit every application you ever made.

---

## 2. ACTIVITY TYPE MAPPING

AgStack Farm Calendar uses the **OpenAgri Semantic Model (OCSM)** activity types. Here's how each Vedic practice maps:

| Vedic Practice | AgStack Activity Type | Notes |
|---------------|----------------------|-------|
| Jeevamrut (soil drench) | `SoilAmendmentApplication` | Notes: "ZBNF Jeevamrut - liquid drench" |
| Jeevamrut (foliar spray) | `CropProtectionApplication` | Notes: "ZBNF Jeevamrut - foliar" |
| Beejamrut | `SeedTreatment` | Notes: "ZBNF Beejamrut - seed coating" |
| Panchgavya | `CropProtectionApplication` | Notes: "ZBNF Panchgavya - foliar tonic" |
| Ghanjeevamrut | `SoilAmendmentApplication` | Notes: "ZBNF Ghanjeevamrut - solid base dressing" |
| Neemastra | `CropProtectionApplication` | Notes: "ZBNF Neemastra - sucking pest control" |
| Agniastra | `CropProtectionApplication` | Notes: "ZBNF Agniastra - severe pest outbreak" |
| Brahmastra | `CropProtectionApplication` | Notes: "ZBNF Brahmastra - caterpillar control" |
| Dashaparni Ark | `CropProtectionApplication` | Notes: "ZBNF Dashaparni - preventive spray" |
| Green manure incorporation | `SoilAmendmentApplication` | Notes: "Green manure - Dhaincha incorporation" |
| Vermicompost application | `SoilAmendmentApplication` | Notes: "Vermicompost - 250kg/Vigha" |
| Mulching | `SoilAmendmentApplication` | Notes: "Mulch - groundnut husk - 600kg/Vigha" |
| Lunar Tithi observation | `Observation` | Notes: "Tithi: Shukla Ekadashi - applied Jeevamrut" |

---

## 3. FARM CALENDAR ENTRY TEMPLATES

Use these as copy-paste templates for the AgStack Farm Calendar API or web UI.

### Jeevamrut Soil Drench
```json
{
  "@context": "https://openagri.eu/ocsm/",
  "type": "SoilAmendmentApplication",
  "parcel": "{your_geo_id}",
  "date": "YYYY-MM-DD",
  "product": "Jeevamrut",
  "quantity": "200L",
  "area_vigha": 1,
  "notes": "ZBNF Jeevamrut - liquid drench. Ingredients: 10kg desi cow dung, 5L cow urine, 2kg jaggery, 2kg besan, soil. Tithi: [Tithi name]. Diluted 1:1."
}
```

### Beejamrut Seed Treatment
```json
{
  "@context": "https://openagri.eu/ocsm/",
  "type": "SeedTreatment",
  "parcel": "{your_geo_id}",
  "date": "YYYY-MM-DD",
  "product": "Beejamrut",
  "crop": "[crop name]",
  "seed_qty_kg": "[quantity of seed treated]",
  "notes": "ZBNF Beejamrut - seed coating. Applied 30min before sowing. Tithi: [Tithi name]."
}
```

### Pest Control Spray (any remedy)
```json
{
  "@context": "https://openagri.eu/ocsm/",
  "type": "CropProtectionApplication",
  "parcel": "{your_geo_id}",
  "date": "YYYY-MM-DD",
  "product": "[Neemastra / Brahmastra / Agniastra / Dashaparni Ark]",
  "quantity": "20L",
  "area_vigha": 1,
  "pest_target": "[aphid / caterpillar / borer / preventive]",
  "notes": "ZBNF [remedy name]. Applied [time of day]. Tithi: [Tithi name]. Pest pressure: [low/medium/severe]."
}
```

### Mulch Application
```json
{
  "@context": "https://openagri.eu/ocsm/",
  "type": "SoilAmendmentApplication",
  "parcel": "{your_geo_id}",
  "date": "YYYY-MM-DD",
  "product": "Mulch",
  "material": "Groundnut husk",
  "quantity_kg": 600,
  "area_vigha": 1,
  "depth_inches": 3,
  "notes": "Mulch top-up. Material: groundnut shell from local harvest. Covers entire bed."
}
```

### Soil Observation (after Jeevamrut cycle)
```json
{
  "@context": "https://openagri.eu/ocsm/",
  "type": "Observation",
  "parcel": "{your_geo_id}",
  "date": "YYYY-MM-DD",
  "observation_type": "SoilHealth",
  "notes": "Soil observation - [describe texture, earthworm count, smell, color, moisture]. After [N] Jeevamrut applications. Compare to baseline: [any change noted]."
}
```

---

## 4. SEASONAL REPORT - WHAT TO INCLUDE

At the end of each season, use AgStack's **Reporting Service** to generate a PDF. Configure it to include:

### Section 1 - Inputs Used
Pull from Farm Calendar:
- All `SoilAmendmentApplication` entries → list every Jeevamrut, Ghanjeevamrut, vermicompost, mulch batch
- All `CropProtectionApplication` entries → complete pest management log
- Total quantities per Vigha

### Section 2 - Soil Observations
Pull all `Observation` entries:
- Baseline vs. end-of-season comparison
- Earthworm count (key indicator)
- Soil texture and moisture retention changes
- Any lab test results (pH, OM%) if done

### Section 3 - Crop Performance
Pull from Farm Calendar crop records:
- Yield per Vigha (manual entry)
- Crop health notes
- Pest incidence (low/medium/severe) and outcome

### Section 4 - Water Use
Pull from IrrigationManagement:
- ETo vs. actual irrigation (are you under-irrigating? Over?)
- Effect of mulching on water reduction (compare Season 1 vs. Season 2)

### Section 5 - Lunar Activity Log
Custom note section:
- Which Tithis were used for which activities
- Any notable observations (e.g., "Jeevamrut applied on Purnima - visible vigor improvement within 5 days")

---

## 5. BUILDING YOUR DEMONSTRATION RECORD

Your farm's demonstration value grows with every logged season. Here's the long-term data trail to build:

| Metric | How to Track | Tool |
|--------|-------------|------|
| Soil organic matter % | Annual lab test → log as Observation | Farm Calendar |
| Earthworm count per sq. meter | Monthly visual count → log | Farm Calendar |
| Water use per season | Log every irrigation event | IrrigationManagement |
| Yield per Vigha | Manual entry after harvest | Farm Calendar |
| Input cost per season | Note costs in entry comments | Farm Calendar |
| Pest incidence trend | Track severity in all spray entries | Farm Calendar |
| Zero chemical verification | No `CropProtectionApplication` with synthetic chemicals | INATrace auto-checks |
| Carbon model trend | Annual carbon model run | field-carbon-model |

**For visitors and other farmers:**
- Share your GeoID - they can see your entire farm record
- Generate INATrace QR code after harvest - proves zero-chemical status
- Print seasonal PDF reports - tangible, shareable demonstration evidence

**Cross-reference:** For full AgStack setup, field registration, and API details, read the `agstack-farming` skill.
