# Task brief

## Goal
Implementirati auto-zoom na mapu (Leaflet) tako da nakon dobijanja rute:
- mapa automatski radi `fitBounds()` na celu rutu
- korisnik dobije jasne UX state-ove: loading / error / empty
- UI tekstovi su na češkom (CZ)

## Context
Repo: **fajntaxi-website** (monorepo)
- Backend: Spring Boot u root-u (`src/main`, `pom.xml`)
- Frontend: Vue 3 + Vite u `frontend/`
Postoji funkcionalnost za routing (Mapy API) i Leaflet mapa već crta rutu nakon klika na dugme.

Relevantno:
- Leaflet Map komponenta (npr. `MapView.vue` ili slično)
- Routing poziv (npr. `frontend/src/.../api` ili direktno u view-u)
- Stranica gde korisnik unosi start/destination i klikne “Najít trasu” (ili slično)

## Constraints
- Backend identifikatori: **EN**
- UI tekst: **CZ**
- Bez novih dependency-ja ako nije baš potrebno
- Fokus je na **frontend** (backend menjati samo ako je potrebno za stabilan API)
- Ovo je sandbox: FajnTaxi je DOZVOLJENO
- AthenaJob je NO-TOUCH

## Acceptance criteria
- [ ] Nakon uspešnog dobijanja rute, mapa automatski zumira tako da je cela ruta vidljiva (sa padding-om).
- [ ] Ako API vrati praznu rutu / nema tačaka, prikaži “empty state” poruku (CZ) i ne pokušavaj fitBounds.
- [ ] Dok se ruta učitava, prikaži loading state (CZ), dugme je disabled.
- [ ] Ako dođe do greške (network/500/timeout), prikaži error state (CZ) + opcija “Zkusit znovu”.
- [ ] UI ima bar minimalnu UX obradu: clear prethodnu rutu pri novom requestu, i reset state-ova.
- [ ] Kod ostaje čist: izdvojen helper za fitBounds, nema “magic” timeout-a.
- [ ] Dodati kratak manual test plan u PR opisu.

## Inputs
### Pretpostavke (ako su fajlovi drugačiji)
Ako su nazivi fajlova drugačiji:
- “MapView” je komponenta koja dobija `routePoints` (array lat/lng) i crta polyline.
- “RoutingView” (ili slično) drži formu i poziva backend.

### API behavior
- Routing endpoint vraća listu tačaka (lat/lon) ili GeoJSON koji se već parsira u tačke.
- Ako nema tačaka, tretirati kao empty result.

## Definition of Done (PR)
- [ ] Summary / Changes / Patch / Test plan / Risks-Rollback / NO-TOUCH potvrda
- [ ] Nema unrelated refactor-a
- [ ] Lint/build prolazi:
  - Backend: `mvn -DskipTests package`
  - Frontend: `cd frontend && npm run build`
