# Irrigation Management -- ETo & Soil Moisture

**Repo**: https://github.com/agstack/OpenAgri-IrrigationManagement  
**License**: EUPL 1.2  
**Framework**: FastAPI + SQLAlchemy + Alembic

## What It Does
1. **ETo Calculator** -- Reference evapotranspiration using the Penman-Monteith equation (FAO-56 standard)
2. **Soil Moisture Analysis** -- Estimates current soil water content and irrigation deficit

## Penman-Monteith ETo (FAO-56)
The global standard for irrigation scheduling. Measures how much water crops "demand" from the atmosphere.

**Formula inputs:**
| Parameter | Symbol | Typical Range (Gujarat) |
|-----------|--------|------------------------|
| Max daily temperature | Tmax | 25-45°C |
| Min daily temperature | Tmin | 10-30°C |
| Relative humidity | RH | 20-90% |
| Wind speed at 2m | u2 | 1-5 m/s |
| Sunshine hours | n | 4-11 hrs/day |
| Altitude | z | 50-200 m (Keshod ~50m) |
| Latitude | φ | 21.3°N for Keshod |

**Typical ETo values for Keshod region:**
- June-August (Monsoon): 4-6 mm/day
- September-November: 4-5 mm/day
- December-February: 2-4 mm/day
- March-May (Summer): 6-10 mm/day

## Crop Water Requirement
```
ETc = Kc × ETo
```
**Kc (Crop Coefficient) for common Kharif crops:**
| Crop | Initial Kc | Mid-Season Kc | Late Kc |
|------|-----------|--------------|---------|
| Groundnut | 0.45 | 1.05 | 0.60 |
| Cotton | 0.35 | 1.15 | 0.70 |
| Bajra (Pearl Millet) | 0.30 | 1.00 | 0.55 |
| Sesame | 0.35 | 1.00 | 0.50 |

**Kc for Rabi crops:**
| Crop | Initial Kc | Mid-Season Kc | Late Kc |
|------|-----------|--------------|---------|
| Cumin | 0.40 | 0.85 | 0.50 |
| Wheat | 0.35 | 1.10 | 0.40 |
| Chickpea | 0.40 | 1.00 | 0.50 |
| Isabgol | 0.35 | 0.85 | 0.45 |

## API Usage
```bash
# Setup
git clone https://github.com/agstack/OpenAgri-IrrigationManagement.git
cd OpenAgri-IrrigationManagement
docker compose up -d
# Runs on port 8003 by default

# Calculate ETo
POST http://localhost:8003/api/v1/irrigation/eto
{
  "date": "2025-03-06",
  "tmax": 36.0,
  "tmin": 22.5,
  "humidity": 55,
  "wind_speed_ms": 2.8,
  "sunshine_hours": 9.5,
  "altitude_m": 50,
  "latitude_deg": 21.302
}
# Response: { "eto_mm_day": 7.2, "date": "2025-03-06" }

# Soil moisture analysis
POST http://localhost:8003/api/v1/irrigation/soil-moisture
{
  "geo_id": "A3B7C2D8E1F4G9H6",
  "soil_type": "loamy_clay",
  "field_capacity_pct": 35,
  "wilting_point_pct": 15,
  "current_moisture_pct": 24,
  "recent_rainfall_mm": 8,
  "eto_mm_day": 7.2,
  "crop": "groundnut",
  "growth_stage": "pod_filling"
}
# Response: irrigation_required: true/false, deficit_mm, days_until_stress
```

## Soil Types in Saurashtra/Junagadh Region
| Soil Type | Field Capacity | Wilting Point | Water Holding |
|-----------|---------------|---------------|---------------|
| Black cotton soil (vertic) | 42-48% | 22-26% | 180-220 mm/m |
| Red loamy soil | 28-35% | 14-18% | 120-160 mm/m |
| Sandy loam | 22-28% | 10-14% | 80-120 mm/m |

## Irrigation Scheduling for Natural Farming
**Drip irrigation (most water-efficient):**
```
Irrigation interval (days) = (FC - 50% depletion) ÷ ETc per day
Example: (35% - 17.5%) ÷ 7.2 mm/day = ~2.4 days
```

**For 1.2-acre organic farm, summer groundnut:**
- ETo ≈ 7.5 mm/day
- Kc (mid) = 1.05 → ETc ≈ 7.9 mm/day
- Irrigation frequency: every 2-3 days
- Per irrigation: 15-20 mm ≈ 600-800 L per vigha

## Natural Farming Water Conservation Strategies
| Method | Estimated ETo Reduction | How to Log |
|--------|------------------------|------------|
| Mulching (straw/dry leaves) | 20-30% reduction | FarmCalendar: "MulchApplication" |
| Cover crops | 15-25% reduction | FarmCalendar: "CoverCropPlanting" |
| Contour bunding | Reduces runoff 40% | FarmCalendar: "SoilConservation" |
| Shade trees (agroforestry) | 10-20% ETo reduction | FarmCalendar: "TreePlanting" |
