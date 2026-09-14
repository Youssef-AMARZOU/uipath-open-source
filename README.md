# UiPath Open Source

[![CI](https://github.com/Youssef-AMARZOU/uipath-open-source/actions/workflows/ci.yml/badge.svg)](https://github.com/Youssef-AMARZOU/uipath-open-source/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![UiPath](https://img.shields.io/badge/UiPath-Studio%202024.10%2B-orange.svg)](https://www.uipath.com/)

Depot open source regroupant **4 automatisations RPA independantes**, construites avec UiPath Studio et le **REFramework**.

## Je suis... ?

| Vous etes ? | Guide recommande |
|-------------|------------------|
| **Utilisateur** (pas de bases techniques) | [Guide Utilisateur](docs/README-USERS.md) |
| **Developpeur** (RPA, UiPath, programmation) | [Guide Developpeur](docs/README-DEVELOPERS.md) |

## Cas d'usage inclus

| # | Module | Description | CI |
|---|--------|-------------|-----|
| 01 | [Traitement de factures](use-cases/01-invoice-processing) | Extraction de donnees depuis des factures PDF | [![CI](https://github.com/Youssef-AMARZOU/uipath-open-source/actions/workflows/ci.yml/badge.svg?job=build-and-analyze+(use-cases/01-invoice-processing))](https://github.com/Youssef-AMARZOU/uipath-open-source/actions) |
| 02 | [Web Scraping](use-cases/02-web-scraping) | Extraction de donnees publiques depuis un site web | [![CI](https://github.com/Youssef-AMARZOU/uipath-open-source/actions/workflows/ci.yml/badge.svg?job=build-and-analyze+(use-cases/02-web-scraping))](https://github.com/Youssef-AMARZOU/uipath-open-source/actions) |
| 03 | [Automatisation e-mails](use-cases/03-email-automation) | Tri et reponse automatique a des e-mails | [![CI](https://github.com/Youssef-AMARZOU/uipath-open-source/actions/workflows/ci.yml/badge.svg?job=build-and-analyze+(use-cases/03-email-automation))](https://github.com/Youssef-AMARZOU/uipath-open-source/actions) |
| 04 | [Integration API](use-cases/04-api-integration) | Synchronisation de donnees via API REST | [![CI](https://github.com/Youssef-AMARZOU/uipath-open-source/actions/workflows/ci.yml/badge.svg?job=build-and-analyze+(use-cases/04-api-integration))](https://github.com/Youssef-AMARZOU/uipath-open-source/actions) |

## Demarrage rapide

1. **Cloner** : `git clone https://github.com/Youssef-AMARZOU/uipath-open-source.git`
2. **Ouvrir** UiPath Studio
3. **Choisir** un module dans `use-cases/` et ouvrir `src/project.json`
4. **Configurer** `src/Config/Config.xlsx`
5. **Lancer** avec F5

## Tests CI

Le pipeline GitHub Actions verifie automatiquement chaque module :

- ✅ 4 modules testes
- ✅ Analyse statique (Workflow Analyzer)
- ✅ Packaging (.nupkg)
- ✅ Tous les tests passent

Voir les [details des actions](https://github.com/Youssef-AMARZOU/uipath-open-source/actions).

## Documentation

- [Guide Utilisateur](docs/README-USERS.md) — Explication simple pour non-techniques
- [Guide Developpeur](docs/README-DEVELOPERS.md) — Architecture, conventions, commandes
- [Architecture](docs/ARCHITECTURE.md) — Structure technique du monorepo
- [Feuille de route](docs/ROADMAP.md) — Planning et jalons
- [Contribution](CONTRIBUTING.md) — Comment contribuer

## Licence

Ce projet est distribue sous licence [MIT](LICENSE).
