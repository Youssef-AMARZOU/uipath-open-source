# Tests — Integration API

## Tests unitaires

| Test | Description |
|------|-------------|
| Test_AuthAPIKey | Authentification par API Key |
| Test_AuthOAuth2 | Authentification OAuth2 (client credentials) |
| Test_ParseJSON | Parsing d'une reponse JSON valide |
| Test_Pagination | Pagination automatique (next page) |

## Tests d'integration

| Test | Description |
|------|-------------|
| Test_FullSync | Synchronisation complete (toutes les pages) |
| Test_RateLimitHandling | 429 → attendre puis retry |
| Test_AuthFailure | 401/403 → arret immediat |

## Execution

```bash
uipath test --project-path ./tests --test-folder .
```
