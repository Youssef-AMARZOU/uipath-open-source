# Configuration — Automatisation e-mails

Creer le fichier `Config.xlsx` avec les onglets suivants :

## Onglet Settings

| Key | Value |
|-----|-------|
| MailServer | imap.example.com |
| Port | 993 |
| UseSSL | True |
| Username | (via Orchestrator Asset) |
| Password | (via Orchestrator Asset) |
| OutputFolder | C:\EmailLogs\ |

## Onglet Rules

| Key | Value |
|-----|-------|
| SubjectKeywords | facture, urgence, demande, alerte |
| SenderFilters | noreply@, alerts@ |
| AutoReplyTemplate | Merci pour votre message. Nous y repondrons sous 48h. |

### Securite

- Utiliser les Orchestrator Assets pour les identifiants
- Ne jamais stocker de mots de passe en dur
