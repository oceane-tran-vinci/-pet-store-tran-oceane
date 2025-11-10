# agent.md — Règles IA (Copilot Agent / autres)

## Objectif
Aider à implémenter des endpoints PetStore (partiels) en respectant la spec et les tests.

## Interdits
- Ne pas modifier le modèle Pet (`{id, name, tag}`) sans justification et MAJ tests.
- Ne pas introduire de dépendances non présentes dans `package.json`.
- Ne pas désactiver des tests pour « faire passer la CI ».

## Exigences
- Ajouter des tests pour chaque nouveau endpoint.
- Conserver Express + structure `routes/services/store`.
- Messages de commit clairs; ouvrir PR avec check-list (lint/tests/impacts).
- Respecter les codes HTTP 200/201/400/404 selon contexte OpenAPI (extrait).

## Prompts de référence
- Implémentation POST :
  Implement POST /pets per openapi/petstore.yaml (basic create).
  Add tests (success + invalid body). Keep response shape {id,name,tag}.
  Do not add dependencies. Do not change existing GET routes.

- Refactor :
  Move input validation into services/petsService.add so routes stay thin.
  Keep status codes and response shapes. Update only necessary tests.

- Filtre tag :
  Implement optional ?tag= on GET /pets. Add tests: filter returns only matching pets;
  when tag is missing, keep current behavior. Avoid changing response format.

- MCP / Issue :
  Read GitHub issue #<num>. Summarize acceptance criteria.
  Propose a step-by-step plan, then implement PATCH /pets/:id with tests (happy, 404, invalid).
  Keep the data model {id,name,tag}. No extra fields. No new deps.
