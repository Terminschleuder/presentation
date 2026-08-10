# CLAUDE.md — presentation folder

This folder holds the **terminschleuder architecture & domain walkthrough** deck
(`terminschleuder-overview.md`) plus its README.

## Keep it in sync

The deck is a **derived artifact** — it summarizes the `backend/` (architecture,
data model, ingestion, geospatial/city-finding, auth, API surface) and the `frontend/`
(demo client stack & behavior).

**Any meaningful change in `../backend/` or `../frontend/` requires updating this folder too.**

Concretely, when you change any of the following, edit `terminschleuder-overview.md`
(and README if structure changes) to match:

- **`backend/docs/`** — architecture.md, data-model.md, api-reference.md, authentication.md,
  geospatial.md, admin.md, user-manual.md. The deck mirrors these; a doc change that would
  matter to a first-time audience needs a matching slide edit.
- **Routing** (`backend/config/urls.py`) — admin mount point, public landing, `/media/`,
  API prefix (the "URL routing" slide).
- **Domain model** (`backend/events/models.py`, `accounts/models.py`,
  `locations/models.py`) — new/renamed entities, fields, choices, lifecycle states, the
  Event/EventObservation trust boundary, provenance fields (the glossary, ERD, Event, and
  ingestion/promotion slides).
- **Proximity / city logic** (`backend/events/views.py`, `locations/`) — `near_city`
  resolution, `ST_DWithin`/distance behavior, online exclusion, `default_radius_km`
  tiers, the city dataset (the "how city finding works" and proximity slides).
- **Auth** (`backend/accounts/`, `config/settings.py`) — JWT/API-key/session mechanisms,
  lifetimes, groups, the `ingestion` group (the auth/authorization slides).
- **API surface** — endpoint additions/removals, pagination, CORS, OpenAPI schema
  (the public API surface and self-describing-API slides).
- **City / demo data** — `locations/data/european_cities_50k.json` (city count, tiers,
  filtering rules), `seed_cities`, `seed_demo` (the "where the data comes from" slides).
- **Demo client** (`frontend/`) — stack, what it demonstrates, the in-UI API-base
  configuration / one-image-any-backend story (the demo client slide).
- **Deployment** — `Dockerfile`, `Dockerfile.db`, `docker-compose.yml`, `start.sh`,
  management commands, the no-`down -v` rule (the deployment slide).

## Rules of thumb

- The deck is **high-level and for a first-time audience** — keep slides tight (bullets,
  tables, diagrams), not field-by-field dumps. Point to `backend/docs/` for depth.
- When adding a concept to the deck, add it to the **domain glossary** slide too.
- Verify accuracy against `backend/docs/` rather than restating from memory.
- Edits are just Markdown; **CI renders the deck to PDF** (`.github/workflows/ci.yml`
  runs the official `ghcr.io/marp-team/marp-cli` image and uploads a `slides` artifact).
  Local export (no build step needed): `npx @marp-team/marp-cli@latest terminschleuder-overview.md -o slides.pdf --html`.