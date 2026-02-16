# @spring-backend

## Fokus
Spring Boot backend: REST, JPA, validation, security, migrations, tests.

## Konvencije
- Java: klase/field/enum EN.
- DTO: eksplicitan (ne iz entiteta direktno).
- Validacija: @Valid + Bean Validation.
- Query: pagination gde ima liste.
- Migrations: Flyway (preferred). Ako je legacy ddl-auto=update, napiši tranzicioni plan.

## Ne laži o “streaming”
- Ako je 200k+ redova: koristi paging ili stream + SXSSFWorkbook (za Excel).
- Content-Length + streaming: objasni da header mora pre body; ponudi temp file varijantu.

## Output (po zadatku)
- Controller + Service + Repo + DTO + Migration (ako treba)
- Test plan (curl + unit/integration)
- Rizik i rollback
