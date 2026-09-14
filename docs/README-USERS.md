# Guide pour les utilisateurs

## C'est quoi ce projet ?

C'est une collection d'outils automatiques qui font des taches repetitives a votre place. Imaginez un assistant numerique qui :

- **Lit vos factures** et en extrait les informations importantes
- **Cherche des informations** sur internet pour vous
- **Classe vos e-mails** et repond automatiquement
- **Recupere des donnees** depuis des sites web et les met en forme

## Comment ca marche ?

Chaque outil est independant. Vous choisissez celui dont vous avez besoin :

| Outil | Ce qu'il fait | Pour qui |
|-------|---------------|----------|
| **Traitement de factures** | Lit les factures PDF, extrait les montants, verifie les calculs | Comptables, admins |
| **Web Scraping** | Recupere des donnees publiques (taux de change, offres d'emploi) | Analystes, chercheurs |
| **Automatisation e-mails** | Classe les e-mails et repond automatiquement | Assistants, support |
| **Integration API** | Recupere des donnees depuis des services en ligne | Tous |

## Comment l'utiliser ?

### Etape 1 : Telecharger

1. Aller sur la page GitHub du projet
2. Cliquer sur le bouton vert "Code"
3. Cliquer "Download ZIP"
4. Decompresser le fichier

### Etape 2 : Installer le logiciel

Vous avez besoin de **UiPath Studio** (gratuit) :
1. Aller sur https://www.uipath.com/download
2. S'inscrire et telecharger UiPath Studio Community
3. Installer et ouvrir le logiciel

### Etape 3 : Ouvrir un outil

1. Dans UiPath Studio, cliquer "Open Project"
2. Aller dans le dossier telecharge
3. Choisir un outil dans `use-cases/`
4. Ouvrir le fichier `project.json`

### Etape 4 : Configurer

Chaque outil a un fichier de configuration (`Config.xlsx`) a creer. C'est comme remplir un formulaire :

**Pour les factures :**
- Où sont les factures ? (chemin du dossier)
- Où mettre le resultat ? (chemin du fichier Excel)

**Pour les e-mails :**
- Quel serveur de mail ? (imap.gmail.com, etc.)
- Quels mots-cles pour classifier ?

### Etape 5 : Lancer

1. Appuyer sur **F5** ou cliquer "Run"
2. L'outil fait le travail tout seul
3. Consulter le resultat dans le fichier genere

## Questions frequentes

### C'est gratuit ?

Oui. UiPath Studio Community est gratuit pour un usage personnel. Le projet est aussi gratuit (licence MIT).

### C'est securise ?

Oui. Les outils ne touchent qu'aux dossiers que vous configurez. Ils n'envoient rien sur internet (sauf l'outil API qui contacte le service que vous configurez).

### Je ne suis pas technique, est-ce que je peux quand meme l' utiliser ?

Oui. Le guide ci-dessus suffit. Si vous bloquez, demandez a quelqu'un avec un minimum de bases en informatique de vous aider pour l'installation.

### Ca marche sur Mac ?

UiPath Studio est uniquement disponible sur Windows. Mais vous pouvez utiliser un Mac avec Windows via Parallels ou Boot Camp.

## Besoin d'aide ?

- Consulter la [documentation UiPath](https://docs.uipath.com/)
- Poser une question sur le [forum UiPath](https://forum.uipath.com/)
- Ouvrir un "Issue" sur GitHub (bouton "Issues" en haut de la page)
