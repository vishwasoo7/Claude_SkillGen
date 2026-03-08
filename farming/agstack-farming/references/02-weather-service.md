# Weather Service -- Agricultural Forecasts

**Repo**: https://github.com/agstack/OpenAgri-WeatherService  
**License**: EUPL 1.2

## What It Does
Delivers 5-day weather forecasts focused on agriculture-relevant indicators. Data is in **JSON-LD** format following the OpenAgri Common Semantic Model (OCSM) for interoperability with all other OpenAgri services.

## Agricultural Indicators Provided
| Indicator | Unit | Agricultural Use |
|-----------|------|-----------------|
| Temperature (max/min/avg) | °C | Crop stress, pest development threshold |
| Relative Humidity | % | Disease risk (fungi, bacteria thrive >80%) |
| Wind Speed & Direction | m/s | Spray timing, evaporation rate |
| Rainfall Probability | % | Irrigation planning |
| Rainfall Amount | mm | Water budget calculation |
| Solar Radiation | MJ/m² | Photosynthesis potential, ETo calculation |
| THI (Temperature-Humidity Index) | -- | Livestock heat stress assessment |
| ETo Estimate | mm/day | Irrigation scheduling reference |

## THI (Temperature-Humidity Index)
Calculated automatically by the service. Formula:
```
THI = (1.8 × T + 32) - ((0.55 - 0.0055 × RH) × (1.8 × T - 26.8))
```
- THI < 72: No stress (livestock comfortable)
- THI 72-79: Mild heat stress
- THI 79-89: Moderate stress (reduce stocking, shade required)
- THI > 89: Severe stress (reduce activity, increase water)

## API Usage
```bash
# Docker setup
git clone https://github.com/agstack/OpenAgri-WeatherService.git
cd OpenAgri-WeatherService
cp .env.sample .env
docker compose up -d

# Fetch 5-day forecast
GET http://localhost:8001/api/v1/weather/forecast
    ?lat=21.302
    &lon=70.252
    &days=5
    &format=json-ld

# Response structure (JSON-LD)
{
  "@context": "https://openagri.eu/ocsm/weather",
  "type": "WeatherForecast",
  "location": { "lat": 21.302, "lon": 70.252 },
  "forecasts": [
    {
      "date": "2025-03-06",
      "tmax": 34.5, "tmin": 21.0, "tavg": 27.8,
      "humidity": 58,
      "wind_speed": 3.2,
      "rainfall_prob": 5,
      "rainfall_mm": 0,
      "solar_radiation": 22.4,
      "eto_estimate": 6.8,
      "thi": 74.2
    }
  ]
}
```

## Gujarat / Keshod Seasonal Reference
| Season | Temp Range | Humidity | Key Risk |
|--------|-----------|----------|----------|
| Kharif (Jun-Oct) | 28-40°C | 70-90% | High fungal disease risk when RH>80% |
| Rabi (Nov-Mar) | 12-30°C | 40-65% | Frost risk Dec-Jan nights; cumin sensitive |
| Summer (Apr-Jun) | 35-45°C | 20-45% | ETo 7-10 mm/day; irrigation critical |

## Integration with Other Services
- Weather data feeds directly into **Irrigation Management** for ETo calculation
- Weather conditions (temperature + humidity over time) feed **Pest & Disease** risk engine
- All weather observations logged in **Farm Calendar** as JSON-LD

## Interpreting Forecasts for Natural Farming
- **Spray timing**: Apply foliar sprays (Jeevamrut, neem) when wind < 3 m/s, temperature < 30°C, no rain forecast for 4+ hours
- **Irrigation timing**: Irrigate early morning when ETo is lowest and temperature < 25°C
- **Composting**: Turn compost when humidity > 60% -- microbial activity peaks
- **Planting windows**: Look for 3+ consecutive days with overnight temp > 15°C (germination threshold for most field crops)
