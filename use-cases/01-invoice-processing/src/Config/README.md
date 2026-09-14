# Configuration — Traitement de factures

Creer le fichier `Config.xlsx` avec les onglets suivants :

## Onglet Settings

| Key | Value |
|-----|-------|
| InputFolder | C:\Input\ |
| ProcessedFolder | C:\Processed\ |
| ErrorsFolder | C:\Errors\ |
| OutputFile | C:\factures_traitees.xlsx |
| MontantSeuilVerification | 10000 |
| ToleranceTVA | 0.01 |

## Onglet Constants

| Key | Value |
|-----|-------|
| TimeoutSeconds | 30 |
| MaxRetryNumber | 3 |

## Onglet Assets

| Name | Store | Credential |
|------|-------|------------|
| (vide en local) | Orchestrator | (a configurer) |

### Securite

- Ne jamais commiter ce fichier avec des credentials reels
- Utiliser les Orchestrator Assets pour les secrets
- Ajouter ce fichier au `.gitignore` en production
