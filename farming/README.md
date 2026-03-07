# Farming Skills

This category contains Claude skills built specifically for natural and organic farming operations. All skills have been calibrated for Saurashtra and Gujarat conditions, including local soil chemistry, available organic inputs, and regional crop calendars.

These skills are designed to support a Subhash Palekar Zero Budget Natural Farming approach from soil preparation through crop management, with a focus on chemical-free inputs and soil restoration.

---

## Skills in This Category

### agstack-farming

**File:** [agstack-farming/SKILL.md](./agstack-farming/SKILL.md)
**Lines:** 274
**Source:** AgStack Foundation (Linux Foundation) and OpenAgri ecosystem

This skill turns Claude into a digital agriculture advisor using open-source tools from the AgStack Foundation. It covers evapotranspiration (ETo) calculations, pest risk assessments, Gujarat-specific crop calendars, field boundary management, supply chain traceability, and carbon credit tracking.

Activate when asking about crop planning, irrigation scheduling, weather data for crops, pest pressure forecasting, or deploying AgStack tools such as asset-registry, OpenAgri services, INATrace, Pancake, Palefire, TerraTrac, or field-carbon-model.

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
**Lines:** 140
**Source:** Custom-built for VP Farm Project

This skill reads Indian soil laboratory reports and converts raw test values into specific organic amendment prescriptions. All dosages are calculated per Vigha and use organic inputs only. It is calibrated for alkaline loamy-clay soils common in the Saurashtra and Junagadh region.

Activate when uploading a soil report PDF or image, or when asking about pH correction, OC percentage, NPK values, EC readings, micronutrient deficiencies (zinc, boron, iron, sulphur), GSFC lab results, or KVK Krishi Vigyan Kendra reports.

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
