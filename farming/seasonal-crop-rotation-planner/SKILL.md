---
name: seasonal-crop-rotation-planner
description: >
  Seasonal crop rotation and succession planner for the Rangpur Natural Farm,
  Keshod, Junagadh, Gujarat. Trigger for: what to plant, crop rotation, what crop
  next season, Kharif planning, Rabi planning, which crops for my farm, intercropping,
  rotation plan, succession planting, soil restoration crop, nitrogen fixing crop,
  cover crop before cumin, 5 year plan, what after Kali Jeeri, chemical detox
  rotation, which parcel for which crop, crop sequence Keshod, crop combination,
  what to grow, planting calendar, which crop is good for soil, companion planting,
  crop diversity, Bajra after Sesame, Cumin after Cowpea, Rabi after Kharif,
  fallow planning, green manure before main crop, year 1 crop, year 2 crop.
  Calibrated for a 3-Vigha chemical-transition farm in Saurashtra, Gujarat,
  starting Kharif 2026 with heavy prior synthetic input history.
---

# Seasonal Crop Rotation Planner
## Keshod Farm -- 5-Year Soil Recovery and Income Plan

Crop rotation on a chemical-transition farm is not just about income scheduling.
Every planting decision either speeds up soil recovery or slows it down.
This skill integrates both into a single plan.

---

## HOW TO USE THIS PLANNER

**Three entry points:**

**1. "What should I plant next season?"**
Go directly to `references/01-five-year-rotation-plan.md`.
Find your current year and season. The table shows what to plant, on which parcel,
and why -- with the soil recovery logic behind each choice.

**2. "Tell me about a specific crop"**
Go to `references/02-crop-profiles-intercropping.md`.
Each crop has a profile: sowing window, harvest window, soil impact, input needs,
typical yield per Vigha, and Keshod-specific notes.

**3. "Should I intercrop X with Y?"**
Go to `references/02-crop-profiles-intercropping.md` -- Intercropping section.
Proven combinations for Saurashtra climate with what each combination achieves.

---

## THE CORE ROTATION PRINCIPLES

These govern every planting decision in the 5-year plan:

**Principle 1: No bare soil, ever**
Every square foot of the farm should have something growing at all times.
Bare soil loses moisture, loses OC, invites weed pressure, and bakes under Gujarat sun.
If a main crop fails or there is a gap between seasons: sow a cover crop immediately.

**Principle 2: Legume every season, on at least one parcel**
Cowpea, Guar, Methi, Chickpea, or Dhaincha -- at least one legume every season.
Legumes fix atmospheric nitrogen, reducing input cost and building soil N reserves.
On a recovering chemical farm, biological N fixation is the primary path to
rebuilding available nitrogen without synthetic inputs.

**Principle 3: Deep root before shallow root**
Alternate deep-rooted crops (Bajra, Dhaincha, Sesame) with shallow-rooted crops
(Cumin, Methi, Coriander) on the same parcel across seasons.
Deep roots break compaction. Shallow roots then access the loosened layer.
This replaces mechanical tillage with biological tillage.

**Principle 4: High-demand after soil-building**
Do not plant Cumin (your highest-value, highest-demand crop) in Year 1 on all parcels.
Cumin performs best on soil with OC above 0.5% and EC below 0.75 dS/m.
Let soil recover for 1-2 seasons before dedicating significant area to Cumin.
Year 3 onward: Cumin area can expand as soil measurements confirm recovery.

**Principle 5: Income from every season, even Year 1**
Soil restoration does not require sacrificing all income.
Year 1 crops (Bajra, Sesame, Cowpea, Guar) are lower-input, drought-tolerant,
and marketable at APMC Keshod. They also happen to be soil-improving crops.
The rotation plan generates income every season while building toward Cumin dominance
in Years 3-5 when soil can support it.

---

## DECISION SCENARIOS

### Scenario A: Planning ahead of time (most common)
Read the 5-year plan in ref01. Identify your year and season.
Cross-check crop profiles in ref02 for input requirements and sowing windows.
Log your planting plan in Farm Calendar (agstack-farming skill).

### Scenario B: Kharif failed or underperformed -- what now for Rabi?
Key question: what did the Kharif crop do to the soil?

| Kharif outcome | Rabi recommendation |
|---|---|
| Cowpea / Guar grew well, good biomass | Cumin -- legume improved N, Cumin will benefit |
| Bajra grew well, heavy residue | Methi or Coriander -- Bajra residue mulches well for these |
| Sesame grew poorly, soil still compacted | Dhaincha cover crop first (30 days), then Rabi sow |
| Crop failed completely, bare soil | Do not leave bare -- sow Methi immediately (short cycle, forgiving) |
| Heavy weed pressure | Mustard (allelopathic -- suppresses weeds), incorporate before Rabi main crop |

### Scenario C: Soil test shows specific deficiency -- what crop helps?

| Soil test result | Rotation response |
|---|---|
| OC below 0.4% | Prioritise Dhaincha green manure + Cowpea this season over income crops |
| N very low, biology inactive | Cowpea or Guar on all parcels this Kharif -- N fixation is the priority |
| EC above 1.5 dS/m | Bajra (salt-tolerant) + gypsum -- do not plant Cumin until EC drops |
| Zn deficient, pH above 8.2 | Mustard cover crop (acidifies slightly) + correct pH before planting sensitive crops |
| Soil compacted (water pools) | Dhaincha before every main crop this year -- deepest roots of any cover crop |

Cross-reference soil test numbers with `soil-test-interpreter` for amendment prescriptions.

---

## WHAT CHANGES YEAR BY YEAR

Year 1 (2026-27): soil biology largely dead, herbicide residue possible, low OC
  Focus: bioremediation crops, legumes, green manure, modest income from hardy crops

Year 2 (2027-28): microbial community stabilising, first OC improvement visible
  Focus: expand legume area, first test of Cumin on best-performing parcel

Year 3 (2028-29): soil structure improving, earthworm population building
  Focus: shift toward higher-value crops, reduce cover crop proportion as soil holds itself

Year 4 (2029-30): approaching healthy natural farm baseline
  Focus: diversify into vegetables or specialty crops, full Cumin rotation possible

Year 5 (2030-31): demonstration farm maturity
  Focus: optimise income, soil is an asset not a liability, mentor other farmers

Detailed season-by-season tables for all 5 years: `references/01-five-year-rotation-plan.md`

---

## CROSS-SKILL LINKS

| Need | Skill |
|---|---|
| Crop prices at APMC Keshod / Junagadh | `agstack-farming` -> `references/10-apmc-pgs.md` |
| How long each crop survives without irrigation | `water-irrigation-emergency` -> `references/01-crop-water-tolerance.md` |
| Cover crop seed rates and incorporation protocol | `soil-test-interpreter` -> `references/06-chemical-detox-retesting.md` |
| ZBNF inputs per crop (Jeevamrut dose, Beejamrut) | `vedic-farming` |
| Soil test interpretation and amendment prescription | `soil-test-interpreter` |
| Log planting decisions and field observations | `farm-journal` |
| Log planting events in Farm Calendar | `agstack-farming` -> `references/04-farm-calendar.md` |
| Lunar calendar timing for sowing | `vedic-farming` -> `references/03-lunar-calendar.md` |

---

## REFERENCE FILES

| File | When to Read |
|---|---|
| `references/01-five-year-rotation-plan.md` | Season-by-season rotation tables for Years 1-5, parcel allocation logic, income vs soil-recovery balance |
| `references/02-crop-profiles-intercropping.md` | Per-crop profiles for 10 Keshod crops, proven intercropping combinations, succession windows |
