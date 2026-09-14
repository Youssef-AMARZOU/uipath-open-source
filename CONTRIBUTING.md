# Guide de Contribution

Merci de votre interet pour contribuer a ce projet RPA open source !

## Types de contribution

- **Bug fixes** : Correction de bugs dans les workflows
- **Nouvelles fonctionnalites** : Ajout de nouveaux processus ou composants
- **Documentation** : Amelioration de la doc existante
- **Tests** : Ajout de tests unitaires ou d'intégration

## Processus de contribution

### 1. Fork le projet

```bash
git clone https://github.com/VOTRE_UTILISATEUR/uipath-open-source.git
```

### 2. Creer une branche

```bash
git checkout -b feature/ma-nouvelle-fonctionnalite
```

### 3. Branches

| Branche | Usage |
|---------|-------|
| `main` | Version stable |
| `develop` | Developpement |
| `feature/*` | Nouvelles fonctionnalites |
| `bugfix/*` | Corrections de bugs |
| `release/*` | Preparation d'une release |

### 4. Conventions de code

#### Nommage des fichiers
- Utiliser le **PascalCase** pour les noms de fichiers `.xaml` : `InitAllSettings.xaml`
- Pas d'espaces dans les noms de fichiers

#### Nommage des variables
- `in_` pour les arguments d'entree
- `out_` pour les arguments de sortie
- `io_` pour les arguments en entree/sortie
- PascalCase pour les variables : `TransactionItem`, `ConfigPath`

#### Structure des workflows
- Un workflow = une tache atomique
- Commenter les etapes complexes
- Utiliser les Retry Scope pour les appels API
- Gerer les Business Exceptions separement des System Exceptions

### 5. Workflow Analyzer

Avant de soumettre une PR, executez le Workflow Analyzer pour valider les bonnes pratiques :

```
UiPath Studio > Analyze > Run Workflow Analyzer
```

Corriger toutes les erreurs et warnings avant soumission.

### 6. Tester vos changements

```bash
# Executer les tests via UiPath Studio
# Menu > Testing > Run Tests
```

### 7. Soumettre une Pull Request

- Decrivez vos changements dans la PR
- Referencez les issues associees (ex: `Fixes #12`)
- Joignez des captures d'ecran si applicable
- Assurez-vous que la CI passe

### 8. Revue de code

- Minimum 1 revue requireise avant merge
- Resoudre tous les commentaires avant merge

## Issues

- Utiliser les templates d'issues GitHub
- Titrer clairement : `[Bug]`, `[Feature]`, `[Doc]`
- Fournir les etapes de reproduction pour les bugs

## Code of Conduct

En participant, vous acceptez le [Code of Conduct](CODE_OF_CONDUCT.md).
