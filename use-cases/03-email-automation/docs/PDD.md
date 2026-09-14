# Process Definition Document — Automatisation e-mails

## 1. Objectif du processus

Automatiser le tri, la classification et la reponse automatique a des e-mails entrants selon des regles metier definies.

## 2. Perimetre

**Dans le perimetre :**
- Connexion a une boite mail via IMAP ou Outlook
- Lecture des e-mails non lus
- Classification par mot-cles dans l'objet, expediteur, ou presence de pieces jointes
- Envoi de reponses automatiques预definies
- Deplacement des e-mails traites vers un dossier dedie

**Hors perimetre :**
- Classification avancee par IA/NLP
- Gestion des e-mails chiffrés
- Integration avec un CRM

## 3. Acteurs

| Acteur | Role |
|---|---|
| Robot UiPath | Lit, classifie, repond, deplace les e-mails |
| Utilisateur metier | Definit les regles de classification, consulte les logs |

## 4. Etapes du processus

1. Connexion a la boite mail (IMAP/Outlook)
2. Recuperation des e-mails non lus
3. Pour chaque e-mail :
   a. Verifier les regles de classification (mot-cles, expediteur)
   b. Si regle correspondante → extraire les donnees clées
   c. Envoyer la reponse automatique associee
   d. Deplacer l'e-mail vers le dossier "Traites"
4. Fermer la connexion

## 5. Regles metier

- Un e-mail avec "facture" dans l'objet → classification "Facture"
- Un e-mail avec "urgence" ou "urgent" → classification "Urgence"
- Un e-mail sans piece jointe et sans mot-cle specifique → "Non classifie"

## 6. Exceptions

| Type | Exemple | Traitement |
|---|---|---|
| Business Exception | E-mail sans objet | Ignore, warning journalise |
| System Exception | Serveur mail inaccessible | Retry puis arret |

## 7. Volumetrie estimee

- 50 a 200 e-mails par execution
- Frequence : toutes les heures ou toutes les 30 minutes
