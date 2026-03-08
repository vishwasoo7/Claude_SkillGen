# Deployment -- Full OpenAgri Stack

## OpenAgri-Bootstrap-Deployment (Recommended Start)
**Repo**: https://github.com/agstack/OpenAgri-Bootstrap-Deployment  
**License**: EUPL 1.2

One-command Docker Compose setup for all OpenAgri services. The easiest way to get the full stack running.

### Prerequisites
- Docker + Docker Compose installed
- Minimum: 4GB RAM, 20GB disk
- Ports available: 8000-8009

### One-Command Setup
```bash
git clone https://github.com/agstack/OpenAgri-Bootstrap-Deployment.git
cd OpenAgri-Bootstrap-Deployment
cp .env.sample .env
# Edit .env with your configuration (database passwords, JWT secret, etc.)
docker compose up -d
```

### Services Started
| Service | Port | Description |
|---------|------|-------------|
| GateKeeper (Auth) | 8000 | JWT login/auth for all services |
| Farm Calendar | 8002 | Operations & observations logging |
| Weather Service | 8001 | Agricultural weather forecasts |
| Irrigation Management | 8003 | ETo & soil moisture |
| Pest & Disease | 8004 | Risk assessment engine |
| Reporting Service | 8005 | PDF generation |
| User Dashboard | 8080 | Web UI |

### Access
- Dashboard: http://localhost:8080
- Farm Calendar: http://localhost:8002
- API docs: http://localhost:8002/api/v1/docs (Swagger)

---

## OpenAgri-GateKeeper -- Authentication
**Repo**: https://github.com/agstack/OpenAgri-GateKeeper  
**License**: EUPL 1.2

Lightweight JWT-based auth proxy. All services authenticate through GateKeeper.

```bash
git clone https://github.com/agstack/OpenAgri-GateKeeper.git
cd OpenAgri-GateKeeper
cp .env.sample .env
# Set: SECRET_KEY, DATABASE_URL, ALLOWED_DOMAINS
docker compose up -d
# GateKeeper runs on port 8000
```

**Auth flow:**
```
Client → POST /auth/login (username + password)
      ← JWT token (expires configurable)

Client → GET /api/v1/... with Authorization: Bearer {token}
      ← Data (GateKeeper validates and forwards)
```

---

## Service-by-Service Deployment

### Farm Calendar (standalone)
```bash
git clone https://github.com/agstack/OpenAgri-FarmCalendar.git
cp .env.sample .env
# If no GateKeeper: remove GATEKEEPER_LOGIN_URL from .env
docker compose run --rm web python3 manage.py initial_setup
docker compose run --rm web python3 manage.py createsuperuser
docker compose up -d
# http://localhost:8002
```

### Weather Service (standalone)
```bash
git clone https://github.com/agstack/OpenAgri-WeatherService.git
cp .env.sample .env
# Set: WEATHER_API_KEY (provider key - e.g., OpenWeatherMap)
docker compose up -d
# http://localhost:8001
```

### Irrigation Management (standalone)
```bash
git clone https://github.com/agstack/OpenAgri-IrrigationManagement.git
# Uses Python 3.11, FastAPI, Alembic, SQLAlchemy
docker compose up -d
# http://localhost:8003
```

### Pest & Disease (standalone)
```bash
git clone https://github.com/agstack/OpenAgri-PestAndDiseaseManagement.git
docker compose up -d
# http://localhost:8004
```

### Reporting Service (standalone)
```bash
git clone https://github.com/agstack/OpenAgri-ReportingService.git
docker compose up -d
# Depends on Farm Calendar for data
# http://localhost:8005
```

---

## OpenAgri Common Semantic Model (OCSM)
**Repo**: https://github.com/agstack/OpenAgri-OCSM  
All services exchange data in JSON-LD format following OCSM. This ensures interoperability -- Farm Calendar data can feed Pest & Disease, which feeds Reporting, etc.

```bash
git clone https://github.com/agstack/OpenAgri-OCSM.git
# Contains: ontology definitions, JSON-LD context files, Jupyter notebooks for exploration
jupyter notebook notebooks/ocsm_exploration.ipynb
```

---

## Minimal Setup for a Small Farm (Single Machine)

For a 1.2-acre demonstration farm with limited IT resources, this is the practical minimum:

**Option A -- Cloud (Recommended for reliability)**
1. Free tier: DigitalOcean Droplet ($6/month), Railway.app, or Render.com
2. Run Bootstrap-Deployment on cloud VM
3. Access everything via mobile browser

**Option B -- Local PC (offline-capable)**
1. Any laptop with 4GB+ RAM running Docker Desktop
2. Bootstrap-Deployment runs locally
3. Backup data regularly to USB/cloud

**Option C -- Public hosted services**
- Asset Registry: https://asset-registry.agstack.org (hosted by AgStack)
- Use only this for field registration, manual entry for other data

---

## Minimum Viable Setup for Your Project

Given you have a tractor and basic farming knowledge, focus on:

1. **Week 1**: Register your field at `asset-registry.agstack.org` (free, no setup)
2. **Month 1**: Set up Farm Calendar on any PC -- Docker Desktop + FarmCalendar repo
3. **Month 2**: Add Weather Service -- enter coordinates for daily ETo
4. **Month 3**: Add Pest & Disease rules for your main crops

You don't need all 41 repos. Start with field registry + farm calendar + weather. Add as needed.
