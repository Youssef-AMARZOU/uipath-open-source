# Process Definition Document — Web Scraping de donnees publiques

## 1. Objectif du processus

Automatiser l'extraction periodique de donnees publiques depuis un site web (exemple : taux de change officiels ou offres d'emploi publiques), et produire un export structuré exploitable.

## 2. Perimetre

**Dans le perimetre :**
- Navigation vers une URL cible (site public, sans authentification requise)
- Extraction d'une liste d'elements structures (ex. devise, taux, date de mise a jour)
- Export au format `donnees_extraites.xlsx` avec horodatage
- Detection de changement de structure de la page (selecteur introuvable)

**Hors perimetre :**
- Sites necessitant une authentification ou un CAPTCHA
- Respect approfondi du `robots.txt` (a verifier manuellement avant tout usage reel)
- Extraction de donnees personnelles ou soumises a droit d'auteur

## 3. Acteurs

| Acteur | Role |
|---|---|
| Robot UiPath | Navigue, extrait, exporte |
| Utilisateur metier | Consulte l'export, ajuste l'URL/selecteurs si le site change |

## 4. Etapes du processus

1. Le robot ouvre le navigateur et accede a l'URL cible (definie dans `Config.xlsx`)
2. Il attend le chargement complet de l'element conteneur (attente explicite, pas de `Delay` fixe)
3. Il extrait la table ou la liste de donnees (Data Scraping / `Extract Structured Data`)
4. Il nettoie les donnees (suppression espaces, conversion de types)
5. Il ajoute un horodatage et ecrit les donnees dans `donnees_extraites.xlsx`
6. Il ferme le navigateur proprement

## 5. Regles metier

- Si le selecteur principal est introuvable apres 3 tentatives, le job s'arrete en exception systeme (le site a probablement change de structure)
- Les lignes avec une valeur numerique invalide sont ecartees et journalisees en warning, sans bloquer l'export des autres lignes

## 6. Exceptions

| Type | Exemple | Traitement |
|---|---|---|
| Business Exception | Ligne de donnee incomplete/invalide | Ligne ignoree, warning journalise, traitement continue |
| System Exception | Site inaccessible, selecteur introuvable | Retry (attente + nouvelle tentative), puis arret si echec persistant |

## 7. Volumetrie estimee

- Une execution par jour (ou selon planification)
- Quelques dizaines a centaines de lignes extraites par execution

## 8. Indicateurs de succes (KPI)

- Taux de disponibilite du site cible au moment de l'execution
- Nombre de lignes extraites avec succes vs ecartees
- Detection precoce d'un changement de structure du site
