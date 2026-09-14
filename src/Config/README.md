# Configuration

## Config.xlsx

Ce dossier contient le fichier de configuration centralise du projet.

### Structure du fichier

Le fichier `Config.xlsx` doit contenir les feuilles suivantes :

#### Feuille "Config"

| Key | Value |
|-----|-------|
| `TransactionQueueName` | Nom de la Queue Orchestrator |
| `MaxRetry` | 3 |
| `LogPath` | C:\Logs\uipath-open-source\ |
| `ConfigPath` | Chemin vers Config.xlsx |

#### Feuille "Credentials"

| Name | Store | Credential |
|------|-------|------------|
| `ServiceAccount` | Orchestrator | Credential Asset |

#### Feuille "Settings"

| Key | Value | DefaultValue |
|-----|-------|--------------|
| `Timeout` | 30 | 30 |
| `PageSize` | 100 | 100 |

### Utilisation

1. Copier ce fichier dans un emplacement securise (pas dans le repo)
2. Modifier les valeurs selon votre environnement
3. Configurer les Assets Orchestrator correspondants

### Securite

- Ne jamais commiter ce fichier avec des credentials reels
- Utiliser les Orchestrator Assets pour les secrets
- Ajouter ce fichier au `.gitignore` en production
