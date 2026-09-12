# Cashflow Ventures — Operations System

A lightweight, Excel + Markdown + folders operating system for two productized service ventures run from one place:

1. **Web Development** — standardized websites for local service businesses
2. **Cinematic Videos** — AI-generated cinematic property/location films for realtors, developers, rental businesses, educational institutions, golf courses, and country clubs

There is **one master CRM, one master activity tracker, one payment tracker, and one combined dashboard system** for both ventures — no duplicate lead databases, no macros, no custom app.

---

## 1. How the unified system works

Everything traces back to **one authoritative source of truth**:

> **`01_Master_CRM/Cashflow_Ventures_Master_CRM.xlsx`** is the single database of every lead, client, and activity for both ventures.

Every record in it carries a **Venture** field (`Web Development` or `Cinematic Videos`), so the two businesses share one pipeline instead of two separate systems. Everything else in this folder structure — dashboards, proposals, payments, delivery folders — is either:

- **generated from** the Master CRM (dashboards, via formulas), or
- **keyed back to** the Master CRM (proposals, invoices, delivery folders, via Lead ID / Client ID), or
- **a satellite ledger** with its own narrow purpose (the Payment Tracker records money; it is not a second lead database).

```
Master CRM (leads + activities)  ──────────────► Master Pipeline Dashboard
        │                                          Web Development Dashboard
        │  Lead ID / Client ID                     Cinematic Videos Dashboard
        ▼
Proposals (02) ──► Client Delivery (04) ──► Payment Tracker (03) ──► Weekly Dashboard (00)
```

The **Payment Tracker** and **Weekly Dashboard** are separate workbooks (payments and weekly operating cadence are naturally distinct concerns from the lead database). To keep every workbook simple, robust, and free of fragile cross-file links, a small number of **"Cash Collected" cells are manually synced weekly** from the Payment Tracker's Totals Summary tab into the CRM dashboards and Weekly Dashboard — these are the only manual-sync cells in the system and are always shaded **yellow**. Every other number recalculates automatically.

## 2. How to switch between ventures using filters and dashboard tabs

You never need two systems. Instead:

- **Master Leads / Activities tabs (Master CRM):** filter the `Venture` column using the built-in AutoFilter dropdown to see one venture, or leave unfiltered to see both.
- **Master Pipeline Dashboard tab:** set the yellow **Venture Filter** cell (`All` / `Web Development` / `Cinematic Videos`) — every KPI card updates instantly. The **Venture Breakdown** table below it always shows all three columns (Web Development, Cinematic Videos, Combined) side by side regardless of the filter.
- **Web Development Dashboard** and **Cinematic Videos Dashboard tabs:** permanently locked to their venture — open the one you want to check.
- **Weekly Dashboard workbook:** same pattern — a `Combined` tab with a venture filter, plus dedicated `Web Development` and `Cinematic Videos` tabs.
- **Weekly_Log tab:** a proper Excel Table — click any column header's filter arrow to slice by Venture, Week, Geography, Vertical, Pipeline Stage Focus, or Lead Tier Focus.

## 3. How to add and qualify a lead

1. Open `01_Master_CRM/Cashflow_Ventures_Master_CRM.xlsx` → **Master Leads** tab.
2. Add a new row with the next sequential **Lead ID** (`LEAD-003`, `LEAD-004`, …). IDs are unique across both ventures — never reuse a number.
3. Fill in **Venture** (dropdown), Business Name, contact details, Lead Source, and the **Current Website or Marketing Problem**.
4. Set **Pipeline Stage** to `Identified` and **Lead Tier** (A/B/C — how good a fit/priority this lead is).
5. **Probability** and **Weighted Pipeline** calculate automatically from Pipeline Stage — do not type into those columns.
6. As you make contact, update **First Outreach Date**, move **Pipeline Stage** forward (`Contacted` → `Follow-Up` → `Replied` → `Qualified` …), and set **Next Action** + **Next Action Date** so nothing goes cold.

A lead is "qualified" once you've confirmed: a real problem you can solve, a real decision-maker, and a realistic budget/timeline — at that point move Pipeline Stage to `Qualified`.

## 4. How activities are logged

Open the **Activities** tab and add a row each time you make contact:

- **Lead ID** — pick from the dropdown (validated against Master Leads).
- **Venture** and **Business Name** fill in automatically from the Lead ID — never type these manually.
- Set **Activity Type**, write a one-line **Notes**, record the **Outcome**, and set **Next Action** + **Next Action Date**.

This is the system's call/email/message log — it feeds the "Outreach," "Follow-ups sent," and reply-rate metrics on the dashboards.

## 5. How leads move through the pipeline

```
Identified → Contacted → Follow-Up → Replied → Qualified → Preview Sent →
Call Booked → Proposal Sent → Verbal Yes → Deposit Invoiced → Deposit Paid → Won
                                                                        ↘ Lost / Nurture
```

Update **Pipeline Stage** every time a lead moves — this single field drives probability, weighted pipeline, and every funnel metric on all three dashboards. `Lost` and `Nurture` are exit states: use `Lost` when the deal is dead (fill in **Lost Reason**), and `Nurture` for leads that are a fit but not ready now.

## 6. When to create a preview

Create a preview (Website Homepage / Website Audit / Cinematic Property Film / Cinematic Location Film / Before-and-After Concept) once a lead is at least `Qualified` and shows real interest. Set **Preview Type** and move **Preview Status** forward: `To Create` → `In Progress` → `Ready` → `Sent` → `Viewed` → `Feedback Received`. A strong, low-cost preview is what earns the right to send a paid proposal — don't skip straight to a proposal on a cold lead.

## 7. When to create a proposal

Once a preview has landed well (or for a warm/referred lead that doesn't need one) and the lead is ready to discuss price, create a proposal:

1. Use the relevant checklist first: `02_Proposals/Web_Development/Templates/Proposal_Checklist.md` or `02_Proposals/Cinematic_Videos/Templates/Proposal_Checklist.md`.
2. Copy the matching template (`Website_Proposal_Template.md` or `Cinematic_Video_Proposal_Template.md`) into that venture's `Drafts/` folder.
3. Fill in every `{{PLACEHOLDER}}`, then move the file to `Sent/`.
4. Update Master CRM: Pipeline Stage → `Proposal Sent`, log an Activity.
5. Move the file to `Accepted/` or `Rejected/` once you hear back, and update Pipeline Stage accordingly.

## 8. When to create a client-delivery folder

As soon as a deal is verbally agreed (Pipeline Stage → `Verbal Yes` or later) and you're issuing the deposit invoice:

1. Copy the relevant `Client_Template/` folder from `04_Client_Delivery/Web_Development/` or `04_Client_Delivery/Cinematic_Videos/`.
2. Rename it `CLIENT-00X_Business-Name` (Client IDs are unique across both ventures — never reuse a number, and they don't have to match the Lead ID number).
3. Place it in that venture's `Active/` folder.
4. Fill in `00_Client_Record.md` with the Lead ID, Client ID, and commercials.

Move the folder to `Waiting_On_Client/` whenever you're blocked on the client, to `Completed/` at handover, and to `Archived/` after some time has passed (or for any lost/cancelled project you want to keep a record of).

## 9. When each delivery clock begins

**Web Development — the 7-business-day clock starts only once all four are true** (tracked in `00_Client_Record.md` and the `Seven_Day_Correction_Log.md`):
1. Deposit received
2. Intake form complete
3. Required content received
4. Required account access received

**Cinematic Videos** has no fixed day-count promise, but follows the same "don't start the clock on incomplete inputs" principle: production begins once required source assets (photos/video, property information, brand assets) are received — track this in `02_Source_Assets/Asset_Request_Checklist.md`.

## 10. How to record deposits and final payments

All money lives in `03_Payments/Cashflow_Ventures_Payment_Tracker.xlsx` → **Payments** tab:

1. Add a row keyed by **Client ID** and **Lead ID**, with **Venture** and **Project Type**.
2. Enter **Project Price** and **Deposit Percentage** — **Deposit Amount** and **Final Payment Amount** calculate automatically.
3. When you invoice the deposit: set **Deposit Invoice Date**, **Deposit Due Date**, and **Deposit Status → Invoiced**. Use `03_Payments/Invoices/Invoice_Template.md`.
4. When it's paid: **Deposit Status → Paid** and set **Deposit Paid Date**. Use `03_Payments/Receipts/Receipt_Template.md`.
5. Repeat the same pattern for the final payment. **Never release final unwatermarked video files or launch a website before Final Payment Status = Paid**, unless explicitly agreed otherwise.
6. If a payment is late, set status to **Overdue** (turns red) and use `03_Payments/Overdue/Overdue_Reminder_Template.md`.
7. **Total Invoiced**, **Total Collected**, and **Outstanding Balance** calculate automatically. Conditional formatting colors every status cell: green = Paid, amber = Invoiced, red = Overdue, grey = Not Invoiced.
8. Check the **Totals Summary** tab weekly and copy its "Combined Total Collected" figure into the yellow **Cash collected** cells on the Master Pipeline Dashboard, Web/Cinematic venture dashboards, and Weekly Dashboard — this is the one manual sync step in the whole system.

## 11. How to archive completed and lost opportunities

- **Won and delivered:** move the client delivery folder to `Completed/`, keep the proposal in `Accepted/`, keep payment rows in the Payment Tracker (they remain the permanent financial record).
- **Lost:** set Pipeline Stage → `Lost` with a **Lost Reason** in Master CRM, move the proposal (if any) to `Rejected/`. Leave the lead row in Master Leads — don't delete history.
- **Old completed projects:** periodically move folders from `Completed/` to `Archived/` under each venture's `04_Client_Delivery/` to keep the active view clean.

## 12. Which files to open every day

1. **`01_Master_CRM/Cashflow_Ventures_Master_CRM.xlsx`** → Master Pipeline Dashboard tab (check overdue follow-ups highlighted in red on Master Leads / Activities), then Master Leads to work your Next Action Date list.
2. **`03_Payments/Cashflow_Ventures_Payment_Tracker.xlsx`** → scan for anything Overdue (red).
3. Whichever venture's `04_Client_Delivery/Active/` folders have work due today.

## 13. Recommended daily workflow

1. Open Master CRM → sort/filter Master Leads by **Follow-Up Date** and **Next Action Date** ≤ today (highlighted red).
2. Work through overdue items: make contact, log it in **Activities**, update Pipeline Stage, set the next Next Action Date.
3. Check Payment Tracker for anything due today or Overdue; send reminders as needed.
4. Check `Active/` client delivery folders for anything due today (revision rounds, previews, launches).
5. Add any new leads that came in.

## 14. Recommended weekly workflow

1. Open `00_Dashboard/Cashflow_Ventures_Weekly_Dashboard.xlsx` → add a new row to **Weekly_Log** for each venture (or update the current week's row) with the week's counts.
2. Review the **Combined**, **Web Development**, and **Cinematic Videos** tabs for progress against monthly targets.
3. Open the Payment Tracker's **Totals Summary** tab and copy the "Combined Total Collected" figures into the yellow Cash Collected cells across the CRM and Weekly dashboards.
4. Review Master Pipeline Dashboard's Venture Breakdown table — is either venture under-pacing?
5. Move any folders in `04_Client_Delivery` that are done to `Completed/`, and any stale ones to `Archived/`.
6. Skim Master Leads for stale `Nurture` or `Follow-Up` leads worth re-engaging.

---

## Naming conventions

| Type | Format | Example |
|---|---|---|
| Lead | `LEAD-XXX` | `LEAD-001` |
| Client | `CLIENT-XXX` | `CLIENT-001` |
| Proposal | `PROP-XXX_Venture_Business-Name_YYYY-MM-DD` | `PROP-001_Web-Development_Riverside-Dental_2026-09-26` |
| Invoice | `INV-XXX_Venture_Business-Name_Deposit` | `INV-001_Web-Development_Riverside-Dental_Deposit` |
| Project folder | `CLIENT-XXX_Business-Name` | `CLIENT-001_Riverside-Dental` |

**Lead IDs and Client IDs are each a single unique sequence shared across both ventures** — never restart numbering per venture, and never reuse a number.

## Folder map

```
Cashflow-Ventures-Operations/
├── 00_Dashboard/            Weekly operating dashboard (Combined / Web Dev / Cinematic tabs)
├── 01_Master_CRM/           THE single source of truth: leads, activities, all dashboards
├── 02_Proposals/            Venture-specific proposal templates + Drafts/Sent/Accepted/Rejected
├── 03_Payments/             Payment Tracker + Invoice/Receipt/Overdue templates
├── 04_Client_Delivery/      Venture-specific client delivery templates + Active/Waiting/Completed/Archived
├── 05_Assets/               Brand, website templates, video templates, contracts, outreach templates
└── README.md                This file
```

## What's included as working examples

Both the Master CRM (`LEAD-001` / `LEAD-002`) and the Payment Tracker (`CLIENT-001` / `CLIENT-002`) and the Weekly Dashboard's `Weekly_Log` contain **one clearly labelled fictional example per venture** ("Example: Riverside Family Dental" for Web Development, "Example: Bluestone Realty Group" for Cinematic Videos). They're marked "Fictional example row — safe to delete" in the Notes column — delete them once you've added your first real leads, or keep them as a reference for the expected format.
