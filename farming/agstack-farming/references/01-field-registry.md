# Field Registry -- Asset Registry & GeoID

**Repo**: https://github.com/agstack/asset-registry  
**Live service**: https://asset-registry.agstack.org  
**User portal**: https://user-registry.agstack.org

## What It Does
Assigns a permanent, globally unique 16-character alphanumeric **GeoID** to any field polygon. Two farmers registering the same field get identical GeoIDs -- enabling cross-platform interoperability without sharing ownership data.

## Why GeoID Matters
- Single stable identifier for all data linked to a field: weather, irrigation, carbon, operations, supply chain
- Used for: insurance, carbon credits, loans, fertilizer traceability, satellite subscriptions
- Based on Google S2 geometry -- geospatially intelligent, deterministic

## Registration Steps
1. Sign up at `user-registry.agstack.org`
2. Go to `asset-registry.agstack.org`
3. Use the **Draw Polygon** or **Draw Rectangle** tool on the map
4. Click the initial point to close the polygon
5. Click **Register Field** → receive your GeoID (16 chars)

## API Reference
```bash
# Register via API (GeoJSON polygon)
POST https://api.agstack.org/register-asset
Content-Type: application/json
{
  "type": "Feature",
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [[70.25, 21.30], [70.255, 21.30], [70.255, 21.305], [70.25, 21.305], [70.25, 21.30]]
    ]
  }
}
# Response: { "geo_id": "A3B7C2D8E1F4G9H6" }

# Fetch GeoID from lat/lon (crowd-sourced lookup)
GET https://api.agstack.org/fetch-field?lat=21.302&lon=70.252
# Returns GeoID if a nearby field is already registered

# Fetch boundary polygon by GeoID
GET https://api.agstack.org/get-boundary?geo_id=A3B7C2D8E1F4G9H6
```

## TerraTrac Mobile App
**Repo**: https://github.com/agstack/TerraTrac-field-app  
Android app for capturing field boundaries in the field (no desktop needed).
- GPS-based polygon recording
- Works offline in areas with poor connectivity
- EUDR (EU Deforestation Regulation) compliance check
- Syncs to Asset Registry when connected

**Use case for Keshod**: Walk the boundary of your 3-vigha field with the app running. It records your GPS path as a polygon and registers it automatically.

## TerraTrac Validator Portal
**Repo**: https://github.com/agstack/TerraTrac-validator-portal  
Upload batch CSV/GeoJSON of plot coordinates → validate for EUDR deforestation risk.

## Auto-Boundary Detection
**Repo**: https://github.com/agstack/autogeobound  
Jupyter notebook-based ML tool that detects field boundaries automatically from satellite imagery. Useful when you have satellite images but no manually drawn polygons.

## Asset Registry 2.0 (Next Generation)
Under development. Adds:
- S2 compact cover identity
- W3C Verifiable Credentials
- EU Data Spaces compliance
- OGC/STAC integration
- Two-level masking for privacy

## Setup (Self-Hosted)
```bash
git clone https://github.com/agstack/asset-registry.git
cd asset-registry
cp .env.example .env
# Edit .env with your database credentials
docker compose up -d
```
Requirements: Python 3.x, PostgreSQL with PostGIS, Docker
