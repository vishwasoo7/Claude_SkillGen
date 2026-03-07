---
name: soil-test-interpreter
description: >
  Interprets Indian soil test lab reports and converts raw numbers into specific organic
  amendment prescriptions per Vigha. Always trigger this skill when the user uploads a soil
  report PDF, image, or photo of a lab report, or mentions soil test, soil report, soil
  analysis, soil health card, NPK values, pH reading, OC percentage, organic carbon, available
  nitrogen, available phosphorus, available potassium, EC value, electrical conductivity,
  micronutrient deficiency, zinc deficiency, boron deficiency, iron deficiency, sulphur
  deficiency, GSFC lab, KVK lab, Krishi Vigyan Kendra result, or asks "what does my soil
  test mean", "how to fix my soil", "my pH is high", "what should I apply based on my
  test", or shares any numbers from a lab report. Also trigger when user describes crop
  symptoms that suggest a nutrient problem. All prescriptions use organic inputs only.
  All dosages are per 1 Vigha: multiply by total Vigha count. Calibrated for
  Saurashtra / Junagadh / Gujarat alkaline loamy-clay soil.
---

# Soil Test Interpreter
## Lab Report → Organic Amendment Prescription
### Calibrated for Saurashtra, Gujarat

All amendment quantities are **per 1 Vigha (≈ 0.4 acres)**.
For your 3-Vigha farm: **multiply every quantity × 3**.

---

## HOW TO USE THIS SKILL

**Three entry points: all supported:**

**A) Upload your lab report (PDF or image)**
Upload the file directly in chat. I will extract all parameter values automatically,
classify each one, and generate a prioritized organic correction plan.
Supported formats: PDF, JPG, PNG, scanned photo of paper report.

**B) Paste your numbers**
Type or paste raw values (e.g., "pH 8.1, OC 0.42%, N 210 kg/ha, Zn 0.31") -
I classify and prescribe immediately.

**C) Describe a crop symptom**
Describe what the plant or soil looks like → I identify the likely deficiency →
I recommend which test to get and which organic fix to start now.

---

## ALL PARAMETERS: STATUS AT A GLANCE

| Parameter | Unit | Low ⚠️ | Medium ✅ | High / Good | Problem |
|-----------|------|--------|----------|-------------|---------|
| **pH** |: | <6.5 | 6.5–7.5 | 7.5–8.5 (Saurashtra normal) | >8.5 🚨 |
| **EC** | dS/m | <0.25 | 0.25–0.75 | 0.75–2.0 caution | >2.0 🚨 |
| **Organic Carbon (OC)** | % | <0.5 🚨 | 0.5–0.75 | 0.75–1.0 | >1.0 ✅ |
| **Available N** | kg/ha | <280 | 280–560 ✅ | >560 |: |
| **Available P** | kg/ha | <10 | 10–25 ✅ | >25 |: |
| **Available K** | kg/ha | <108 | 108–280 ✅ | >280 |: |
| **Zinc (Zn)** | mg/kg | <0.6 🚨 | 0.6–1.2 ✅ | >1.2 |: |
| **Iron (Fe)** | mg/kg | <4.5 | 4.5–9.0 ✅ | >9.0 |: |
| **Manganese (Mn)** | mg/kg | <2.0 | 2.0–5.0 ✅ | >5.0 |: |
| **Copper (Cu)** | mg/kg | <0.2 | 0.2–0.5 ✅ | >0.5 |: |
| **Boron (B)** | mg/kg | <0.5 🚨 | 0.5–1.0 ✅ | >1.0 |: |
| **Sulphur (S)** | mg/kg | <10 | 10–20 ✅ | >20 |: |

> **Unit note:** mg/kg = ppm (identical). Some labs report N in kg/ha, others as %.
> Per-Vigha conversion: divide kg/ha values by 2.47.
> OC vs OM: OM% = OC% × 1.724 (if your report shows OM, divide by 1.724 to get OC).

---

## PRIORITY CORRECTION ORDER

**Always fix in this sequence: skipping steps wastes inputs:**

```
1. pH first     : if >8.5 or <6.5, nutrients are locked regardless of quantities
2. OC / Organic Carbon: foundation for all microbial activity and nutrient cycling
3. Macronutrients: N, then P, then K
4. Micronutrients: Zn first (most common in Saurashtra), then B, S, Fe
5. EC last      : salinity managed separately, doesn't interact with nutrient fixes
```

**Why this order:** pH >8.0 locks P and Zn even when they exist in soil.
Low OC means microbes cannot cycle any nutrient inputs you apply.
Always build the foundation before adding inputs on top.

---

## QUICK AMENDMENT TABLE: Per 1 Vigha

| Parameter | Status | First Organic Fix | Per Vigha Qty | Full Detail |
|-----------|--------|------------------|---------------|-------------|
| pH | >8.5 | Gypsum | 50 kg | `04-ph-ec-corrections.md` |
| pH | <6.5 | Lime (chuna) | 50 kg | `04-ph-ec-corrections.md` |
| OC | <0.5% | Jeevamrut + vermicompost + green manure | 200L + 400kg + 5kg seed | `02-macronutrient-corrections.md` |
| N | Low | Jeevamrut + neem cake + green manure | 200L + 50kg + 5kg seed | `02-macronutrient-corrections.md` |
| P | Low | Rock phosphate + vermicompost | 50 kg + 200 kg | `02-macronutrient-corrections.md` |
| K | Low | Wood ash + vermicompost | 50 kg + 200 kg | `02-macronutrient-corrections.md` |
| Zn | <0.6 | Neem cake + Jeevamrut + ZnSO₄ | 50kg + 200L + 5kg | `03-micronutrient-corrections.md` |
| B | <0.5 | Borax foliar + vermicompost | 1kg/200L water + 300kg | `03-micronutrient-corrections.md` |
| S | <10 | Gypsum + mustard cake | 40 kg + 50 kg | `03-micronutrient-corrections.md` |
| EC | >2.0 | Leaching + gypsum | 50 kg | `04-ph-ec-corrections.md` |

---

## REFERENCE FILES

| File | When to Read |
|------|-------------|
| `references/01-parameter-ranges.md` | Full classification tables, unit conversions, per-Vigha math |
| `references/02-macronutrient-corrections.md` | Full N, P, K, OC correction protocols with per-Vigha doses |
| `references/03-micronutrient-corrections.md` | Zn, Fe, Mn, Cu, B, S corrections + visual symptom guide |
| `references/04-ph-ec-corrections.md` | pH and EC interpretation + Saurashtra-specific fixes |
| `references/05-reading-lab-reports.md` | Decoding GSFC / KVK / Soil Health Card + PDF/image upload guide |

---

## CROSS-SKILL LINKS

| This skill recommends | Where to find preparation details |
|----------------------|----------------------------------|
| Jeevamrut | `vedic-farming` → `references/01-liquid-preparations.md` |
| Vermicompost, green manure, mulching | `vedic-farming` → `references/04-soil-amendments.md` |
| Logging soil test result + corrections | `agstack-farming` → `references/04-farm-calendar.md` |
| Tracking OC improvement over seasons | `agstack-farming` → `references/07-carbon-soil.md` |

---

## SAURASHTRA BASELINE: What to Expect Before Testing

Most Saurashtra-area soils start at these typical values:

| Parameter | Typical Starting Range | Priority |
|-----------|----------------------|----------|
| pH | 7.8–8.3 (alkaline: normal) | Manage, don't panic |
| OC | 0.3–0.6% (low: critical to build) | 🔴 High |
| N | Low to Medium | 🟡 Medium |
| P | Low (locked by alkaline pH) | 🔴 High |
| K | Medium to High (Saurashtra is K-rich) | 🟢 Usually fine |
| Zn | Deficient in >60% of Saurashtra farms | 🔴 High |
| B | Deficient in groundnut/cotton areas | 🔴 High |
| S | Often Low to Medium | 🟡 Medium |
