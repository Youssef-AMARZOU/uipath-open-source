# Process Definition Document — Integration API

## 1. Objectif du processus

Automatiser la synchronisation de donnees depuis une API REST externe vers un systeme interne (fichier Excel ou BDD locale), en gerant l'authentification, la pagination et les erreurs.

## 2. Perimetre

**Dans le perimetre :**
- Appels HTTP GET/POST vers une API REST
- Authentification par API Key ou OAuth2
- Pagination automatique (par page ou par curseur)
- Gestion des rate limits et retries
- Export des donnees dans un fichier Excel

**Hors perimetre :**
- Ecriture dans une base de donnees externe
- Authentification par certificat client
- Webhooks ou temps reel

## 3. Acteurs

| Acteur | Role |
|---|---|
| Robot UiPath | Effectue les appels API, traite les reponses |
| Utilisateur metier | Configure l'API, consulte les donnees synchronisees |

## 4. Etapes du processus

1. Authentifier aupres de l'API (API Key dans header ou OAuth2 token)
2. Appeler l'endpoint de donnees avec pagination
3. Pour chaque page :
   a. Parser la reponse JSON
   b. Extraire les enregistrements
   c. Valider les champs obligatoires
4. Ecrire toutes les donnees dans Excel
5. Journaliser le resume (nb enregistrements, erreurs)

## 5. Regles metier

- Si le code HTTP est 429 (rate limit) → attendre le delai indique puis retry
- Si le code HTTP est 401/403 → arret immédiat (erreur d'authentification)
- Les enregistrements sans champ obligatoire sont ignores (warning)

## 6. Exceptions

| Type | Exemple | Traitement |
|---|---|---|
| Business Exception | Enregistrement incomplet | Ignore, warning, traitement continue |
| System Exception | Timeout, erreur reseau, 500 | Retry avec backoff exponentiel |

## 7. Volumetrie estimee

- 100 a 10 000 enregistrements par execution
- 1 a 100 pages par execution
- Frequence : quotidienne ou horaire
