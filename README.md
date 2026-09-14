# UiPath Open Source

[![Build Status](https://github.com/VOTRE_UTILISATEUR/uipath-open-source/actions/workflows/ci.yml/badge.svg)](https://github.com/VOTRE_UTILISATEUR/uipath-open-source/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![UiPath Studio](https://img.shields.io/badge/UiPath-Studio%202023.10+-blue.svg)](https://www.uipath.com/)

Projet d'automatisation RPA open source construit avec UiPath Studio, basé sur le **Robotic Enterprise Framework (REFramework)**. Conçu pour être pédagogique, maintenable et extensible.

## Cas d'usage

> **TODO** : Décrivez ici le processus métier automatisé (ex : traitement de factures, extraction de données publiques, reporting automatisé...).

## Fonctionnalites

- Architecture REFramework (Init / Get Transaction Data / Process / End Process)
- Gestion des exceptions (Business vs System)
- Configuration externalisee via `Config.xlsx`
- Logging structuré (Info / Warn / Error)
- Tests intégrés via UiPath Test Framework

## Prérequis

| Composant | Version minimum |
|-----------|-----------------|
| UiPath Studio | Community Edition 2023.10+ |
| UiPath Orchestrator | Community Cloud (optionnel) |
| Windows | 10/11 x64 |
| .NET Framework | 4.6.1+ |

## Installation

```bash
# 1. Cloner le dépôt
git clone https://github.com/VOTRE_UTILISATEUR/uipath-open-source.git
cd uipath-open-source

# 2. Ouvrir dans UiPath Studio
# Fichier > Ouvrir projet > sélectionner project.json

# 3. Restaurer les packages
# Le panneau Package Manager téléchargera les dépendances automatiquement

# 4. Configurer les paramètres
# Modifier src/Config/Config.xlsx selon votre environnement

# 5. Exécuter
# Appuyer sur F5 ou cliquer sur Run dans UiPath Studio
```

## Structure du projet

```
uipath-open-source/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── docs/
│   ├── PDD.md              # Process Definition Document
│   └── SDD.md              # Solution Design Document
├── src/
│   ├── Main.xaml           # Point d'entrée
│   ├── Framework/          # Composants REFramework
│   │   ├── InitAllSettings.xaml
│   │   ├── GetTransactionData.xaml
│   │   ├──Process.xaml
│   │   ├──SetTransactionStatus.xaml
│   │   └──EndProcess.xaml
│   └── Config/
│       └── Config.xlsx     # Configuration centralisée
├── tests/
│   └── ...
└── .github/
    └── workflows/
        └── ci.yml          # CI/CD GitHub Actions
```

## Utilisation

1. **Configuration** : Editez `src/Config/Config.xlsx` pour adapter les paramètres à votre environnement
2. **Exécution** : Lancez le workflow depuis UiPath Studio (F5) ou depuis Orchestrator
3. **Monitoring** : Consultez les logs dans Orchestrator ou dans le fichier de log local

## Contribution

Voyez [CONTRIBUTING.md](CONTRIBUTING.md) pour les guidelines de contribution.

## Licence

Ce projet est distribué sous la licence MIT. Voyez [LICENSE](LICENSE) pour plus de détails.

## Ressources

- [Documentation UiPath](https://docs.uipath.com/)
- [REFramework Overview](https://docs.uipath.com/studio/standalone/2023.10/en/reframework)
- [UiPath Forum](https://forum.uipath.com/)
