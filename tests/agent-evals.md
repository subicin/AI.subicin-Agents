# Agent evaluations (quick suite)

## 1) Java correctness
Objasni == vs equals sa 3 realna bug primera + 1 rečenica pravilo.
PASS: pominje null-safe i wrapper caching / string interning.

## 2) Spring 404 debugging
Controller postoji ali /api/users vraća 404. Daj top 8 uzroka + proveru svakog.
PASS: pominje context-path, component scan, security, proxy, mapping.

## 3) Excel export “hard mode”
Endpoint /api/leads/export.xlsx sa filter status + q.
Traženo:
- 200k+ redova bez OOM
- pravi Excel date
- objasni Content-Length tradeoff
PASS: koristi SXSSFWorkbook + paging/stream; Content-Length: temp file ili objašnjen chunked.

## 4) DB query
PostgreSQL: po danu total calls, completed, avg duration, top outcomes.
PASS: date_trunc + FILTER + pravilni joinovi.

## 5) Migration
Dodaj novu tabelu follow_up_tasks (Flyway). Link na Lead ili Partner.
PASS: constraints + index + rollback.

## 6) Vue list + filter
UI CZ. Lista taskova sa filter status + search + badge.
PASS: empty/loading/error state.

## 7) Security check
Proceni 10 sigurnosnih rizika u “file upload CV”.
PASS: size limit, content-type, AV scan option, path traversal, storage.

## 8) DevOps safe rollout
Nginx reverse proxy promena za novi /api route.
PASS: pre-check + rollback, bez diranja OpenClaw.

## 9) Code review trap
Daj mu kod koji koristi XSSFWorkbook + List<Lead> i tvrdi “streaming”.
PASS: agent kaže da nije streaming i ispravi.

## 10) Prompt adherence
Zadaj equals contract + transitivity (Point/ColorPoint).
PASS: ne skreće na drugo, daje transitivity primer i ispravku.
