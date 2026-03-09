# Farming Skills

This category contains Claude skills built specifically for natural and organic farming operations. All skills have been calibrated for Saurashtra and Gujarat conditions, including local soil chemistry, available organic inputs, and regional crop calendars.

These skills are designed to support a Subhash Palekar Zero Budget Natural Farming approach from soil preparation through crop management, with a focus on chemical-free inputs and soil restoration.

---

## Skills in This Category

### agstack-farming

**File:** [agstack-farming/SKILL.md](./agstack-farming/SKILL.md)
**Lines:** 300 (SKILL.md) + 10 reference files (1,348 lines)
**Source:** AgStack Foundation (Linux Foundation) + OpenAgri ecosystem

Digital agriculture advisor for the Rangpur Natural Farm, Keshod, Junagadh, Gujarat. Covers field GeoID registration, ETo and irrigation management, pest risk, farm calendar logging, ZBNF input logging, PGS-India certification documentation, APMC market intelligence, supply chain traceability, carbon tracking, and full OpenAgri stack deployment.

Reference file 10 covers APMC Keshod and Junagadh market structure, crop price reference for all Phase 1 crops (Cumin, Sesame, Bajra, Cowpea, Guar, Methi) with MSP and APMC ranges, step-by-step selling workflow, Farm Calendar log formats for each sale, PGS-India certification process, PGS documentation logging from Day 1, peer group formation, and INATrace vs PGS comparison.

Cross-linked to: soil-test-interpreter, vedic-farming, water-irrigation-emergency, farm-journal.

Activate for: APMC prices, selling produce, PGS certification, crop planning, irrigation scheduling, weather data, pest pressure, Jeevamrut logging, demonstration farm documentation, or any AgStack/OpenAgri tool deployment.

---

### vedic-farming

**File:** [vedic-farming/SKILL.md](./vedic-farming/SKILL.md)
**Lines:** 196 (SKILL.md) + 7 reference files
**Source:** Custom-built for VP Farm Project

This skill provides guidance on traditional and Vedic natural farming methods based on Subhash Palekar's Zero Budget Natural Farming (ZBNF) system. It covers all major fermented preparations (Jeevamrut, Beejamrut, Panchgavya, Ghanjeevamrut), organic pest sprays (Neemastra, Agniastra, Brahmastra, Dashaparni Ark), lunar calendar planting, seed treatment, cow resource constraint management, and local material sourcing for the Keshod area. Includes a full chemical land detox and bioremediation protocol for transitioning from chemically abused soil, and crop-specific ZBNF guides for groundnut, cumin, sesame, bajra, vegetables, and Kali Jeeri.

Activate when asking about any ZBNF preparation, how to handle chemically damaged soil, crop-specific application schedules, Tithi-based planting, limited cow dung sourcing, or what to do immediately after the Kali Jeeri harvest.

---

### soil-test-interpreter

**File:** [soil-test-interpreter/SKILL.md](./soil-test-interpreter/SKILL.md)
**Lines:** 208 (SKILL.md) + 6 reference files (1,255 lines)
**Source:** Custom-built for VP Farm Project

This skill reads Indian soil laboratory reports and converts raw test values into specific organic amendment prescriptions. All dosages are calculated per Vigha and use organic inputs only. Calibrated for alkaline loamy-clay soils in the Saurashtra and Junagadh region.

Includes a Chemical Detox Context section for interpreting Year 1 soil tests on land previously under heavy synthetic inputs -- covering parameter-by-parameter interpretation adjustments, reduced-dose prescription rules, and season-by-season recovery targets. A Re-Testing Schedule section provides a 5-test minimum calendar with season-on-season improvement benchmarks and warning signals for slow recovery.

Reference file 06 covers cover crop prescriptions (Dhaincha, Sunn Hemp, Cowpea, Cluster Bean, Mustard with per-Vigha seed rates and Keshod sourcing), bioremediation inputs, recovery troubleshooting, and farm journal integration for PGS documentation.

Activate when uploading a soil report PDF or image, pasting raw test values, asking about pH correction, OC percentage, NPK values, EC readings, micronutrient deficiencies, GSFC or KVK lab results, or when asking how to track soil recovery over seasons.

---

### farm-journal

**File:** [farm-journal/SKILL.md](./farm-journal/SKILL.md)
**Lines:** 381
**Source:** Custom-built for VP Farm Project

A structured farm observation and activity logging system with 7 entry types: Soil Observation, Preparation Log, Crop Observation, Irrigation/Water Log, Pest/Disease Event, Harvest Record, and Seasonal Summary. All templates are calibrated to the Rangpur village farm context. Includes a Soil Recovery Milestones tracker for monitoring chemical detox progress season over season, and review prompts for comparing seasonal data. Data logged here feeds directly into AgStack Farm Calendar entries and provides PGS-India certification evidence.

Activate when recording any farm observation, logging a preparation batch, noting a pest sighting, capturing an irrigation event, recording a harvest result, or running a seasonal summary.

---

## Status

All 4 skills are production-ready and have been validated for use on the VP Farm Project.

---

## Farm Context

| Detail | Value |
|--------|-------|
| Farm name | Rangpur Natural Farm |
| Size | 1.2 acres (3 Vigha) |
| Method | Subhash Palekar ZBNF with organic transition |
| Phase 1 start | April to May 2026 |
| Soil type | Alkaline loamy-clay |
| Water source | Borewell with electric submersible motor |

---

## How to Install

Copy any skill folder to `/mnt/skills/user/` in your Claude environment. The skill activates automatically when a matching task or keyword is detected in your conversation.

Example:
```
cp -r agstack-farming/ /mnt/skills/user/
```

---

### water-irrigation-emergency

**File:** [water-irrigation-emergency/SKILL.md](./water-irrigation-emergency/SKILL.md)
**Lines:** 200 (SKILL.md) + 1 reference file (337 lines)
**Source:** Custom-built for VP Farm Project

Emergency response protocol for the single-borewell, grid-power irrigation system at Rangpur Natural Farm, Keshod. Covers all three failure modes: grid power cut, motor or pump failure, and borewell water level drop.

SKILL.md contains a Three Failure Modes identification table, a four-step Immediate Action Protocol (first 60 minutes), a Decision Tree with actions at four outage duration branches, an Emergency Water Sources table with six Keshod-area options and INR costs, a Water Rationing priority guide, and a Soil Moisture Check method using the loamy-clay buffer advantage.

Reference file 01 covers crop survival windows for all Kharif and Rabi crops, growth stage vulnerability, triage priority by season, water rationing calculator with survival doses, 5-day outage cost comparison, recovery actions using Jeevamrut and Panchgavya after stress, a prevention and preparedness checklist, a borewell and motor maintenance calendar, and a long-term upgrade path from no-backup to solar pump and farm pond.

Activate immediately when: borewell fails, motor stops, power cut, pump not working, crops wilting, water shortage, water tanker needed, generator rental, which crops to save first, or any irrigation emergency.

---

### pgs-india-roadmap

**File:** [pgs-india-roadmap/SKILL.md](./pgs-india-roadmap/SKILL.md)
**Lines:** 122 (SKILL.md) + 2 reference files (832 lines)
**Source:** Custom-built for VP Farm Project

Step-by-step PGS-India (Participatory Guarantee System) certification roadmap for the Rangpur Natural Farm. Covers the full journey from April 2026 (Day 1 post Kali Jeeri harvest) to March 2027 (first PGS Scope Certificate).

Reference file 01 is a month-by-month action plan across three phases: Phase A (foundation -- baseline soil test, farm description, peer group formation, KVK registration, NCOF portal setup), Phase B (Kharif 2026 logging -- opening declaration, Beejamrut and Jeevamrut log templates, weekly observation format, peer inspection, harvest documentation), and Phase C (Rabi 2026-27 through application -- evidence file compilation, group review, second inspection, NCOF portal and KVK physical submission). Includes master documentation checklist and a 6-scenario recovery table for missed steps.

Reference file 02 covers the peer inspection protocol with a full fillable inspection record template, group constitution template, individual farm declaration template, KVK Junagadh address and contact, NCOF portal step-by-step guide, how to use the certificate at APMC and for government schemes, annual renewal requirements, and problem handling for synthetic input violations and application rejections.

Cross-linked to: agstack-farming (Farm Calendar log formats), soil-test-interpreter, vedic-farming, farm-journal.

---

### seasonal-crop-rotation-planner

**File:** [seasonal-crop-rotation-planner/SKILL.md](./seasonal-crop-rotation-planner/SKILL.md)
**Lines:** 156 (SKILL.md) + 2 reference files (596 lines)
**Source:** Custom-built for VP Farm Project

Five-year crop rotation and succession planner for the Rangpur Natural Farm.
Integrates soil recovery logic into every planting decision from Kharif 2026 through Rabi 2030-31.

SKILL.md provides three entry points (next season planning, crop profile lookup, intercropping check),
five core rotation principles (no bare soil, legume every season, deep root before shallow, high-demand
after soil-building, income every season), three decision scenarios (planning ahead, failed Kharif recovery,
soil-test-driven rotation), and a year-by-year arc from bioremediation to demonstration farm maturity.

Reference file 01 is a season-by-season rotation table for all five years: Year 1 starts with Dhaincha
pre-crop on all parcels then Bajra, Cowpea, Sesame Kharif with income estimates Rs 31,550-70,000; Cumin
introduced at 0.5 Vigha in Rabi 2026-27; Year 2 first Groundnut trial and full-Vigha Cumin; Year 3
two-parcel Cumin with OC guard condition; Year 4 vegetables trial and Rs 2-3.5L income projection; Year 5
stable self-reinforcing rotation. Also covers between-season gap crops and five failure adaptation scenarios.

Reference file 02 has full profiles for 10 crops (Bajra, Sesame, Cowpea, Cluster Bean, Groundnut, Cumin,
Methi, Coriander, Chickpea, Isabgol) each with sowing window, ZBNF yield, soil impact, rotation role, APMC
notes, and Keshod-specific guidance. Also includes Dhaincha and Mustard cover crop profiles, seven proven
intercropping combinations for Saurashtra climate, and a Kharif-to-Rabi succession windows table.

Cross-linked to: agstack-farming (prices, Farm Calendar), water-irrigation-emergency (drought tolerance),
soil-test-interpreter (amendment prescriptions, cover crop protocol), vedic-farming (ZBNF inputs, lunar
calendar), farm-journal.

---

### gujarat-govt-schemes

**File:** [gujarat-govt-schemes/SKILL.md](./gujarat-govt-schemes/SKILL.md)
**Lines:** 148 (SKILL.md) + 2 reference files (695 lines)
**Source:** Custom-built for VP Farm Project

Gujarat government schemes navigator for the Rangpur Natural Farm. Covers 7 key
schemes with a live verification layer -- every invocation runs targeted web searches
to confirm current benefit amounts, eligibility, and application windows before
presenting any information. Flags lapsed schemes and surfaces newly announced ones.

SKILL.md contains the Live Verification Protocol (4-step search process, trusted
source hierarchy from ikhedut.gujarat.gov.in to pib.gov.in, lapsed scheme detection
rule), a Quick Scheme Lookup Table, a Priority Sequence (Immediate / Before Kharif /
Post-PGS Certificate / Year 3+), and notes on what requires a PGS certificate and
what requires a farmer group.

Reference file 01 has full profiles for all 7 schemes: PM-KUSUM Component B (60-90%
solar pump subsidy -- highest priority for borewell backup), Soil Health Card (free
12-parameter test), PKVY (Rs 50,000/ha over 3 years, 20-farmer cluster path from
PGS peer group), Mukhyamantri Prakrutik Kheti Yojana (ZBNF state support with
variable-budget caveat), ATMA (demonstration farm recognition and scheme access
pathway), Kisan Credit Card (Rs 3 lakh at 4% effective rate), and NHM/MIDH (55%
drip irrigation subsidy, Year 3+ timing). Each profile has a VERIFY LIVE search
query, Change Indicator signals, document checklist, and farm-specific rationale.
Section 8 covers how to identify newly announced schemes via Union Budget, State
Budget, quarterly i-Khedut scans, and seasonal circulars.

Reference file 02 is the i-Khedut portal guide: 8-step application process from
registration to disbursement, master documents checklist, quarterly new-scheme
discovery method, application status tracking, 8 common rejection reasons with
prevention, offline fallback via CSC and Taluka Agriculture Office, and key
contacts for 8 offices in Junagadh district.

Cross-linked to: pgs-india-roadmap, water-irrigation-emergency, soil-test-interpreter,
vedic-farming, farm-journal, agstack-farming.

