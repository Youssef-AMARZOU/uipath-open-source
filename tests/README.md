# Tests

Ce dossier contient les tests du projet.

## Types de tests

### Tests unitaires

- Tests des workflows individuels
- Validation des regles métier
- Tests des fonctions utilitaires

### Tests d'integration

- Tests bout-en-bout du processus
- Tests d'integration avec les systemes externes
- Tests de performance

## Execution des tests

### Via UiPath Studio

1. Ouvrir le projet dans UiPath Studio
2. Menu > Testing > Run Tests
3. Selectionner les tests a executer

### Via UiPath CLI

```bash
uipath test --project-path ./tests --test-folder .
```

### Via CI/CD

Les tests sont executes automatiquement lors de chaque push via GitHub Actions.

## Structure des tests

```
tests/
├── README.md
├── Unit/
│   └── TestProcess.xaml
└── Integration/
    └── TestEndToEnd.xaml
```

## Ajouter un test

1. Creer un nouveau workflow dans le dossier approprie
2. Utiliser les activities de test UiPath
3. Ajouter des assertions pour valider les resultats
4. Committer le test avec le code correspondant
