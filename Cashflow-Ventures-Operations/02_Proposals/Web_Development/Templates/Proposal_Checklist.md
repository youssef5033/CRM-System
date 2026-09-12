# Web Development — Proposal Checklist

Use before sending any website proposal.

## Before drafting

- [ ] Lead exists in Master CRM (`01_Master_CRM`) with a Lead ID
- [ ] Pipeline Stage is at least "Qualified" or a preview has been sent
- [ ] Preview (homepage mockup or audit) reviewed with client, or scheduled
- [ ] Confirmed decision-maker / contact who can approve and pay

## Drafting the proposal

- [ ] Copy `Website_Proposal_Template.md` into `02_Proposals/Web_Development/Drafts/`
- [ ] Rename to `PROP-{ID}_Web-Development_{Business-Name}_{YYYY-MM-DD}.md`
- [ ] Fill in every `{{PLACEHOLDER}}` — no unresolved placeholders remain
- [ ] Confirm price: Standard ($1,200) or Launch-Partner ($1,000) — conditions understood by client
- [ ] Set Expiry Date (recommend proposal date + 7–14 days)
- [ ] Set target Delivery Date (proposal acceptance + buffer + 7 business days)
- [ ] Proofread for client name, business name, and pricing accuracy

## Sending

- [ ] Move file from `Drafts/` to `Sent/`
- [ ] Update Master CRM: Pipeline Stage → "Proposal Sent"
- [ ] Log an Activity in the Activities tab (Activity Type: "Proposal Sent")
- [ ] Set Next Action + Next Action Date (e.g., "Follow up on proposal" in 3 business days)

## After response

- [ ] **If accepted:** move file to `Accepted/`, update Pipeline Stage → "Verbal Yes" or "Deposit Invoiced", create the client delivery folder in `04_Client_Delivery/Web_Development/Active/`, issue the deposit invoice from `03_Payments`
- [ ] **If rejected/no response after expiry:** move file to `Rejected/`, update Pipeline Stage → "Lost" or "Nurture", record Lost Reason in Master CRM
