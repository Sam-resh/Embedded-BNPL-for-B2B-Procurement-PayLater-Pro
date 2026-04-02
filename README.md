# 💳 PayLater Pro — B2B Embedded BNPL for Procurement
### Product Management Portfolio Project

> **Embedded Buy Now, Pay Later for B2B procurement workflows** — integrating directly into SAP Ariba, Zoho Books, and Tally to offer business buyers flexible installment payments, while suppliers receive T+1 settlement.

---

## 📁 Repository Structure

```
b2b-bnpl-project/
│
├── PRD.md                    # Product Requirements Document (v1.0)
├── Business_Case.md          # Full business case with P&L and unit economics
├── Market_Analysis.md        # TAM/SAM/SOM, segmentation, regulatory landscape
├── Competitor_Analysis.md    # Competitive intelligence on 7 global players
├── User_Stories.md           # 16 user stories with acceptance criteria
├── Notion_Dashboard.html     # Interactive PM dashboard (open in browser)
└── README.md                 # This file
```

---

## 🎯 Project Summary

| Attribute | Detail |
|---|---|
| **Product** | Embedded B2B BNPL at procurement checkout |
| **Target companies** | Mastercard, Goldman Sachs, Stripe, Razorpay |
| **Market** | India (launch) → SE Asia (Year 3) |
| **TAM** | $530B India SMB working capital gap |
| **SAM** | $8.2B mid-market digital procurement (India) |
| **Year 1 TPV target** | $50M |
| **Blended take rate** | 2.8% |
| **Break-even** | Month 19 |
| **5-year NPV** | $42M at 12% discount rate |

---

## 🚀 How to Use These Documents

### Viewing the Dashboard
Open `Notion_Dashboard.html` directly in any modern browser — no server required. The dashboard includes:
- 8 key product metrics
- 6 interactive charts (market growth, TAM/SAM/SOM, P&L, vertical fit, WTP, seasonality)
- Competitive feature matrix
- Live OKR progress tracker
- Risk register
- Integration partner status

### Document Reading Order (for reviewers)
1. **Start here:** `Business_Case.md` — understand the strategic opportunity
2. **Market context:** `Market_Analysis.md` — understand why now
3. **Competitive landscape:** `Competitor_Analysis.md` — understand where we win
4. **Product detail:** `PRD.md` — understand what we're building and why
5. **Engineering handoff:** `User_Stories.md` — understand how it gets built
6. **Living tracker:** `Notion_Dashboard.html` — monitor progress

---

## 🏗️ Product Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    PROCUREMENT PLATFORM                          │
│         (SAP Ariba / Zoho Books / Tally / Coupa)                │
└──────────────────────────┬──────────────────────────────────────┘
                           │ Embedded widget (JS + API)
┌──────────────────────────▼──────────────────────────────────────┐
│                    PAYLATER PRO CORE                             │
│  ┌───────────────┐  ┌───────────────┐  ┌────────────────────┐  │
│  │  KYB Engine   │  │ Credit Engine │  │  Payment Engine    │  │
│  │ GSTIN + AA    │  │ ML Scoring    │  │  Plans + Schedule  │  │
│  └───────────────┘  └───────────────┘  └────────────────────┘  │
└──────────────────────────┬──────────────────────────────────────┘
                           │
         ┌─────────────────┴────────────────────┐
         │                                      │
┌────────▼────────┐                   ┌─────────▼────────┐
│  BUYER ACCOUNT  │                   │ SUPPLIER ACCOUNT  │
│  Dashboard      │                   │  T+1 Settlement   │
│  Notifications  │                   │  Reconciliation   │
│  Approvals      │                   │  Dashboard        │
└─────────────────┘                   └──────────────────┘
```

---

## 📊 Key Financial Highlights

| Metric | Year 1 | Year 2 | Year 3 |
|---|---|---|---|
| Total Payment Volume | $50M | $180M | $480M |
| Gross Revenue | $1.4M | $5.04M | $13.44M |
| Net Credit Loss Rate | 1.2% | 1.2% | 1.2% |
| EBITDA | ($9.2M) | ($5.16M) | ($0.56M) |
| LTV : CAC | 44:1 | 44:1 | 44:1 |

---

## ⚔️ Competitive Advantage

PayLater Pro is the **only** B2B BNPL product that is:
1. **Embedded at procurement checkout** — not a separate portal
2. **India-native** — GSTIN + Account Aggregator framework scoring
3. **Multi-approver workflow** — built for enterprise finance teams
4. **T+1 supplier settlement** — suppliers get paid next day, always

Global players (Billie, Resolve, Mondu) have none of these India-specific capabilities. India-native players (CredAble, Oxyzo) are not embedded in procurement platforms.

---

## 📋 Document Standards

All documents in this repository follow enterprise PM standards:
- **PRD:** Google/Stripe-style with functional + non-functional requirements, personas, and risk register
- **Business Case:** McKinsey-style with financial modeling, sensitivity analysis, and strategic alternatives
- **User Stories:** Atlassian/Linear format with acceptance criteria and test cases
- **Market Analysis:** BCG/Redseer-referenced with primary research data

---

## 🏷️ Tags

`fintech` `b2b-payments` `bnpl` `product-management` `embedded-finance` `india-fintech` `working-capital` `procurement` `goldman-sachs` `mastercard` `pm-portfolio`

---

*This is a portfolio project demonstrating PM capabilities for senior roles at top fintech firms.*  
*All financial projections are illustrative models based on publicly available market data.*
