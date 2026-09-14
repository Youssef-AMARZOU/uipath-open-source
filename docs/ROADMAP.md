# Feuille de route — uipath-open-source

Roadmap couvrant la conception, le developpement et la publication des 4 modules d'automatisation.

## Vue d'ensemble par module

| Module | Priorite | Duree estimee | Pre-requis techniques |
|---|---|---|---|
| 01 — Traitement de factures | 1 (demarrer en premier, bon cas pedagogique) | 2-3 semaines | UiPath Document Understanding ou OCR + RegEx |
| 02 — Web Scraping | 2 (le plus simple, bon pour valider la CI) | 1 semaine | UiPath.Web.Activities / UiAutomation |
| 03 — Automatisation e-mails | 3 | 1,5-2 semaines | UiPath.Mail.Activities (IMAP ou Outlook) |
| 04 — Integration API | 4 (le plus complexe, a faire en dernier) | 2-3 semaines | UiPath.WebAPI.Activities, gestion OAuth/API Key |

**Duree totale estimee : 7 a 9,5 semaines** (peut etre parallellise si plusieurs contributeurs)

## Phase transverse — Fondations du depot (deja realisee)

- [x] Structure de depot, LICENSE, CONTRIBUTING, CODE_OF_CONDUCT
- [x] `.gitignore` adapte UiPath
- [x] Pipeline CI de base

## Phase par module (a repeter x4)

Pour chaque module, le cycle suit les memes 6 etapes :

1. **Cadrage** — rediger le PDD (perimetre, regles metier, volumetrie)
2. **Conception** — rediger le SDD (architecture technique, structure Config, diagramme de flux)
3. **Developpement** — implementer le REFramework (Init / GetTransactionData / Process / End)
4. **Tests** — cas nominaux, cas d'exception metier, cas d'exception systeme
5. **Documentation** — README du module avec captures d'ecran / GIF de demo
6. **Integration CI** — ajout du module a la matrice `ci.yml`, verification Workflow Analyzer

## Planning suggere (approche sequentielle, un seul contributeur)

| Semaine | Module | Activite |
|---|---|---|
| 1 | 01 - Factures | Cadrage + Conception (PDD/SDD) |
| 2 | 01 - Factures | Developpement + Tests |
| 3 | 01 - Factures | Documentation + integration CI, puis demarrage cadrage 02 |
| 4 | 02 - Web Scraping | Developpement complet (module simple) |
| 5 | 03 - E-mails | Cadrage + Conception + debut developpement |
| 6 | 03 - E-mails | Fin developpement + Tests + Documentation |
| 7 | 04 - API | Cadrage + Conception |
| 8 | 04 - API | Developpement (gestion auth, pagination, retries) |
| 9 | 04 - API | Tests + Documentation + finalisation globale du depot |

## Jalons de publication

- **v0.1.0** — Module 01 (factures) fonctionnel et documente
- **v0.2.0** — Module 02 (web scraping) ajoute
- **v0.3.0** — Module 03 (e-mails) ajoute
- **v1.0.0** — Les 4 modules fonctionnels, CI complete, documentation finalisee

## Apres la v1.0.0 (maintenance continue)

- Ouvrir des issues "good first issue" pour chaque module (ex. ajouter un fournisseur d'API alternatif, gerer un nouveau format de facture)
- Ajouter un 5e cas d'usage propose par la communaute
- Maintenir la compatibilite avec les nouvelles versions de UiPath Studio et des packages d'activites
