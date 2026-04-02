# Product Requirements Document
## Embedded BNPL for B2B Procurement — PayLater Pro

**Document version:** 1.0  
**Status:** Draft → In Review  
**Author:** Product Management  
**Last updated:** April 2026  
**Stakeholders:** Product, Engineering, Risk, Legal, Finance, Sales  

---

## 1. Executive Summary

B2B commerce runs on credit — but the infrastructure powering it is broken. Net-30/60/90 payment terms are manually negotiated, paper-heavy, and inaccessible to small and mid-market buyers. Suppliers bleed cash waiting for payment. Buyers lose purchasing power due to lack of flexible financing.

**PayLater Pro** is an embedded Buy Now, Pay Later product for B2B procurement. It integrates directly into procurement platforms (SAP Ariba, Coupa, Zoho Books, Tally) to offer business buyers flexible installment payment options at checkout — while suppliers receive immediate settlement. The product sits inside the existing procurement workflow, requiring no behavior change.

**Strategic fit:** This product directly expands Mastercard's commercial card network, Goldman Sachs's Marcus B2B lending portfolio, or Stripe's revenue share from business payments. It targets the $50B+ B2B BNPL TAM projected by 2028.

---

## 2. Problem Statement

### 2.1 The Cash Flow Gap

| Stakeholder | Pain Point | Magnitude |
|---|---|---|
| SMB Buyers | Can't afford large orders upfront; lose supplier discounts | $2.1T in unmet working capital demand (IFC) |
| Suppliers | Wait 60–90 days to receive payment; fund buyer credit themselves | 82% of supplier defaults tied to delayed receivables |
| Finance Teams | Manual PO → invoice → approval → payment cycle | Avg. 14-day processing cycle per invoice |
| CFOs | No visibility into company-wide BNPL exposure | 67% of CFOs cite cash flow as top operational risk |

### 2.2 Why Existing Solutions Fail

- **Business credit cards** — require personal guarantees, low limits, not embedded in workflow
- **Invoice factoring** — high cost (3–8% fees), requires supplier to initiate, slow onboarding
- **Trade credit** — manually negotiated, inconsistent, no analytics layer
- **Consumer BNPL (Klarna, Affirm)** — built for individuals, no multi-approver logic, no ERP integration

---

## 3. Goals & Success Metrics

### 3.1 Product Goals

1. Enable B2B buyers to access flexible payment terms at the point of procurement
2. Ensure suppliers receive same-day or T+1 settlement regardless of buyer payment schedule
3. Create a risk-scoring engine that approves 70%+ of qualified SMB applicants in under 60 seconds
4. Achieve seamless integration with top 5 procurement platforms within 6 months of launch

### 3.2 North Star Metric

> **Total Payment Volume (TPV) financed through PayLater Pro per month**

### 3.3 OKRs — Year 1

**Objective 1: Achieve product-market fit with enterprise procurement platforms**
- KR1: Sign 3 procurement platform integration partnerships by Q2
- KR2: 500 active business accounts within 6 months of launch
- KR3: Net Promoter Score (NPS) ≥ 45 among finance decision-makers

**Objective 2: Build a scalable, low-loss credit product**
- KR1: Credit approval rate ≥ 65% for qualified applicants
- KR2: Net credit loss rate ≤ 1.2% of TPV
- KR3: Average credit decision time ≤ 45 seconds

**Objective 3: Drive revenue and unit economics**
- KR1: $50M TPV in first 12 months
- KR2: Blended take rate of 2.8% on financed GMV
- KR3: CAC payback period ≤ 9 months

---

## 4. User Personas

### Persona 1: The Finance Controller — "Priya"
- **Role:** Finance Controller at a 200-person manufacturing company
- **Goal:** Maximize working capital efficiency without increasing credit card debt
- **Frustration:** Has to call 3 suppliers to negotiate payment terms for every large order
- **Behavior:** Uses SAP Ariba for procurement; approves POs over ₹5L
- **Quote:** *"I don't want another financing product. I want payment flexibility built into the tools I already use."*

### Persona 2: The Procurement Manager — "Arjun"
- **Role:** Senior Procurement Manager at a D2C brand
- **Goal:** Place large seasonal inventory orders without straining the company's cash position
- **Frustration:** Q4 inventory buildup requires 60-day cash commitment before revenue arrives
- **Behavior:** Negotiates with 40+ suppliers; uses Zoho Books + Excel tracking
- **Quote:** *"If I could split my ₹80L order into 3 monthly payments, I'd buy 30% more stock every season."*

### Persona 3: The Supplier CFO — "Ramesh"
- **Role:** CFO at a mid-size auto-parts distributor
- **Goal:** Offer credit terms to attract more buyers without absorbing the credit risk himself
- **Frustration:** Loses deals to competitors who offer longer payment terms; his working capital is constantly tied up
- **Behavior:** Manages receivables via Tally ERP; 80 active buyer relationships
- **Quote:** *"I'd give every buyer Net-60 if someone else was willing to carry that risk."*

---

## 5. Scope

### 5.1 In Scope — MVP (v1.0)

| Feature Area | Capability |
|---|---|
| Embedded checkout | BNPL widget integrated into SAP Ariba & Zoho Books checkout |
| Credit decisioning | Real-time approval via ML scoring (GST data, bank statements, trade history) |
| Payment plans | 3 plans: Net-30, Pay in 3 (monthly), Pay in 6 (monthly) |
| Supplier settlement | T+1 ACH/NEFT settlement to supplier regardless of buyer schedule |
| Multi-approver workflow | Finance Controller + CFO dual approval for orders above ₹10L |
| Basic dashboard | Buyer credit utilization, payment schedules, upcoming dues |
| Notifications | WhatsApp + email reminders at D-7, D-3, D-0 before due dates |
| KYB onboarding | Automated KYB (Know Your Business) via GSTIN + bank account verification |

### 5.2 Out of Scope — v1.0

- Dynamic early payment discounts (planned v1.2)
- Cross-currency / international BNPL (planned v2.0)
- Insurance / trade credit protection layer (planned v1.5)
- Buyer-supplier marketplace (planned v2.0)
- Invoice discounting for suppliers (planned v1.3)

---

## 6. Functional Requirements

### 6.1 Onboarding & KYB

**FR-01:** The system shall verify business identity via GSTIN lookup within 30 seconds.  
**FR-02:** The system shall pull bank statement data via Account Aggregator (AA) framework or Perfios integration.  
**FR-03:** The system shall assign an initial credit limit within 60 seconds of KYB completion.  
**FR-04:** The system shall support re-verification triggers when credit limit increase is requested.  
**FR-05:** Onboarding shall require no more than 5 data input fields from the user.

### 6.2 Credit Decisioning Engine

**FR-06:** The scoring model shall use a minimum of 12 financial signals including GST filing regularity, bank balance trends, payment history, and industry classification.  
**FR-07:** The system shall support three decision outcomes: Approved, Conditionally Approved (lower limit), Declined.  
**FR-08:** Declined applicants shall receive a plain-language reason for decline and a re-application eligibility date.  
**FR-09:** Credit limits shall be dynamically reassessed every 90 days.  
**FR-10:** The system shall flag and escalate applications from high-risk industry categories (real estate, crypto, commodities) to a human underwriter.

### 6.3 Payment Plans & Checkout

**FR-11:** At checkout, the buyer shall see 3 plan options with full fee disclosure before selecting.  
**FR-12:** The system shall display the effective APR for each plan per RBI digital lending guidelines.  
**FR-13:** Buyer acceptance of a BNPL plan shall constitute a binding digital agreement compliant with IT Act 2000.  
**FR-14:** The checkout widget shall load within 1.2 seconds on a 4G connection.  
**FR-15:** The system shall support partial BNPL — buyer pays a down payment and finances the remainder.

### 6.4 Supplier Settlement

**FR-16:** Suppliers shall receive settlement confirmation within 15 minutes of buyer approval.  
**FR-17:** Actual fund transfer to supplier shall complete by T+1 (next business day).  
**FR-18:** Suppliers shall receive itemized settlement reports per PO for reconciliation.  
**FR-19:** The system shall support NEFT, IMPS, and UPI settlement methods.

### 6.5 Multi-Approver Workflow

**FR-20:** Orders above a configurable threshold (default ₹10L) shall require a second approver before BNPL is activated.  
**FR-21:** Approval requests shall be sent via email and WhatsApp with a one-tap approve/reject action.  
**FR-22:** Approval timeout (48 hours) shall auto-escalate to the CFO.  
**FR-23:** All approval actions shall be logged with timestamp and user ID for audit.

### 6.6 Dashboard & Analytics

**FR-24:** Buyer dashboard shall show: available credit, utilized credit, payment schedule, transaction history.  
**FR-25:** Finance Controller shall be able to export payment schedule to CSV/Excel.  
**FR-26:** System shall send automated monthly statements to the registered company email.  
**FR-27:** Supplier dashboard shall show: settled invoices, upcoming payouts, buyer activity.

---

## 7. Non-Functional Requirements

| Category | Requirement |
|---|---|
| **Availability** | 99.95% uptime SLA; planned maintenance only in 2am–4am window |
| **Latency** | Credit decision API p95 ≤ 800ms; checkout widget render ≤ 1.2s |
| **Security** | AES-256 encryption at rest; TLS 1.3 in transit; SOC 2 Type II compliance |
| **Scalability** | System shall handle 10,000 concurrent credit decisions without degradation |
| **Data residency** | All Indian customer data stored on servers within India (RBI data localization) |
| **Audit** | Immutable audit log for all credit decisions, approvals, and settlements |
| **Accessibility** | Dashboard WCAG 2.1 AA compliant |

---

## 8. Integration Requirements

| Platform | Integration Type | Priority | Timeline |
|---|---|---|---|
| SAP Ariba | Embedded iframe + webhook API | P0 | Month 3 |
| Zoho Books | Native plugin (Zoho Marketplace) | P0 | Month 4 |
| Tally Prime | Desktop plugin via Tally API | P1 | Month 6 |
| Coupa | Supplier portal widget | P1 | Month 7 |
| Razorpay | Payment gateway for collections | P0 | Month 2 |
| Account Aggregator (Finvu/Onemoney) | Bank data fetch for scoring | P0 | Month 2 |
| GSTIN API (NIC/Sandbox) | KYB identity verification | P0 | Month 1 |

---

## 9. Risk Register

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| High credit losses in first cohort | Medium | High | Conservative initial limits; strict industry filters; personal guarantee for orders >₹25L |
| Platform partner integration delays | High | Medium | Start with API-first headless integration; platform plugins in parallel |
| RBI regulatory change (digital lending norms) | Medium | High | Legal team engaged pre-launch; build compliance module as separate service |
| Slow KYB adoption by traditional SMBs | High | Medium | Offer WhatsApp-assisted KYB for low-tech users |
| Fraud via synthetic business identities | Medium | High | Bureau checks (Experian/CIBIL) + physical GSTIN validation |

---

## 10. Launch Plan

### Phase 1 — Closed Beta (Months 1–4)
- 3 integration partners onboarded in sandbox
- 50 buyer businesses in closed beta
- Manual underwriting backstop for all credit decisions
- Objective: Validate credit model accuracy and checkout conversion

### Phase 2 — Limited Launch (Months 5–7)
- SAP Ariba + Zoho Books live in production
- 200 buyer businesses; automated underwriting for <₹5L
- Supplier settlement T+1 live
- Objective: Achieve 35% checkout conversion; NPS ≥ 40

### Phase 3 — Scale (Months 8–12)
- Tally + Coupa integrations live
- Dynamic credit limit engine deployed
- 500+ active businesses; $10M monthly TPV target
- Objective: Reach sustainable unit economics; CAC payback < 9 months

---

## 11. Open Questions

1. Should we offer a supplier-facing early payment discount product at launch or defer to v1.3?
2. What is our strategy for buyers who cross-utilize BNPL limits across multiple suppliers?
3. Do we build our own collections team or white-label a collections partner for delinquent accounts?
4. Is a freemium supplier tier (no platform fee, lower limits) the right go-to-market strategy?

---

*Document owner: Head of Product, Commercial Payments*  
*Next review: 2 weeks from circulation*  
*Approval required from: CPO, CRO, General Counsel*
