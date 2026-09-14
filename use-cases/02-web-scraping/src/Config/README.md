# Configuration — Web Scraping

Creer le fichier `Config.xlsx` avec les onglets suivants :

## Onglet Settings

| Key | Value |
|-----|-------|
| TargetURL | https://example.com/data |
| SelectorPrincipal | `<html>...` (selecteur CSS/XPath du conteneur) |
| OutputFile | C:\donnees_extraites.xlsx |
| MaxRetries | 3 |

## Onglet Constants

| Key | Value |
|-----|-------|
| TimeoutNavigation | 30 |
| WaitForElementSeconds | 10 |

### Securite

- Verifier le `robots.txt` du site cible avant toute extraction
- Ne pas extraire de donnees personnelles
- Respecter les conditions d'utilisation du site
