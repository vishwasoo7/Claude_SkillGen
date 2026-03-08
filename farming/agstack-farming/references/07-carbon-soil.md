# Carbon Model & Soil Health

**Repo**: https://github.com/agstack/field-carbon-model  
**License**: Apache 2.0  
**Technology**: Python, Jupyter Notebooks, NASA SMAP L4C satellite data

## What It Does
Field-specific carbon model that leverages **NASA's SMAP L4C** (Soil Moisture Active Passive -- Level 4 Carbon) satellite product to estimate:
- Net Ecosystem Exchange (NEE) of carbon
- Gross Primary Production (GPP) -- photosynthesis
- Ecosystem Respiration (Reco)
- Soil carbon stock estimates per field

## Why This Matters for Natural Farming
Natural/organic farming practices build soil carbon over time. This model lets you:
1. **Measure baseline**: What is your field's carbon level at the start?
2. **Track improvement**: Does adding Jeevamrut, composting, mulching increase carbon?
3. **Prove carbon sequestration**: Potential for carbon credit programs

## SMAP L4C -- What It Measures
| Variable | Description | Resolution |
|----------|-------------|-----------|
| GPP | Gross Primary Production (g C/m²/day) | ~9 km spatial, daily |
| NEE | Net Ecosystem Exchange | 9 km spatial, 3-hourly |
| Reco | Ecosystem Respiration | 9 km spatial |
| Soil moisture | Volumetric water content (m³/m³) | 9 km, 3-hourly |

Note: 9 km resolution means a 1.2-acre field gets the same reading as its surrounding area. Useful for regional trends and inter-season comparisons.

## Setup & Usage
```bash
git clone https://github.com/agstack/field-carbon-model.git
cd field-carbon-model
pip install -r requirements.txt
# Requires: NASA Earthdata account for SMAP data access

# Open Jupyter notebook
jupyter notebook notebooks/field_carbon_analysis.ipynb
```

**NASA Earthdata access:**
1. Register free at https://urs.earthdata.nasa.gov/
2. Request access to SMAP L4C product (SPL4CMDL)
3. Configure credentials in `.env`

## Running Analysis for Keshod Field
```python
# Example notebook cell
from field_carbon_model import FieldCarbonAnalyzer

analyzer = FieldCarbonAnalyzer(
    geo_id="A3B7C2D8E1F4G9H6",
    lat=21.302, lon=70.252,
    start_date="2024-06-01",
    end_date="2025-05-31"
)

# Fetch SMAP data for the field location
analyzer.fetch_smap_data()

# Calculate annual carbon metrics
results = analyzer.calculate_carbon_metrics()
print(results)
# Output: {
#   "gpp_gC_m2_year": 845,
#   "nee_gC_m2_year": -120,   # negative = carbon sink (good!)
#   "reco_gC_m2_year": 725,
#   "carbon_balance": "sink",
#   "soil_moisture_avg": 0.28
# }
```

## Interpreting Carbon Metrics for Your Farm

### Soil Organic Carbon (SOC) & Natural Farming
Natural farming practices that increase SOC over time:
| Practice | SOC Building Rate | Timeframe |
|----------|-----------------|-----------|
| Compost application (5t/ha) | +0.1-0.3% per year | 3-5 years |
| Mulching | +0.05-0.15% per year | 2-4 years |
| Cover crops (legumes) | +0.1-0.2% per year | 2-3 years |
| No tillage / minimal tillage | +0.1-0.2% per year | 3-5 years |
| Jeevamrut (microbial) | Accelerates all above | 1-2 years |

### What Good Carbon Trends Look Like
- NEE negative = field is a net carbon sink ✓
- GPP increasing year-on-year = improving soil fertility ✓
- Reco/GPP ratio decreasing = more carbon stored vs. released ✓

## Connecting to Farm Calendar
Log all practices that affect carbon:
```json
{
  "@type": "CropActivity.SoilAmendment",
  "date": "2025-04-15",
  "material": "FYM_compost",
  "quantity_t_ha": 5,
  "carbon_equivalent_kg_ha": 2500,
  "notes": "Fully decomposed FYM + 10% vermicompost mix"
}
```

Over seasons, you can correlate logged inputs with SMAP carbon measurements to prove your natural farming practices are building soil health -- valuable for demonstration farm documentation.

## Carbon Credit Potential (Future)
With documented practices + carbon model measurements:
- Baseline: Register field + measure current carbon
- Improvement: Document practices in Farm Calendar
- Verification: Annual carbon model measurements show increase
- Credits: Each tonne of CO₂ sequestered = potential carbon credit (~₹3,000-5,000/tonne)
- For 1.2 acres with 0.2% annual SOC gain: ~0.3-0.5 tonne CO₂/year potential
