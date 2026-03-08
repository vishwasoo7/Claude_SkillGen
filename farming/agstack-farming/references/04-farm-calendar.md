# Farm Calendar -- Operations, Observations & Assets

**Repo**: https://github.com/agstack/OpenAgri-FarmCalendar  
**License**: EUPL 1.2  
**UI**: http://localhost:8002/ after Docker setup

## What It Does
The central logbook for your farm. Records:
- **Operations**: planting, irrigation, fertilization, spraying, harvesting, tillage
- **Observations**: crop health, pest sightings, soil notes, weather observations
- **Parcel properties**: area, soil type, crop, crop stage
- **Farm assets**: tractors, tools, storage, animals

All data in **JSON-LD** format, conforming to OpenAgri Common Semantic Model.

## Docker Setup
```bash
git clone https://github.com/agstack/OpenAgri-FarmCalendar.git
cd OpenAgri-FarmCalendar
cp .env.sample .env
# Edit .env:
# GATEKEEPER_LOGIN_URL=http://localhost:8000/auth/  (or leave blank for local auth)
# JWT_SIGNING_KEY=your-secret-key
docker compose up -d
# Access: http://localhost:8002
```

## Core Data Models (OCSM Types)

### Farm & Parcel
```json
{
  "@type": "Farm",
  "name": "Rangpur Natural Farm",
  "location": { "lat": 21.302, "lon": 70.252 },
  "area_ha": 0.49,
  "parcels": [
    {
      "@type": "Parcel",
      "geo_id": "A3B7C2D8E1F4G9H6",
      "area_ha": 0.16,
      "soil_type": "loamy_clay",
      "current_crop": "groundnut"
    }
  ]
}
```

### Operation Types
| Type | OCSM Class | Example |
|------|-----------|---------|
| Planting | `CropActivity.Planting` | Sowing groundnut seed |
| Irrigation | `CropActivity.Irrigation` | 20mm drip irrigation |
| Organic fertilization | `CropActivity.OrganicFertilization` | Jeevamrut spray 10L/ha |
| Crop protection | `CropActivity.CropProtection` | Neem oil 2L/ha |
| Harvesting | `CropActivity.Harvesting` | Groundnut pods 1.2 t/ha |
| Tillage | `CropActivity.SoilPreparation` | Deep ploughing pre-season |
| Observation | `CropObservation` | "Yellow leaves, 3 plants in block B" |

## REST API Quick Reference
```bash
# List all activities
GET /api/v1/farmcalendar/activities

# Create a planting activity
POST /api/v1/farmcalendar/activities
Authorization: Bearer {jwt_token}
{
  "@context": "https://openagri.eu/ocsm/",
  "@type": "CropActivity.Planting",
  "parcel_geo_id": "A3B7C2D8E1F4G9H6",
  "date": "2025-06-15",
  "crop": "groundnut",
  "variety": "GG-20",
  "seed_rate_kg_ha": 100,
  "row_spacing_cm": 30,
  "notes": "Pre-soaked in Beejamrut for 12 hours"
}

# Create an observation
POST /api/v1/farmcalendar/observations
{
  "@type": "CropObservation",
  "parcel_geo_id": "A3B7C2D8E1F4G9H6",
  "date": "2025-07-10",
  "observation_type": "pest_sighting",
  "pest": "aphid",
  "severity": "low",
  "location_in_field": "north-east corner",
  "notes": "5-10 aphids per leaf, ~15% of plants affected"
}

# Log Jeevamrut application
POST /api/v1/farmcalendar/activities
{
  "@type": "CropActivity.OrganicFertilization",
  "parcel_geo_id": "A3B7C2D8E1F4G9H6",
  "date": "2025-07-01",
  "product": "Jeevamrut",
  "preparation": "10L cow dung + 10L cow urine + 1kg jaggery + 1kg gram flour + handful soil, fermented 7 days",
  "application_method": "soil_drench",
  "rate_L_ha": 500,
  "notes": "Applied before irrigation"
}
```

## Natural Farming Log Templates

### Beejamrut Seed Treatment
```json
{
  "@type": "CropActivity.SeedTreatment",
  "method": "Beejamrut",
  "preparation": "1L cow urine + 50g cow dung + 50g lime + water to 1L",
  "soak_hours": 12,
  "crop": "groundnut",
  "quantity_treated_kg": 15
}
```

### Monthly Jeevamrut Schedule
```json
{
  "schedule": "Every 15 days",
  "rate": "200L per acre",
  "timing": "Early morning, before irrigation",
  "preparation_days": 7
}
```

## Reporting Integration
After recording operations, generate a season-end PDF:
```bash
POST /api/v1/reports/season-summary
{
  "farm_geo_id": "A3B7C2D8E1F4G9H6",
  "season": "kharif-2025",
  "include": ["activities", "observations", "yield", "input_costs"]
}
```
This calls the **OpenAgri-ReportingService** to produce a printable PDF -- ideal for demonstration farm documentation.
