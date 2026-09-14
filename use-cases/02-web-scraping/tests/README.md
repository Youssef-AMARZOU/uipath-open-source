# Tests — Web Scraping

## Tests unitaires

| Test | Description |
|------|-------------|
| Test_WaitForElement | Valide l'attente explicite de l'element conteneur |
| Test_ExtractData | Valide l'extraction structuree des donnees |
| Test_CleanData | Valide le nettoyage (espaces, types) |
| Test_InvalidRowSkipped | Ligne avec valeur invalide → warning, pas d'arret |

## Tests d'integration

| Test | Description |
|------|-------------|
| Test_FullExtraction | Extraction complete → fichier Excel genere |
| Test_SiteInaccessible | Site en erreur → retry puis System Exception |
| Test_SelectorChanged | Selecteur introuvable → System Exception |

## Execution

```bash
uipath test --project-path ./tests --test-folder .
```
