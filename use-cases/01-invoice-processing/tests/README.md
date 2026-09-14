# Tests — Traitement de factures

## Tests unitaires

| Test | Description |
|------|-------------|
| Test_ExtractInvoiceNumber | Valide l'extraction du numero de facture via RegEx |
| Test_ExtractAmounts | Valide l'extraction des montants HT/TTC/TVA |
| Test_ValidateAmountsOK | Monte TTC = HT + TVA (dans la tolerance) |
| Test_ValidateAmountsKO | Monte TTC != HT + TVA (hors tolerance) |
| Test_InvoiceNumberRequired | Absence de numero → Business Exception |
| Test_LargeAmountFlag | Montant TTC > 10000 → flag "a verifier" |

## Tests d'integration

| Test | Description |
|------|-------------|
| Test_ProcessValidInvoice | Facture complete et coherente → Processed/ |
| Test_ProcessInvalidInvoice | Facture incoherente → Errors/ |
| Test_ProcessCorruptedPDF | PDF corrompu → retry puis System Exception |
| Test_EndToEnd | Batch de 10 factures →Resume correct |

## Execution

```bash
# Via UiPath CLI
uipath test --project-path ./tests --test-folder .
```
