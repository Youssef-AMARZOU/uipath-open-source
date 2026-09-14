# Process Definition Document — Traitement de factures

## 1. Objectif du processus

Automatiser la lecture de factures fournisseurs recues au format PDF (ou Excel), l'extraction des donnees cles, leur validation, et leur enregistrement dans un fichier de suivi (Excel), en isolant les factures necessitant une intervention humaine.

## 2. Perimetre

**Dans le perimetre :**
- Factures au format PDF (texte naturel ou scanne) deposees dans un dossier local `Input/`
- Extraction : numero de facture, nom du fournisseur, date d'emission, montant HT, montant TTC, devise
- Validation des montants (coherence HT/TTC/TVA)
- Ecriture dans un fichier `factures_traitees.xlsx`
- Deplacement des fichier traites vers `Processed/` ou `Errors/`

**Hors perimetre :**
- Integration a un ERP reel (demonstration uniquement)
- Paiement ou validation comptable
- Gestion multi-devises avec conversion automatique

## 3. Acteurs

| Acteur | Role |
|---|---|
| Robot UiPath | Execute l'extraction et la validation |
| Utilisateur metier | Depose les factures, consulte le fichier de suivi, traite les exceptions |

## 4. Etapes du processus (As-Is manuel → automatise)

1. Une facture PDF arrive dans le dossier `Input/`
2. Le robot ouvre le fichier et extrait le texte (OCR si necessaire)
3. Le robot identifie les cles via expressions regulieres ou UiPath Document Understanding
4. Le robot valide que : montant TTC = montant HT + TVA (marge de tolerance 0,01)
5. Si valide → ecriture dans `factures_traitees.xlsx`, fichier deplace vers `Processed/`
6. Si invalide ou champ manquant → fichier deplace vers `Errors/`, ligne ajoutee avec le motif dans `factures_traitees.xlsx`

## 5. Regles metier

- Un numero de facture est obligatoire ; son absence est une exception metier bloquante pour cette transaction
- Une facture dont le montant TTC depasse 10 000 (devise du Config) est marquee "a verifier manuellement" meme si les calculs sont coherents
- Les fichiers non-PDF dans `Input/` sont ignores et journalises en warning

## 6. Exceptions

| Type | Exemple | Traitement |
|---|---|---|
| Business Exception | Champ obligatoire manquant, incoherence de montants | Transaction en echec, fichier vers `Errors/`, traitement continue |
| System Exception | Fichier PDF corrompu, acces disque refuse | Retry (3 tentatives), puis arret du job si echec persistant |

## 7. Volumetrie estimee (demonstration)

- 10 a 50 factures par execution
- Frequence : declenchement manuel ou planifie (ex. toutes les heures)

## 8. Indicateurs de succes (KPI)

- Taux de factures traitees sans intervention manuelle
- Temps moyen de traitement par facture
- Nombre d'exceptions metier par execution
