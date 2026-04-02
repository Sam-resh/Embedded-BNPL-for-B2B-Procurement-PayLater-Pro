# User Stories
## PayLater Pro — B2B Embedded BNPL

**Document version:** 1.0  
**Sprint scope:** MVP (v1.0) — Phases 1 & 2  
**Format:** As a [persona], I want to [action], so that [outcome]  
**Priority:** P0 (must-have launch) / P1 (launch + 60 days) / P2 (roadmap)  

---

## Personas Quick Reference

| ID | Persona | Role | Primary Goal |
|---|---|---|---|
| BYR | Buyer | Finance Controller / Procurement Manager | Access payment flexibility at checkout without paperwork |
| SUP | Supplier | CFO / AR Manager | Get paid immediately; offer terms to win more buyers |
| ADM | Finance Admin | Treasury / AP Manager | Manage company-wide BNPL exposure and approvals |
| PLT | Platform Admin | SAP Ariba / Zoho system admin | Configure and manage the BNPL widget for their organization |
| OPS | Internal Ops | PayLater Pro credit/ops team | Manage credit decisions, disputes, and collections |

---

## Epic 1: Business Onboarding & KYB

### US-001 — GSTIN Verification (P0)
**As a** Buyer (BYR),  
**I want to** verify my business identity by entering my GSTIN,  
**So that** I can access a credit limit without uploading any physical documents.

**Acceptance Criteria:**
- [ ] User enters GSTIN; system validates format (15-character alphanumeric) before API call
- [ ] GSTN API returns business name, registration address, and filing status within 30 seconds
- [ ] If GSTIN is active and has ≥4 quarters of filing history, user proceeds to bank verification step
- [ ] If GSTIN is inactive or <2 quarters old, user sees clear rejection reason and eligibility criteria
- [ ] All verified data is pre-filled; user cannot manually override GSTN-sourced fields

**Test cases:**
- Valid GSTIN → proceeds to bank step ✓
- Invalid format GSTIN → inline validation error before API call ✓
- GSTIN with 1 quarter history → rejected with reason shown ✓
- GSTIN API timeout (>30s) → fallback to manual document upload ✓

---

### US-002 — Bank Account Verification via AA Framework (P0)
**As a** Buyer (BYR),  
**I want to** connect my business bank account using the Account Aggregator framework,  
**So that** my credit limit is set instantly without sharing login credentials.

**Acceptance Criteria:**
- [ ] System presents AA consent screen with clear explanation of what data is accessed
- [ ] User selects their bank from a list of AA-supported banks (minimum 15 banks at launch)
- [ ] Consent is OTP-authenticated via the user's registered mobile number
- [ ] Bank data (last 12 months of transactions) is fetched within 60 seconds of consent
- [ ] If AA consent is declined, fallback to PDF bank statement upload (6-month minimum)
- [ ] User can revoke AA consent at any time from account settings

---

### US-003 — Instant Credit Limit Assignment (P0)
**As a** Buyer (BYR),  
**I want to** receive my approved credit limit immediately after completing KYB,  
**So that** I can start placing orders the same day I sign up.

**Acceptance Criteria:**
- [ ] Credit decision is returned within 60 seconds of KYB completion in ≥90% of cases
- [ ] Decision screen shows: approved limit, available payment plans, and effective APR for each plan
- [ ] "Conditionally Approved" cases (lower limit) show the limit + reason it is lower than requested
- [ ] Declined applications show: reason for decline (in plain language, not risk codes), reapplication eligibility date, alternative suggestions (e.g., "Apply again after 2 GST filings")
- [ ] Approved limit is immediately available in the buyer's dashboard

---

### US-004 — KYB Completion for Supplier (P0)
**As a** Supplier (SUP),  
**I want to** onboard my business to receive same-day settlements,  
**So that** I can offer PayLater Pro to my buyers without carrying credit risk myself.

**Acceptance Criteria:**
- [ ] Supplier onboarding requires: GSTIN, bank account (IFSC + account number), and KYC of authorized signatory (Aadhaar or PAN)
- [ ] Bank account is verified via penny drop within 5 minutes
- [ ] Supplier dashboard is activated immediately upon verified onboarding
- [ ] Supplier sees: payment terms they offer, settlement schedule, and active buyer list
- [ ] Supplier can set a maximum BNPL-eligible order value per buyer

---

## Epic 2: Checkout & Payment Plan Selection

### US-005 — BNPL Widget at Procurement Checkout (P0)
**As a** Buyer (BYR),  
**I want to** see PayLater Pro as a payment option when I reach the payment step in SAP Ariba,  
**So that** I can choose to pay later without leaving the procurement platform.

**Acceptance Criteria:**
- [ ] PayLater Pro widget appears as a payment method alongside existing options (bank transfer, credit card)
- [ ] Widget loads within 1.2 seconds on a 4G connection
- [ ] Widget shows: available credit limit, utilization after this order, 3 plan options with fees
- [ ] All fees are shown before the buyer commits — no hidden charges revealed post-selection
- [ ] If order exceeds available limit, widget shows maximum eligible BNPL amount and offers partial financing

---

### US-006 — Payment Plan Selection (P0)
**As a** Buyer (BYR),  
**I want to** choose between Net-30, Pay-in-3, and Pay-in-6 payment plans,  
**So that** I can align my payments with my business's cash flow cycle.

**Acceptance Criteria:**
- [ ] Three plans displayed: Net-30 (free), Pay-in-3 (fee disclosed), Pay-in-6 (fee disclosed)
- [ ] Each plan shows: total cost to buyer, payment dates, fee in absolute rupee terms
- [ ] Effective APR shown for each plan (RBI digital lending compliance)
- [ ] User can toggle between plans; summary updates in real time
- [ ] Selecting a plan requires one confirmation tap — no additional form fields

---

### US-007 — Down Payment Option (P1)
**As a** Buyer (BYR),  
**I want to** pay a portion of the invoice upfront and finance the remainder,  
**So that** I can access BNPL even when the order value exceeds my full credit limit.

**Acceptance Criteria:**
- [ ] If order > available credit limit, partial BNPL is automatically offered
- [ ] User sets down payment amount using a slider (min: 20% of order value)
- [ ] System recalculates BNPL amount and payment schedule in real time as slider moves
- [ ] Down payment is charged immediately; BNPL portion follows selected plan schedule
- [ ] Payment confirmation screen clearly separates down payment vs. financed amount

---

### US-008 — Multi-Approver Workflow (P0)
**As a** Finance Admin (ADM),  
**I want to** approve large BNPL orders before they are finalized,  
**So that** the company's credit utilization stays within board-approved limits.

**Acceptance Criteria:**
- [ ] Threshold for second approval is configurable by Company Admin (default: ₹10L)
- [ ] Approval request is sent via email AND WhatsApp within 60 seconds of buyer submission
- [ ] Approval message contains: order summary, supplier name, BNPL plan, and total cost
- [ ] Approver can approve or reject with one tap (no login required for approval action)
- [ ] Approved orders lock supplier payment within 15 minutes; rejected orders notify buyer with reason
- [ ] If approver does not respond in 48 hours, order auto-escalates to the next approver in the hierarchy
- [ ] All approval actions logged with timestamp, user ID, and action taken

---

## Epic 3: Supplier Settlement

### US-009 — Same-Day Settlement Confirmation (P0)
**As a** Supplier (SUP),  
**I want to** receive immediate confirmation when a buyer selects PayLater Pro,  
**So that** I know the invoice will be paid and can dispatch the goods with confidence.

**Acceptance Criteria:**
- [ ] Supplier receives WhatsApp + email notification within 5 minutes of buyer order confirmation
- [ ] Notification contains: buyer name, order amount, PO number, expected settlement date
- [ ] Settlement confirmation is binding — PayLater Pro guarantees payment regardless of buyer behavior
- [ ] If a buyer defaults, supplier is NOT notified of the default — PayLater Pro handles collections independently

---

### US-010 — T+1 Fund Transfer (P0)
**As a** Supplier (SUP),  
**I want to** receive funds in my bank account by the next business day,  
**So that** I can use the capital to fulfill more orders immediately.

**Acceptance Criteria:**
- [ ] NEFT/IMPS transfer is initiated by 6pm on the day the buyer order is confirmed
- [ ] Settlement reflects in supplier's bank account by 11am the following business day
- [ ] Supplier dashboard shows: initiated, in-transit, and settled status for each payment
- [ ] Settlement amount = invoice amount minus MDR (clearly itemized in dashboard)
- [ ] If settlement fails (invalid bank details), supplier is notified within 1 hour and re-attempt is automatic

---

### US-011 — Supplier Reconciliation Report (P1)
**As a** Supplier (SUP),  
**I want to** download a GST-compatible reconciliation report,  
**So that** my finance team can match payments to invoices without manual data entry.

**Acceptance Criteria:**
- [ ] Weekly and monthly reports available for download in CSV and PDF
- [ ] Report contains: invoice number, buyer name, invoice date, gross amount, MDR deducted, net settled amount, settlement date
- [ ] Report format is compatible with Tally ERP import (column headers match Tally's import template)
- [ ] Reports are auto-emailed to registered supplier email on the 1st of each month
- [ ] Historical reports available for up to 24 months

---

## Epic 4: Buyer Dashboard & Notifications

### US-012 — Credit Utilization Dashboard (P0)
**As a** Finance Admin (ADM),  
**I want to** see my company's BNPL credit utilization in real time,  
**So that** I can make informed procurement decisions and avoid hitting the credit limit unexpectedly.

**Acceptance Criteria:**
- [ ] Dashboard shows: total credit limit, utilized amount, available credit, as a visual meter
- [ ] All active BNPL installments shown with: supplier, order date, amount, due dates, status
- [ ] Clicking any installment shows full order and payment plan details
- [ ] "Team view" shows which employee placed each order (for Finance Controller)
- [ ] Dashboard data refreshes every 15 minutes; manual refresh button available

---

### US-013 — Payment Due Reminders (P0)
**As a** Buyer (BYR),  
**I want to** receive reminders before each installment is due,  
**So that** I never miss a payment and damage my credit score.

**Acceptance Criteria:**
- [ ] Reminder sent at D-7, D-3, and D-0 (due date) for each installment
- [ ] Channel: WhatsApp (primary) + email (secondary) + in-app notification (if app installed)
- [ ] Reminder contains: amount due, due date, payment link, and helpline contact
- [ ] D-0 reminder sent at 9am; includes option to request a 3-day grace period (one time per quarter)
- [ ] User can configure preferred reminder channels in account settings

---

### US-014 — Payment Schedule Export (P1)
**As a** Finance Admin (ADM),  
**I want to** export my company's full payment schedule to Excel,  
**So that** I can incorporate BNPL liabilities into our monthly cash flow forecast.

**Acceptance Criteria:**
- [ ] Export covers: all active installments, due dates, amounts, and supplier names
- [ ] Available as CSV download from the dashboard in one click
- [ ] Optional: auto-schedule monthly email delivery of the schedule
- [ ] Export is available in INR only for MVP; multi-currency in v2.0

---

## Epic 5: Collections & Delinquency Management (Internal — Ops)

### US-015 — Automated Late Payment Handling (P0)
**As an** Internal Ops agent (OPS),  
**I want to** automatically trigger late payment sequences without manual intervention,  
**So that** we maintain low credit losses while preserving buyer relationships.

**Acceptance Criteria:**
- [ ] D+1 (1 day past due): automated WhatsApp + email with payment link; late fee disclosed
- [ ] D+7: second attempt + offer of restructured payment plan (split overdue into 2 payments)
- [ ] D+14: escalation to collections team; account flagged; new BNPL purchases frozen
- [ ] D+30: formal legal notice initiated; bureau reporting triggered
- [ ] All communications are logged; Ops team can view full contact history per account
- [ ] Ops team can manually pause the automated sequence for any account

---

### US-016 — Credit Limit Review Request (P2)
**As a** Buyer (BYR),  
**I want to** request a credit limit increase after 3 months of successful repayments,  
**So that** I can finance larger orders as my business grows.

**Acceptance Criteria:**
- [ ] "Request limit increase" button appears after 3 months of on-time repayments
- [ ] System triggers a re-scoring using latest AA data (with fresh consent)
- [ ] Decision returned within 60 seconds; new limit effective immediately if approved
- [ ] If denied, reason shown and eligibility for next review communicated
- [ ] Limit increase request can be made once per quarter maximum

---

## Story Map Summary

| Epic | P0 Stories | P1 Stories | P2 Stories |
|---|---|---|---|
| 1. Onboarding & KYB | US-001, US-002, US-003, US-004 | — | — |
| 2. Checkout & Plans | US-005, US-006, US-008 | US-007 | — |
| 3. Supplier Settlement | US-009, US-010 | US-011 | — |
| 4. Dashboard & Notifications | US-012, US-013 | US-014 | — |
| 5. Collections | US-015 | — | US-016 |
| **Total** | **12** | **3** | **1** |

---

## Definition of Done (DoD)

A user story is **Done** when:
- [ ] All acceptance criteria pass in QA
- [ ] API contract reviewed and signed off by Engineering Lead
- [ ] Edge cases (timeout, error states, empty states) implemented and tested
- [ ] Accessibility: all interactive elements keyboard-navigable and screen-reader labeled
- [ ] Load tested at 5× expected traffic
- [ ] Security review complete (no PII logged in cleartext; no sensitive data in URLs)
- [ ] Product Manager sign-off after demo walkthrough
- [ ] Release notes drafted for stakeholder communication

---

*Stories maintained in: Linear / Jira (B2B-BNPL project)*  
*Story point estimation: Planning Poker with engineering team*  
*Sprint cycle: 2-week sprints; backlog grooming every Thursday*
