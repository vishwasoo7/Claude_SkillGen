# 05 -- Reading Lab Reports
## GSFC · KVK · Soil Health Card · PDF & Image Upload Guide

---

## TABLE OF CONTENTS
1. [Uploading Your Report -- PDF and Image Guide](#1-uploading-your-report)
2. [GSFC Lab Report Format](#2-gsfc-lab-report-format)
3. [KVK (Krishi Vigyan Kendra) Report Format](#3-kvk-report-format)
4. [Government Soil Health Card](#4-government-soil-health-card)
5. [Private Lab Reports -- Common Variations](#5-private-lab-reports)
6. [Common Confusions and Mistakes](#6-common-confusions-and-mistakes)
7. [What to Ask the Lab](#7-what-to-ask-the-lab)
8. [Where to Get Tested in Junagadh](#8-where-to-get-tested-in-junagadh)
9. [How to Collect a Soil Sample Correctly](#9-how-to-collect-a-soil-sample)

---

## 1. UPLOADING YOUR REPORT

**Supported upload types -- all work:**
- PDF (lab-generated digital report)
- JPG or PNG (scanned report or photograph)
- Phone photo of paper report (even if slightly angled or in partial shadow -- readable)
- WhatsApp-forwarded image of lab report

**What happens when you upload:**
1. I extract all parameter values from the document
2. I identify which lab format it is (GSFC / KVK / private / Soil Health Card)
3. I classify each parameter (Low / Medium / High / Deficient)
4. I apply unit conversions automatically (P₂O₅→P, K₂O→K, OM→OC if needed)
5. I generate a prioritized organic correction plan with per-Vigha quantities

**For best reading quality:**
- Photograph in natural daylight -- avoid flash glare on glossy lab paper
- Capture the full page including header (lab name helps identify format)
- If multi-page -- upload all pages together or one by one
- Handwritten values on a printed form are also readable

**If the image is unclear:**
Simply type the values you can read -- "pH 8.1, N 245, Zn 0.4" --
and I will work from those directly without needing the full document.

---

## 2. GSFC LAB REPORT FORMAT

GSFC (Gujarat State Fertilizers & Chemicals) soil labs are the most commonly used in Saurashtra.
Reports typically have a printed table format with these column headers:

| Column on GSFC Report | What It Means | Unit Reported |
|----------------------|--------------|---------------|
| pH (1:2.5) | Soil pH in water suspension | -- (dimensionless) |
| EC (1:2.5) | Electrical conductivity | dS/m |
| OC % | Organic Carbon percentage | % |
| Av. N | Available Nitrogen | kg/ha |
| Av. P₂O₅ | Available Phosphorus (as pentoxide) | kg/ha |
| Av. K₂O | Available Potassium (as oxide) | kg/ha |
| DTPA-Zn | Available Zinc (DTPA extraction) | mg/kg |
| DTPA-Fe | Available Iron | mg/kg |
| DTPA-Mn | Available Manganese | mg/kg |
| DTPA-Cu | Available Copper | mg/kg |
| Hot water B | Available Boron | mg/kg |
| CaCl₂-S | Available Sulphur | mg/kg |

**GSFC common abbreviations:**
- "Av." = Available
- "DTPA" = Extraction method for micronutrients (standard, reliable)
- "1:2.5" after pH or EC = ratio of soil to water used in measurement (standard)
- P₂O₅ = phosphorus pentoxide form → divide by 2.29 to get elemental P
- K₂O = potassium oxide form → divide by 1.2 to get elemental K

**Status column:** GSFC reports often include a "Status" column reading Low / Medium / High.
Use this as your first classification guide. But always cross-check with the tables in
`01-parameter-ranges.md` -- especially for P and Zn where pH context changes the interpretation.

---

## 3. KVK REPORT FORMAT

Krishi Vigyan Kendra labs may use slightly different terminology from GSFC:

| KVK Column Header | GSFC Equivalent | Conversion if Needed |
|------------------|----------------|---------------------|
| Hydrogen Ion Concentration | pH | Same -- no conversion |
| Soluble Salts | EC | Sometimes in mmho/cm = dS/m (same) |
| Organic Matter % | OC % | KVK often reports OM -- divide by 1.724 to get OC |
| N (Alkaline KMnO₄) | Available N | Slightly different extraction; values comparable |
| P (Olsen method) | Available P | Check if reported as elemental P or P₂O₅ |
| K (NH₄OAc method) | Available K | Check if elemental K or K₂O |
| Micronutrients | Same parameters, DTPA method | Same units mg/kg |

**Key KVK difference:** KVK often reports Organic Matter (OM%) rather than Organic Carbon (OC%).
To convert: **OC% = OM% ÷ 1.724**
Example: KVK report shows OM 1.03% → OC = 1.03 ÷ 1.724 = 0.60% (Medium-Low range)

---

## 4. GOVERNMENT SOIL HEALTH CARD

The Soil Health Card scheme (Government of India) is free and available through
your local agricultural office or Gram Sevak in Keshod.

**Format:** Color-coded card for 12 parameters.

**Color codes:**
| Color | Meaning | Action |
|-------|---------|--------|
| 🟢 Green | Sufficient / High | No input needed |
| 🟡 Yellow | Medium / Adequate | Maintenance inputs -- prevent decline |
| 🔴 Red | Low / Deficient | Immediate correction needed |

**12 parameters tested:** pH, EC, OC, N, P, K, Zn, Fe, Mn, Cu, B, S

**How to use the card:**
1. Any 🔴 Red = priority correction this season (refer to reference files 02-04)
2. Any 🟡 Yellow = apply maintenance protocol to prevent dropping to Red
3. 🟢 Green = no input needed for that parameter -- do not over-apply

**Limitation of Soil Health Card:**
It gives status categories (Red/Yellow/Green) but not exact numbers.
For precise per-Vigha prescriptions, get a GSFC or KVK numeric report.
Use the card for direction, then get a numeric report for exact dosing.

---

## 5. PRIVATE LAB REPORTS -- COMMON VARIATIONS

Private labs in Rajkot, Ahmedabad, and Junagadh may format reports differently:

| Variation You Might See | What It Means | What to Do |
|------------------------|--------------|------------|
| "Total N" instead of "Available N" | Total = locked + available. Not useful for prescription. | Ask lab to re-test for Available N specifically |
| P reported in ppm not kg/ha | ppm here = mg/kg | Multiply by 2.47 to convert to kg/ha |
| K reported as meq/100g | Milliequivalents | Multiply by 391 to get mg/kg |
| OC reported as g/kg | Grams per kilogram | Divide by 10 to get OC% |
| pH reported as 1:1 ratio | Slightly lower reading than 1:2.5 | Both valid; note which method |
| EC reported in μS/cm | Microsiemens | Divide by 1000 to get dS/m |
| Separate "Total" and "Available" columns | Use the Available column only | Ignore Total for prescription purposes |

---

## 6. COMMON CONFUSIONS AND MISTAKES

**Confusion 1 -- Total N vs Available N**
Total N = all nitrogen in soil including locked organic matter.
Available N = what plants can absorb this season from soil water.
A report showing "Total N 1200 kg/ha" sounds rich but is not actionable.
Always base prescriptions on Available N.

**Confusion 2 -- P₂O₅ vs Elemental P**
Report says "Available P₂O₅ = 22 kg/ha."
Elemental P = 22 ÷ 2.29 = 9.6 kg/ha → this is Low (below 10 kg/ha threshold).
Without converting, you would incorrectly classify this as Medium and under-correct.

**Confusion 3 -- OC vs OM**
GSFC reports OC%. KVK often reports OM%.
A KVK report showing OM 1.38% = OC 0.80% = Medium (not Good as it might appear).
Always convert OM to OC before comparing to classification tables.

**Confusion 4 -- mg/kg and ppm are identical**
0.5 mg/kg Zn = 0.5 ppm Zn. No conversion needed between these two labels.
Many reports use ppm, tables use mg/kg -- they are the same.

**Confusion 5 -- dS/m and mmho/cm are identical**
EC 0.85 dS/m = EC 0.85 mmho/cm. No conversion needed.

**Confusion 6 -- "Sufficient" on report ≠ available to plant if pH is high**
A GSFC report showing Zn "Medium" at pH 8.2 does not mean plants are getting that Zn.
pH is locking it. Always overlay pH onto your micronutrient reading.

---

## 7. WHAT TO ASK THE LAB

When submitting a sample, specify these to get the most useful report:

**Basic package (minimum -- always request):**
pH, EC, OC%, Available N (kg/ha), Available P (kg/ha), Available K (kg/ha)

**Extended package (recommended for Saurashtra):**
Add: Zn, Fe, B, S -- these four are the most commonly deficient in Junagadh district

**Full micronutrient package:**
Also add Mn, Cu -- for a complete picture

**Questions to ask explicitly:**
- "Is P reported as elemental P or as P₂O₅?"
- "Is K reported as elemental K or as K₂O?"
- "Is this Available N or Total N?"
- "Which extraction method did you use for P -- Olsen or Bray?"
  (Olsen is correct for alkaline/calcareous soils like Saurashtra -- Bray underestimates)
- "Can you add EC to the report if it is not included?"

---

## 8. WHERE TO GET TESTED IN JUNAGADH

| Lab | Location | Approx. Cost | Package Included |
|-----|----------|-------------|-----------------|
| GSFC Soil Testing Lab | Junagadh district agricultural office | ₹150-300 | Full macro + micro |
| KVK Junagadh | Junagadh | Free or subsidized | Full 12-parameter |
| Soil Health Card (GoI scheme) | Via local Gram Sevak or Krishi Kendra | Free | 12 parameters, color-coded |
| Private labs (Rajkot) | Send sample by courier | ₹500-1500 | Full + micronutrients + custom |

**Recommendation for your farm:**
- First season: Get the free Soil Health Card for baseline direction
- Then: GSFC or KVK full numeric report -- gives actual numbers to track over seasons
- Each season thereafter: Same lab, same time (pre-sowing) -- to track improvement trajectory

---

## 9. HOW TO COLLECT A SOIL SAMPLE CORRECTLY

A prescription is only as accurate as the sample. Poor sampling = misleading report.

**When to sample:**
- After previous crop harvest -- before new season inputs are applied
- Pre-sowing (May for Kharif, October for Rabi)
- Same calendar date each year for year-on-year comparison

**How to collect:**
1. Walk across the field in a W or Z pattern
2. Collect small portions from 10-15 spots across the Vigha
3. Depth: 0-15 cm (surface root zone) for standard test
4. Remove surface debris, stones, and visible roots
5. Mix all collected soil in a clean plastic bucket
6. Take approximately 500g from the mixed pile
7. Dry in shade for 1-2 hours before placing in the sample bag

**What to avoid:**
- Do not sample from spots where fresh manure was applied within 30 days
- Do not sample from field borders or near trees / bunds
- Do not use a rusty or iron-contaminated tool (affects Fe and micronutrient readings)
- Do not collect wet / waterlogged soil immediately after irrigation

**Label the bag clearly:**
Farm name, village (Rangpur), taluka (Keshod), district (Junagadh), date of collection,
depth (0-15 cm), crop to be grown, and any special notes (e.g., "saline patch area").
