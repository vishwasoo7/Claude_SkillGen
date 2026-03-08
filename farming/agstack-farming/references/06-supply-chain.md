# Supply Chain Traceability -- INATrace & EUDR

## INATrace -- Blockchain Farm-to-Consumer Traceability
**Repo (meta)**: https://github.com/agstack/inatrace  
**Backend**: https://github.com/agstack/inatrace-backend (Java/Spring Boot)  
**Frontend**: https://github.com/agstack/inatrace-frontend (TypeScript)  
**Mobile**: https://github.com/agstack/inatrace-mobile (TypeScript)  
**Coffee Network**: https://github.com/agstack/inatrace-coffee-network  
**License**: Mozilla Public License 2.0

### What It Does
Open-source blockchain-based track and trace system covering the full journey from farmer to consumer. Originally built for coffee, now generalized for any agricultural commodity.

**Key capabilities:**
- Register farmers and their fields (linked to GeoID)
- Record each harvest batch with: date, quantity, quality parameters, inputs used
- Track processing steps: drying, milling, sorting, packaging
- Generate QR codes that buyers can scan to verify origin
- Cryptographically sign each step on a blockchain -- tamper-proof

### Architecture
```
Farmer (mobile app) → records harvest + inputs
    ↓
INATrace Backend (blockchain ledger)
    ↓
Processor / Aggregator → records processing steps
    ↓
Trader / Exporter → records shipment
    ↓
Consumer (QR scan) → sees full journey
```

### Setup
```bash
git clone https://github.com/agstack/inatrace-backend.git
cd inatrace-backend
# Requires Java 17+, PostgreSQL, Docker
docker compose up -d

# Frontend
git clone https://github.com/agstack/inatrace-frontend.git
cd inatrace-frontend
npm install && npm run dev
```

### API -- Register a Harvest Batch
```json
POST /api/v1/stockOrders
{
  "orderType": "PURCHASE_ORDER",
  "productionDate": "2025-10-25",
  "crop": "groundnut",
  "quantity": 120,
  "unit": "kg",
  "farmerGeoId": "A3B7C2D8E1F4G9H6",
  "inputs_used": [
    { "type": "organic_fertilizer", "product": "Jeevamrut", "quantity_L_ha": 500 },
    { "type": "crop_protection", "product": "Neem oil", "quantity_L_ha": 3 }
  ],
  "certifications": ["chemical_free", "no_synthetic_pesticides"]
}
# Returns: batch_id, QR code URL
```

### For Natural Farming Produce
Highly valuable use case: document that your produce is chemical-free.
1. Log all inputs in **Farm Calendar** (organic only)
2. At harvest, create INATrace batch -- it automatically pulls Farm Calendar input history
3. QR code on packaging shows buyers: what was applied, when, in what quantity
4. Creates premium market access: organic restaurants, export, premium retail

---

## TraceFood Chain
**Repo**: https://github.com/agstack/tracefoodchain  
Flutter-based mobile/web app for tracing various goods along food production chains. Lighter-weight alternative to INATrace for smaller operations or single-commodity producers.

---

## TerraTrac -- EUDR Compliance
**Field App**: https://github.com/agstack/TerraTrac-field-app (Kotlin/Android)  
**Validator Portal**: https://github.com/agstack/TerraTrac-validator-portal (SCSS/TypeScript)

### EU Deforestation Regulation (EUDR)
EUDR requires that certain commodities (soy, beef, cocoa, coffee, palm oil, wood, rubber) exported to the EU must prove they were not produced on deforested land after 31 Dec 2020.

**TerraTrac workflow:**
1. Farmer uses mobile app to record plot geolocation
2. App captures GPS polygon or point location
3. Data syncs to Validator Portal
4. Portal checks coordinates against deforestation databases
5. Generates compliance certificate for export

### Setup
```bash
# Validator Portal
git clone https://github.com/agstack/TerraTrac-validator-portal.git
cd TerraTrac-validator-portal
npm install && npm start

# Android field app
git clone https://github.com/agstack/TerraTrac-field-app.git
# Open in Android Studio, build and deploy
```

---

## Connecting Traceability to Your Farm Project
For a demonstration natural farm, the traceability stack creates proof of your organic methods:

```
Register field (GeoID) 
    → Log all inputs in Farm Calendar (zero chemicals documented)
    → Harvest recorded in INATrace
    → QR code generated
    → Visitors / buyers scan QR → see every input used on the farm
    → Builds trust + premium pricing
```

This is particularly powerful in Gujarat where organic groundnut oil and cumin command 30-50% premium in export markets.
