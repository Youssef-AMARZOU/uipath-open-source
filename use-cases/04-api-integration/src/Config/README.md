# Configuration — Integration API

Creer le fichier `Config.xlsx` avec les onglets suivants :

## Onglet Settings

| Key | Value |
|-----|-------|
| BaseURL | https://api.example.com/v1 |
| Endpoint | /data |
| PageSize | 100 |
| OutputFile | C:\api_data.xlsx |

## Onglet Auth

| Key | Value |
|-----|-------|
| AuthType | APIKey (ou OAuth2) |
| APIKey | (via Orchestrator Asset) |
| TokenEndpoint | https://auth.example.com/token |
| ClientID | (via Orchestrator Asset) |
| ClientSecret | (via Orchestrator Asset) |

## Onglet Retry

| Key | Value |
|-----|-------|
| MaxRetries | 3 |
| TimeoutSeconds | 30 |

### Securite

- Utiliser les Orchestrator Assets pour les cles API et secrets
- Ne jamais commiter de credentials dans le depot
- Les tokens OAuth ont une duree de vie limitee
