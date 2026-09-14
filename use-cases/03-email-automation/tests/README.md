# Tests — Automatisation e-mails

## Tests unitaires

| Test | Description |
|------|-------------|
| Test_ClassifyBySubject | Classification par mot-cles dans l'objet |
| Test_ClassifyBySender | Classification par expediteur |
| Test_AutoReplySent | Reponse automatique envoyee |
| Test_EmailWithoutSubject | E-mail sans objet → ignore |

## Tests d'integration

| Test | Description |
|------|-------------|
| Test_FullCycle | E-mails lus, classes, repondus, deplaces |
| Test_ServerUnavailable | Serveur inaccessible → retry |

## Execution

```bash
uipath test --project-path ./tests --test-folder .
```
