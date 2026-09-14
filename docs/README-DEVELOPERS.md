# Guide pour les developpeurs

## Architecture technique

Monorepo multi-modules. Chaque module est un projet UiPath autonome avec son propre REFramework.

```
uipath-open-source/
├── .github/workflows/ci.yml    # CI/CD GitHub Actions
├── docs/
│   ├── ARCHITECTURE.md          # Architecture globale
│   ├── ROADMAP.md               # Feuille de route
│   ├── README-USERS.md          # Guide utilisateur
│   └── README-DEVELOPERS.md     # Ce fichier
└── use-cases/
    ├── 01-invoice-processing/   # Module factures
    ├── 02-web-scraping/         # Module web scraping
    ├── 03-email-automation/     # Module e-mails
    └── 04-api-integration/      # Module API
```

## Pre-requis

| Outil | Version | Usage |
|-------|---------|-------|
| UiPath Studio | 2024.10+ Community | Developpement |
| UiPath CLI | 25.10.x | CI/CD |
| .NET SDK | 8.0+ | UiPath CLI |
| Git | 2.x | Versionning |

## Structure d'un module

Chaque module suit le pattern REFramework :

```
module/
├── README.md
├── docs/
│   ├── PDD.md                  # Process Definition Document
│   └── SDD.md                  # Solution Design Document
├── src/
│   ├── project.json            # Meta-donnees du projet UiPath
│   ├── Main.xaml               # Point d'entree
│   ├── Framework/
│   │   ├── InitAllSettings.xaml
│   │   ├── GetTransactionData.xaml
│   │   ├── Process.xaml        # Logique metier
│   │   ├── SetTransactionStatus.xaml
│   │   └── EndProcess.xaml
│   └── Config/
│       └── Config.xlsx         # Configuration (a creer)
└── tests/
    ├── Unit/
    └── Integration/
```

## REFramework — Cycle de vie

```
Init → Get Transaction Data → Process → Set Transaction Status → End Process
                                ↑                                    |
                                └────────────────────────────────────┘
                                         (loop until no more transactions)
```

- **Init** : Charge Config.xlsx, verifie les pre-requis
- **GetTransactionData** : Recupere la prochaine transaction
- **Process** : Execute la logique metier
- **SetTransactionStatus** : Marque la transaction (Success/Business Exception/System Exception)
- **End Process** : Log du resume, fermeture

## Gestion des exceptions

| Type | Quand | Comportement |
|------|-------|--------------|
| Business Exception | Erreur metier previsible (champ manquant, incoherence) | Transaction echecée, traitement continue |
| System Exception | Erreur technique (fichier corrompu, site inaccessible) | Retry (MaxRetry), puis arret |

## CI/CD — GitHub Actions

Le pipeline execute pour chaque module :

1. **Checkout** du code
2. **Setup .NET 8**
3. **Install UiPath CLI** (`dotnet tool install --global UiPath.CLI.Windows`)
4. **Restore** des packages NuGet
5. **Analyze** via Workflow Analyzer
6. **Pack** en fichier .nupkg
7. **Upload** de l'artefact

```yaml
# .github/workflows/ci.yml
strategy:
  matrix:
    module:
      - use-cases/01-invoice-processing
      - use-cases/02-web-scraping
      - use-cases/03-email-automation
      - use-cases/04-api-integration
```

## Commandes utiles

```bash
# Restaurer les packages
uipcli package restore use-cases/01-invoice-processing/src/project.json

# Analyser le code
uipcli package analyze use-cases/01-invoice-processing/src/project.json

# Packager
uipcli package pack use-cases/01-invoice-processing/src/project.json -o ./output
```

## Ajouter un nouveau module

1. Creer le dossier `use-cases/05-nom-module/`
2. Copier la structure d'un module existant
3. Creer `project.json` avec les dependencies
4. Implementer les 5 workflows REFramework
5. Creer `docs/PDD.md` et `docs/SDD.md`
6. Ajouter le module dans la matrice CI (`ci.yml`)
7. Tester localement via UiPath Studio

## Conventions de code

### Nommage

| Element | Convention | Exemple |
|---------|-----------|---------|
| Fichiers XAML | PascalCase | `InitAllSettings.xaml` |
| Variables | camelCase | `transactionItem` |
| Arguments in | prefix `in_` | `in_ConfigPath` |
| Arguments out | prefix `out_` | `out_Result` |
| Arguments io | prefix `io_` | `io_Counter` |

### Packages UiPath

| Package | Usage |
|---------|-------|
| UiPath.Workflow | Core activities |
| UiPath.Excel.Activities | Manipulation Excel |
| UiPath.WebAPI.Activities | Appels API REST |
| UiPath.Mail.Activities | IMAP/SMTP/Outlook |
| UiPath.PDF.Activities | Lecture PDF |
| UiPath.System.Activities | File I/O, Logging |

## Tester

```bash
# Via UiPath CLI
uipcli test --project-path ./tests --test-folder .

# Via UiPath Studio
# Menu > Testing > Run Tests
```

## Debug

1. Ouvrir le module dans UiPath Studio
2. Positionner un breakpoint sur le workflow desire
3. Appuyer sur **F5** (mode Debug)
4. Utiliser les "Watch" pour inspecter les variables
