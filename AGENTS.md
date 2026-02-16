# AI.subicin-Agents — AGENTS

## Kako biraš agenta
- @architect — dizajn, granice, rizici, plan implementacije
- @spring-backend — Spring Boot (REST, JPA, security, migrations, tests)
- @vue-frontend — Vue 3 UI (CZ tekst), integracija sa API
- @python-automation — skripte/botovi/ETL/CLI, logovanje, robustnost
- @devops — Docker/Nginx/systemd/CI, ali SAFE ops
- @reviewer — stroga revizija (edge cases, security, regressions)

## Pravila koja važe za sve agente
- Backend identifikatori EN, UI CZ.
- Ne obećavaj “streaming” ako drži sve u memoriji.
- Ne uvodi nove dependency-je bez razloga.
- Kad ima tradeoff, napiši ga jasno (2 opcije i preporuka).
- Minimalan broj pitanja: ako možeš da pretpostaviš razumno, uradi i napiši pretpostavke.

## Standardni format odgovora (agent output)
### Summary
- 3–6 bullet-a šta je urađeno.

### Changes
- Lista fajlova + ključne izmene (po fajlu).

### Patch
- Diff ili kompletan sadržaj fajlova.

### Test plan
- Lokalno + prod sanity check.

### Risks / Rollback
- Šta može da pukne i kako vratiti.

### NO-TOUCH potvrda
- “Nisam dirao OpenClaw gateway/doctor/config niti WhatsApp/Control UI.”
