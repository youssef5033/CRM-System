# Overdue Payment Reminder — Email/Message Template

Use when the Payment Tracker shows a **Deposit Status** or **Final Payment Status** of "Overdue."

**Subject:** Friendly reminder — Invoice {{INVOICE_ID}} for {{BUSINESS_NAME}}

Hi {{CLIENT_NAME}},

Just a quick reminder that invoice **{{INVOICE_ID}}** for **{{AMOUNT}}** ({{PROJECT_TYPE}}, {{VENTURE}}) was due on **{{DUE_DATE}}** and is still outstanding.

- Payment link / method: {{PAYMENT_LINK_PLACEHOLDER}}
- Reference: {{INVOICE_ID}}

Let me know if you have any questions or if there's anything blocking payment on your end — happy to help sort it out. Once this clears we'll [resume work / proceed to final delivery / continue hosting].

Thanks,
{{YOUR_NAME}}
{{YOUR_COMPANY}}

---

## Workflow notes

1. Move a copy of the related invoice into this `Overdue/` folder for tracking once it passes its due date.
2. Log an Activity in the Master CRM's Activities tab with Activity Type "Payment Reminder."
3. Update the Payment Tracker's Deposit/Final Payment Status to "Overdue" if not already set.
4. If final payment is overdue, do **not** release final unwatermarked deliverables — hold in `Waiting_On_Client` in the relevant `04_Client_Delivery` folder.
5. Once paid, move the invoice copy out of `Overdue/`, update status to "Paid" in the Payment Tracker, and issue a receipt from `03_Payments/Receipts/`.

*Placeholders: `{{CLIENT_NAME}}`, `{{BUSINESS_NAME}}`, `{{INVOICE_ID}}`, `{{AMOUNT}}`, `{{PROJECT_TYPE}}`, `{{VENTURE}}`, `{{DUE_DATE}}`, `{{PAYMENT_LINK_PLACEHOLDER}}`, `{{YOUR_NAME}}`, `{{YOUR_COMPANY}}`.*
