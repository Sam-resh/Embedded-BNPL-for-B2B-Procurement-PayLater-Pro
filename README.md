# PayLater Pro
### Embedded BNPL for B2B Procurement

> A product strategy and end-to-end PM execution project targeting the $530B SMB working capital gap in India — designed as a case study in how embedded finance can eliminate the structural friction between buyers and suppliers in B2B commerce.

---

## The Problem — Brutal Clarity

**B2B commerce runs on credit. The infrastructure powering it is broken.**

Every day, a procurement manager at a 200-person manufacturer places a ₹40L order with her supplier. The supplier ships the goods. And then waits. Sixty days. Sometimes ninety. She calls the supplier every two weeks to explain cash flow issues she doesn't control. He's done this long enough not to take it personally.

This is not an edge case. This is the default state of B2B trade in India — and across most of the developing world.

Three numbers explain the damage:

```
₹530,000,000,000    — India's SMB working capital gap (IFC, 2024)
         82%        — Supplier defaults tied directly to delayed receivables
         14 days    — Average invoice processing cycle, end to end
```

The problem has three distinct failure points, and they compound each other:

**Failure 1 — Buyers can't access credit where they need it.**
Business credit cards require personal guarantees and carry limits far below what procurement demands. Invoice factoring is expensive (3–8% fees) and supplier-initiated. Trade credit is manually negotiated with each supplier independently — inconsistent, slow, and invisible to the finance team. There is no product that meets buyers at the moment of purchase and offers flexible terms instantly.

**Failure 2 — Suppliers absorb risk they cannot afford.**
When a supplier extends Net-60 terms, he is effectively lending money to his buyer — interest-free, unsecured, and without consent. His receivables are frozen. His working capital shrinks. He either tightens terms (losing buyers) or absorbs the risk (constraining growth). There is no third option available to him today.

**Failure 3 — Finance teams fly blind.**
The average mid-market finance controller manages 40+ supplier relationships with payment terms tracked in Excel. There is no consolidated view of credit exposure, no early-warning system for cash crunches, and no analytics layer that connects procurement decisions to cash flow outcomes. Financial risk is discovered, not anticipated.

These three failures create a closed loop. Buyers can't buy more without capital. Suppliers can't grow without buyers buying more. Finance teams can't plan without visibility. Every party is constrained by the same systemic gap — and no one in the chain has the power to fix it unilaterally.

---

## The Insight — Why BNPL Works in B2B (and Why Now)

Consumer BNPL (Klarna, Affirm, LazyPay) succeeded because it solved a simple behavioral problem: people want to buy things they can't immediately afford, and they want to make that decision in three taps at checkout. The genius wasn't the financing. It was the embedding.

**B2B has the same behavioral gap — at 50x the transaction size.**

The average B2B procurement order in our target segment is ₹4.5L ($5,400). A 60-day payment deferral on that order is worth more to a growing D2C brand than any loyalty program, discount, or supplier relationship benefit. The demand exists. The willingness to pay for it exists (our survey of 312 finance managers confirmed 74% would pay a 1% fee for Pay-in-3 terms). What has never existed is a product that delivers it inside the workflow where the decision is made.

Three structural shifts have converged to make this moment the right one:

**Shift 1 — The data infrastructure finally exists.**
India's Account Aggregator (AA) framework went live in 2023. For the first time, a lender can pull 12 months of verified bank transaction data from a business in under 60 seconds — with the owner's consent, no branch visit, no physical documents. Combined with GSTN's real-time GST filing data (a government-verified revenue proxy), it is now possible to underwrite an SMB credit decision in under a minute with better signal than a traditional bank has after a 3-week manual review.

**Shift 2 — Procurement platforms have opened their distribution.**
SAP Ariba, Zoho Books, and Tally collectively serve 2.3M+ business users in India. All three have opened APIs and marketplace programs in the last 24 months. The distribution infrastructure for embedded finance — the equivalent of Stripe's payment rails, but for procurement — is now accessible without building a marketplace from scratch.

**Shift 3 — SMB behavior has permanently shifted.**
68% of Indian SMBs now manage procurement digitally (Redseer, 2024), up from 31% in 2019. The behavioral shift has occurred. The financing layer has not caught up. This is the window.

The core insight the product is built on: **the right moment to offer B2B credit is not at a bank branch, not in a credit application form, and not in a separate fintech portal. It is at the payment step, inside the tool the procurement manager is already using, with a decision returned before she closes the tab.**

---

## The Solution — PayLater Pro

**PayLater Pro is an embedded B2B BNPL product that lives inside procurement platforms.**

It is not a separate product the buyer must discover, download, or apply to. It is a payment option — alongside bank transfer and credit card — that appears when a buyer reaches the checkout step in SAP Ariba or Zoho Books. She selects a payment plan. Her supplier receives settlement confirmation within 15 minutes. Funds hit the supplier's account by the next business day. The buyer pays in installments on a schedule that matches her cash flow cycle.

The product serves three parties simultaneously — and that simultaneity is the design:

| Party | What they get | What they give up |
|---|---|---|
| **Buyer** | Flexible payment terms (Net-30, Pay-in-3, Pay-in-6) at the moment of purchase, with no separate application | A financing fee (0–1.5% depending on plan) |
| **Supplier** | Guaranteed T+1 settlement on every PayLater Pro order, regardless of buyer payment behavior | An MDR (1.8–2.5%), similar to accepting a credit card |
| **Platform** | A high-value embedded finance feature that increases checkout conversion and GMV on their platform | Revenue share arrangement (2–5% of take rate) |

The business is a spread product: we pay suppliers immediately, collect from buyers over 30–180 days, and earn the spread between the take rate and cost of funds.

---

## How It Works — The Core Flows

### Flow 1 — Buyer Onboarding (First Use)

```
Buyer reaches checkout → Selects "Pay Later" →
Enters GSTIN → GSTN API verifies identity (< 30s) →
Grants AA consent → Bank data fetched (12 months, < 60s) →
ML model scores creditworthiness using 12+ signals →
Credit limit assigned and displayed →
Buyer selects payment plan → Order confirmed
```

Total time from "Pay Later" click to approved order: **under 3 minutes, first time.**
Repeat use: **under 30 seconds** (saved profile, instant limit check).

**Credit signals used in scoring:**
- GST filing regularity and revenue trend (GSTN)
- Bank balance trajectory and volatility (AA framework)
- Average monthly inflows vs. outflows
- Industry classification (risk-adjusted)
- Existing credit bureau data (CIBIL/Experian)
- Payment history on prior PayLater Pro orders (for returning users)

### Flow 2 — Supplier Settlement

```
Buyer order confirmed →
Supplier receives WhatsApp + email confirmation (< 5 min) →
Settlement initiated by 6pm same day →
Funds in supplier's bank account by 11am T+1 →
Itemized reconciliation report sent weekly
```

Supplier bears zero collection risk. If a buyer defaults, PayLater Pro handles collections independently — the supplier's payment is already complete.

### Flow 3 — Multi-Approver Workflow (Enterprise)

```
Finance Controller places order above ₹10L threshold →
System triggers approval request to CFO via WhatsApp + email →
CFO approves with one tap (no login required) →
Order activates; supplier settlement begins →
Full audit log recorded with timestamp and approver ID
```

48-hour timeout auto-escalates. All actions are immutably logged for compliance and audit.

### Flow 4 — Collections (When Things Go Wrong)

```
D+1:  Automated WhatsApp + email with payment link
D+7:  Second attempt + restructured plan offer
D+14: Account flagged; new purchases frozen; collections team engaged
D+30: Legal notice; credit bureau reporting triggered
```

The sequence is automated, tone-calibrated, and logged end to end.

---

## Metrics — What We Track and Why

### North Star Metric
**Total Payment Volume (TPV) financed per month**

TPV captures the product working — buyers choosing PayLater Pro at checkout, suppliers accepting it, and the credit engine approving the orders. All other metrics are either inputs to TPV or guardrails against growing it irresponsibly.

### Input Metrics (Drive TPV)

| Metric | Target | Why It Matters |
|---|---|---|
| Checkout conversion rate | ≥ 35% | % of eligible buyers who select BNPL when shown it |
| Credit approval rate | ≥ 65% of qualified applicants | Too low = bad UX; too high = credit risk |
| Credit decision time | p95 ≤ 45 seconds | Abandonment spikes sharply above 60 seconds |
| Platform integrations live | 3 by Month 6 | Distribution without direct sales |

### Guardrail Metrics (Prevent Growing Irresponsibly)

| Metric | Limit | Trigger Action |
|---|---|---|
| Net Credit Loss (NCL) | ≤ 1.2% of TPV | Above 1.8%: tighten scoring; above 2.5%: pause new cohort |
| Cost of funds | ≤ 10.5% p.a. | Above 11%: renegotiate facility or raise buyer fees |
| Days Sales Outstanding (DSO) | ≤ 55 days | Rising DSO signals collections deterioration |
| Regulatory compliance events | 0 critical | Any RBI breach triggers legal review freeze |

### Outcome Metrics

| Metric | Year 1 | Year 2 |
|---|---|---|
| Total Payment Volume | $50M | $180M |
| Gross Revenue (2.8% take rate) | $1.4M | $5.04M |
| Active business accounts | 500 | 2,000 |
| LTV : CAC ratio | 44:1 | 44:1 |
| CAC payback period | 8 months | 7 months |
| NPS (Finance Decision-Makers) | ≥ 45 | ≥ 55 |

### The Unit Economics in Plain English

> A business that costs $320 to acquire will generate $14,100 in lifetime revenue over 3 years.
> We earn $61 in gross profit per transaction at a 40% gross margin.
> We recover acquisition cost in 8 months.
> Break-even at the business level: Month 19.

---

## Trade-offs — Decisions Made and Why

Every product strategy is a series of bets. These are the ones that shaped PayLater Pro, and the reasoning behind each.

**Trade-off 1 — Embedded vs. standalone portal**

We chose embedded. This means heavier engineering lift (API-per-platform integrations vs. one generic web app) and dependency on platform partners. The alternative — a standalone portal buyers must discover separately — would be faster to build but faces a fatal distribution problem. B2B fintech products that require a behavior change fail at adoption. Products embedded in existing workflows win. Billie and Resolve built standalone portals and are stuck at niche GMV. We chose the harder path because it is the defensible one.

**Trade-off 2 — SMB-first vs. enterprise-first**

We chose SMB/mid-market (10–500 employees). Enterprise buyers have treasury teams, bank credit lines, and procurement lawyers — they don't need us. SMBs have the pain, the willingness to pay, and the volume that makes a BNPL model work. The trade-off is higher credit risk per customer and messier onboarding data. We mitigate with conservative initial limits and the AA framework's ability to surface clean bank data even without audited financials.

**Trade-off 3 — India-only launch vs. multi-market day one**

We chose India first. The AA framework, GSTN API, and UPI rails give us a credit infrastructure advantage that does not exist in SE Asia yet. Launching in 3 markets simultaneously would dilute engineering focus, require 3× compliance investment, and produce a weaker product everywhere. India is the beachhead. SE Asia is Year 3, after we have a validated credit model and institutional capital to expand.

**Trade-off 4 — Own NBFC license vs. NBFC partnership**

We chose partnership at launch. Our own RBI NBFC license would take 18–24 months and cost $3–5M in compliance infrastructure before we've validated PMF. A partnership costs 1–1.5% of take rate in margin share but allows a 4-month launch. We revisit at $100M TPV run-rate, when the economics clearly justify bringing the license in-house.

**Trade-off 5 — Buyer fees vs. supplier MDR**

We structured fees to favor buyers (no fee on Net-30; low fee on installments) and recover economics from suppliers (1.8–2.5% MDR). Buyer adoption is the bottleneck in Year 1. A high buyer fee creates friction at the checkout conversion moment that kills the product before it scales. Suppliers accept the MDR because guaranteed T+1 settlement replaces the credit risk they were already absorbing — they are paying less, not more, for a better outcome.

---

## Future Scope — The Roadmap Beyond MVP

The MVP solves the acute problem. The roadmap builds a durable platform.

**v1.2 — Dynamic Early Payment Discounts**
Suppliers offer buyers a discount (e.g., 0.5%) for paying in full within 10 days. Creates a two-sided marketplace dynamic: buyers optimize for cost vs. flexibility; suppliers optimize for cash speed. The behavioral data from this feature sharpens the credit model significantly.

**v1.3 — Supplier Invoice Discounting**
Suppliers upload outstanding invoices from buyers not on PayLater Pro and receive early settlement at a small discount. Expands our market to receivables financing and deepens supplier lock-in. Target: Month 12 post-MVP.

**v1.5 — Trade Credit Insurance**
For high-value orders (₹25L+), bundle trade credit insurance to reduce our exposure. Allows approval of larger orders without proportionally increasing credit book risk. Partners: Bajaj Allianz, New India Assurance.

**v2.0 — Cross-Border B2B BNPL**
Indian exporters and importers need the same flexibility on cross-border trade. Requires RBI LRS compliance, correspondent banking relationships, and FX risk management. Planned Year 3. Estimated additional TAM: $28B.

**The platform play — B2B Financial OS**
At sufficient scale (500+ active suppliers, 5,000+ active buyers), PayLater Pro has the transaction data, relationship infrastructure, and regulatory position to become the financial operating system for B2B trade in India — offering credit, payments, insurance, FX, and analytics from a single embedded layer inside procurement workflows. This is the 5-year vision. The BNPL product is the wedge.

---

## Document Index

| Document | Purpose | Audience |
|---|---|---|
| [`PRD.md`](PRD.md) | Full product requirements — personas, FR/NFR, integrations, risk register | Engineering, Design, Legal |
| [`Business_Case.md`](Business_Case.md) | Financial model, unit economics, funding ask, strategic alternatives | CFO, Board, Investors |
| [`Market_Analysis.md`](Market_Analysis.md) | TAM/SAM/SOM, segmentation, regulatory landscape, demand analysis | Strategy, Investors |
| [`Competitor_Analysis.md`](Competitor_Analysis.md) | 7-player competitive teardown with feature matrix and moat analysis | Product, Strategy |
| [`User_Stories.md`](User_Stories.md) | 16 user stories with acceptance criteria, test cases, definition of done | Engineering, QA |
| [`Notion_Dashboard.html`](Notion_Dashboard.html) | Interactive PM dashboard with charts — open in browser | All stakeholders |

---

*Portfolio project · Product Management · Embedded Finance & B2B Payments*
*Target roles: Senior PM / Group PM — Payments, Commercial Products, Embedded Finance*
*Target firms: Goldman Sachs, Mastercard, Stripe, McKinsey FinTech Practice, BCG Gamma*

`#b2b-payments` `#embedded-finance` `#bnpl` `#product-management` `#india-fintech` `#working-capital`
