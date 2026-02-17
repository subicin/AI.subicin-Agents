# AI.subicin-Agents

Repo sa definicijama i pravilima za “programerske agente” (Codex + specijalizovani agenti) koji ubrzavaju razvoj i smanjuju greške.

Cilj: **produkcijski kvalitet**, manje improvizacije, jasni test planovi i rollback.

## Repo structure

AI.subicin-Agents/
IDENTITY.md # Ko smo, jezik, hard rules (NO-TOUCH), standardi
AGENTS.md # Koji agent za šta + zajednička pravila
agents/ # Definicije uloga (architect, reviewer, backend, frontend...)
workflows/ # Standardni workflow (task -> design -> impl -> review -> merge)
templates/ # Task brief i PR checklist šabloni
tests/ # Brzi eval testovi da se proveri kvalitet agenta

markdown
Copy code

## Quick start (kako se koristi)

1) **Napiši task** koristeći šablon:
   - `templates/task-brief.md`

2) **Dizajn + plan**:
   - pozovi `@architect` (ili orchestrator ako ga koristiš)

3) **Implementacija**:
   - `@spring-backend` / `@vue-frontend` / `@python-automation` / `@devops`

4) **Review gate**:
   - `@reviewer` mora da potvrdi “Must fix” pre merge-a

5) **PR checklist**:
   - `templates/pr-checklist.md`

## Agents (kratko)

- `@architect` — arhitektura, granice, plan, rizici
- `@reviewer` — stroga revizija (correctness > stil)
- `@spring-backend` — Spring Boot REST/JPA/migrations/tests
- `@vue-frontend` — Vue 3 UI (CZ tekst), UX states, integracija
- `@python-automation` — skripte/botovi/ETL, logovanje, robustnost
- `@devops` — Docker/Nginx/systemd/CI, **SAFE ops**

Detalji: vidi `AGENTS.md` i fajlove u `agents/`.

## Standards (obavezno)

### Jezik i naming
- Komunikacija: **srpski**, direktno.
- Backend identifikatori: **EN** (class/field/DTO/route/DB).
- Frontend UI tekst: **CZ** (labeli, dugmad, validacije, poruke).

### Output format (svaki zadatak)
Agent mora da vrati:
1) Summary
2) Changes (po fajlu)
3) Patch (diff ili komplet fajl)
4) Test plan
5) Risks / Rollback
6) NO-TOUCH potvrda

### “Ne izmišljaj”
- Ne tvrdi da radi ako ne može da se build-uje / nije realno.
- Kod “streaming + Content-Length”: objasni tradeoff (temp file vs chunked).

## Safety: NO-TOUCH (hard rule)

Zabranjeno:
- dirati OpenClaw gateway/doctor/config u produkciji
- destabilizovati Control UI / WhatsApp flow

Ako zadatak implicira gore navedeno:
- agent daje **plan** + izolovano rešenje (feature flag / dokument / zaseban servis),
- ali ne radi “brze” izmene na postojećem setup-u.

## Recommended project policy

- Prvo testiranje agenata na **FajnTaxi** (sandbox).
- AthenaJob i produkcioni sistemi tek nakon eksplicitnog odobrenja + zaštite grana (PR + review).

## Agent evaluation (brza provera kvaliteta)

Fajl: `tests/agent-evals.md`

Koristi ga kad:
- uvodiš novog agenta
- menjaš pravila
- sumnjaš u “haluciniranje” ili nepoštovanje standarda

## License / Notes

Interni standardi i šabloni za tvoje projekte.
