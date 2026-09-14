# UiPath Open Source

![CI](https://img.shields.io/badge/build-passing-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![UiPath](https://img.shields.io/badge/UiPath-Studio%202024.10%2B-orange)

Depot open source de demonstration regroupant **4 automatisations RPA independantes**, construites avec UiPath Studio et le **REFramework**, illustrant chacune un cas d'usage metier courant. Objectif : servir de reference pedagogique pour apprendre les bonnes pratiques UiPath (gestion des exceptions, configuration externalisee, logging, tests, CI/CD).

## Cas d'usage inclus

| # | Module | Description | Complexite |
|---|--------|-------------|------------|
| 01 | [Traitement de factures](use-cases/01-invoice-processing) | Extraction de donnees (fournisseur, montant, date) depuis des factures PDF/Excel | Moyenne |
| 02 | [Web Scraping](use-cases/02-web-scraping) | Extraction de donnees publiques depuis un site web et export structure | Faible |
| 03 | [Automatisation e-mails](use-cases/03-email-automation) | Tri, classification et reponse automatique a des e-mails entrants | Moyenne |
| 04 | [Integration API](use-cases/04-api-integration) | Synchronisation de donnees entre une API externe et un systeme interne | Elevee |

## Structure du depot

```
uipath-open-source/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── .gitignore
├── .github/workflows/ci.yml
├── docs/
│   ├── ARCHITECTURE.md
│   └── ROADMAP.md
└── use-cases/
    ├── 01-invoice-processing/
    │   ├── README.md
    │   ├── docs/PDD.md
    │   ├── docs/SDD.md
    │   ├── src/Main.xaml
    │   ├── src/Framework/
    │   ├── src/Config/Config.xlsx
    │   └── tests/
    ├── 02-web-scraping/
    ├── 03-email-automation/
    └── 04-api-integration/
```

## Demarrage rapide

1. Cloner le depot : `git clone https://github.com/<votre-compte>/uipath-open-source.git`
2. Ouvrir UiPath Studio
3. Choisir un module dans `use-cases/` et ouvrir son `src/project.json`
4. Lire le `docs/PDD.md` et `docs/SDD.md` du module pour comprendre le processus avant de lancer
5. Configurer `src/Config/Config.xlsx` (identifiants via Orchestrator Assets recommande)

## Documentation

- [Architecture globale du monorepo](docs/ARCHITECTURE.md)
- [Feuille de route du projet](docs/ROADMAP.md)
- [Guide de contribution](CONTRIBUTING.md)

## Licence

Ce projet est distribue sous licence [MIT](LICENSE).
