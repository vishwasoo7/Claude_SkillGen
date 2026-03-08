# Pest & Disease Management

**Repo**: https://github.com/agstack/OpenAgri-PestAndDiseaseManagement  
**License**: EUPL 1.2

## What It Does
A rule-based probabilistic Decision Support System (DSS). Takes weather conditions, crop type, and growth stage → outputs pest/disease risk scores and recommended actions.

**Key design**: The system is rule-configurable. You define risk rules (temperature thresholds, humidity windows, crop stage) and the service evaluates them against incoming sensor/weather data.

## How Risk Assessment Works
```
Inputs:
  - Crop type + growth stage
  - Temperature (avg, max, min) over past 7 days
  - Humidity (avg) over past 7 days
  - Rainfall last 7 days
  - Optional: scouting observations from Farm Calendar

Rule Engine evaluates:
  - Does temp/humidity match pest development window?
  - Is crop in a vulnerable growth stage?
  - Were pests recently observed (from Farm Calendar)?

Output:
  - Risk score 0.0-1.0 per pest/disease
  - Risk level: Low / Medium / High / Critical
  - Recommended action
  - Notification trigger (if configured)
```

## API Usage
```bash
# Setup
git clone https://github.com/agstack/OpenAgri-PestAndDiseaseManagement.git
cd OpenAgri-PestAndDiseaseManagement
docker compose up -d

# Run risk assessment
POST http://localhost:8004/api/v1/pest/assess
{
  "geo_id": "A3B7C2D8E1F4G9H6",
  "crop": "groundnut",
  "growth_stage": "pegging",
  "weather_last_7d": {
    "temp_avg": 29.5,
    "temp_max": 36.0,
    "humidity_avg": 78,
    "rainfall_mm": 45
  },
  "observations": [
    { "pest": "leaf_miner", "severity": "low", "date": "2025-08-01" }
  ]
}

# Define a custom risk rule
POST http://localhost:8004/api/v1/pest/rules
{
  "pest": "tikka_leaf_spot",
  "crop": "groundnut",
  "trigger_conditions": {
    "temp_min": 22, "temp_max": 32,
    "humidity_min": 80,
    "consecutive_wet_days": 3
  },
  "risk_weight": 0.8,
  "action": "Apply neem-based fungicide; improve canopy airflow"
}
```

## Common Pests & Diseases for Junagadh/Keshod Region

### Kharif Season (June-October)
| Pest/Disease | Crop | Risk Trigger | Organic Control |
|--------------|------|--------------|-----------------|
| Leaf miner | Groundnut | Temp 25-35°C, low humidity | Neem oil 2%, yellow sticky traps |
| Aphid | Groundnut, Cotton | Temp 20-30°C, dry spells | Neem extract, release ladybird |
| Whitefly | Cotton | Temp >30°C, dry | Neem oil, reflective mulch |
| Tikka leaf spot | Groundnut | Temp 25-30°C, RH >80%, rain | Reduce plant density, neem fungicide |
| Stem borer | Bajra | Early rains, high humidity | Pheromone traps, Trichoderma |
| Bollworm | Cotton | Temp 25-35°C | Bt spray, pheromone traps |
| Red hairy caterpillar | Groundnut | Pre-monsoon dry spell + first rain | Inter-crop, tilling soil pre-season |

### Rabi Season (November-March)
| Pest/Disease | Crop | Risk Trigger | Organic Control |
|--------------|------|--------------|-----------------|
| Powdery mildew | Cumin | Temp 15-25°C, RH 60-80% | Cow urine spray, sulfur dust |
| Aphid | Cumin, Wheat | Cool dry weather | Neem extract 3%, garlic spray |
| Rust | Wheat | Temp 15-20°C, dew | Remove volunteer plants, resistance varieties |
| Blight | Chickpea | Cool wet weather | Trichoderma, bordeaux mixture |

## Natural/Organic Control Recipes (Log in Farm Calendar)
```
Neem Oil Spray:
  - 3% neem oil + 1% soap emulsifier + water
  - Apply at 7-10 day intervals during risk period
  - Best applied early morning or evening

Cow Urine Spray (antifungal):
  - Fermented cow urine (10-15 days): dilute 1:10 with water
  - Spray on foliage weekly during humid periods
  - Effective against powdery mildew and some rust strains

Panchagavya (immune booster):
  - 5L cow dung + 5L cow urine + 1L milk + 1L curd + 1L ghee
  - Ferment 21 days, stir daily
  - Dilute 3% in water, spray at 15-day intervals

Garlic-Ginger Pepper Extract:
  - 100g garlic + 100g ginger + 50g pepper → grind, soak in 1L water 24h
  - Strain, dilute 1:10, spray for sucking pests
```

## Setting Up Notification Alerts
```bash
# Configure alert threshold
POST http://localhost:8004/api/v1/pest/alerts/configure
{
  "geo_id": "A3B7C2D8E1F4G9H6",
  "alert_when": "risk_score > 0.6",
  "notify_via": "webhook",
  "webhook_url": "https://your-app.com/farm-alert"
}
```
When risk crosses threshold, the service POSTs an alert to your webhook with pest name, risk score, and recommended action.
