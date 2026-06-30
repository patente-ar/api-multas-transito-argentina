# Repo profile: api-multas-transito-argentina

## GitHub creation settings

- Owner: patente-ar
- Repository name: api-multas-transito-argentina
- Visibility: Public
- Add README: yes
- .gitignore: Node
- License: MIT License
- Homepage: https://patente.ar/api-multas
- Description: Ejemplos de integracion para consultar multas de transito en Argentina con la API de patente.ar.

## Topics

api, argentina, multas, transito, patentes, webhooks, openapi, nodejs, python

## SEO positioning

- Primary keyword: API multas Argentina
- Secondary keywords: API de multas de transito en Argentina, infracciones, API vehicular Argentina, API patente argentina
- Canonical commercial page: https://patente.ar/api-multas
- Public informational page: https://patente.ar/multas-transito
- Brand/entity link: https://patente.ar

## Repository features

- Enable Issues for integration questions.
- Enable Discussions only if there is time to moderate.
- Enable GitHub Pages from the `docs/` folder on `main`.
- Pin this repo on the GitHub profile after the README is published.
- Keep default branch as `main`.

## GitHub API metadata command

```bash
GH_TOKEN="$(security find-generic-password -a patente-ar -s codex-github:doc-apis-github -w)"
gh repo edit patente-ar/api-multas-transito-argentina \
  --description "Ejemplos de integracion para consultar multas de transito en Argentina con la API de patente.ar." \
  --homepage "https://patente.ar/api-multas" \
  --enable-issues=true
gh repo edit patente-ar/api-multas-transito-argentina --add-topic "api,argentina,multas,transito,patentes,webhooks,openapi,nodejs,python"
```
