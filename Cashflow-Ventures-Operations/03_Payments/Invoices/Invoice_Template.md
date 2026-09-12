# Invoice

**Invoice #:** INV-{{ID}}_{{VENTURE}}_{{BUSINESS_NAME}}_{{INVOICE_TYPE}}
**Client ID:** {{CLIENT_ID}}  |  **Lead ID:** {{LEAD_ID}}
**Venture:** {{VENTURE}}
**Invoice Date:** {{INVOICE_DATE}}
**Due Date:** {{DUE_DATE}}

---

**Billed To**
{{BUSINESS_NAME}}
Attn: {{CLIENT_NAME}}
{{CLIENT_EMAIL}} · {{CLIENT_PHONE}}

**From**
{{YOUR_COMPANY}}
{{YOUR_EMAIL}} · {{YOUR_PHONE}}

---

## Invoice Detail

| Description | Venture | Project Type | Amount |
|---|---|---|---|
| {{INVOICE_LINE_DESCRIPTION}} (e.g. 50% Deposit / 50% Final Payment / Monthly Hosting) | {{VENTURE}} | {{PROJECT_TYPE}} | {{AMOUNT}} |

**Total Due: {{AMOUNT}}**

## Payment Instructions

- **Payment Link:** {{PAYMENT_LINK_PLACEHOLDER}}  *(no live payment processor connected yet — send the client your current preferred payment method: bank transfer, payment link, etc.)*
- **Payment Terms:** Due on {{DUE_DATE}}
- Please reference **{{INVOICE_ID}}** with your payment.

## Notes

{{NOTES}}

---
*Template placeholders: `{{VENTURE}}`, `{{PROJECT_TYPE}}`, `{{CLIENT_ID}}`, `{{LEAD_ID}}`, `{{BUSINESS_NAME}}`, `{{CLIENT_NAME}}`, `{{CLIENT_EMAIL}}`, `{{CLIENT_PHONE}}`, `{{INVOICE_DATE}}`, `{{DUE_DATE}}`, `{{AMOUNT}}`, `{{INVOICE_ID}}`, `{{PAYMENT_LINK_PLACEHOLDER}}`, `{{NOTES}}`, `{{YOUR_COMPANY}}`, `{{YOUR_EMAIL}}`, `{{YOUR_PHONE}}`.
Works for either venture — just swap `{{VENTURE}}` and `{{PROJECT_TYPE}}`.*
