---
title: "Prospero Credit Platform - Technical Overview"
description: "Production-grade credit risk assessment, sector-adjusted scoring, and loan recommendation engine for Nigerian SMEs and corporate entities"
date: 2024-03-01
draft: false
showToc: true
TocOpen: true
hidemeta: false
comments: false
disableHLJS: false
disableShare: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: false
UseHugoToc: true
cover:
    image: "/images/portfolio/projects/project6/logo.webp"
    alt: "Prospero Credit Platform"
    caption: "AI-powered credit platform for Nigerian SMEs"
    relative: false
    hidden: false
---

## PCL Models — Credit Risk & Recommender System

**Phase 1 | PCL (Provident Credit Limited) | Nigeria**

A production-grade credit risk assessment, sector-adjusted scoring, and loan recommendation engine for Nigerian SMEs and corporate entities.

---

## 🏗️ Architecture

```
PCL-Models/
├── src/
│   ├── types/           # Core TypeScript type definitions
│   ├── data/
│   │   ├── loaders/     # CSV data loaders (with period fix for financial statements)
│   │   └── DataStore.ts # In-memory data store with O(1) lookup indexes
│   ├── models/
│   │   ├── FinancialScorer.ts    # Financial ratios + weighted scorecard (40%)
│   │   ├── BehavioralScorer.ts   # Repayment history + bank features (35%)
│   │   ├── SectorRiskEngine.ts   # Sector risk profiles from NSE signals (25%)
│   │   └── ConfidenceScorer.ts   # Data quality & confidence assessment
│   ├── services/
│   │   ├── ScoringService.ts     # Orchestrates full scoring pipeline
│   │   ├── RecommenderService.ts # Credit recommendation with explainability
│   │   ├── PricingService.ts     # Risk-based pricing (CBN MPR + spreads)
│   │   ├── WalletService.ts      # Wallet behavioral signals
│   │   └── AuditService.ts       # Blockchain-style tamper-evident audit trail
│   ├── api/
│   │   ├── app.ts        # Express app setup
│   │   └── routes/       # REST API route handlers
│   └── index.ts          # Application entry point
├── scripts/
│   ├── fix-financial-data.ts  # Fixes period labeling in CSV
│   └── seed-data.ts           # Data validation & summary
├── tests/
│   └── scoring.test.ts   # Unit tests for scoring models
├── Pcldata/              # CSV data files (11 files)
├── docker-compose.yml
├── Dockerfile
└── package.json
```

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- npm or yarn

### 1. Install dependencies
```bash
npm install
```

### 2. Set up environment
```bash
cp .env.example .env
```

### 3. Validate data
```bash
npm run seed
```

### 4. Start development server
```bash
npm run dev
```

The API will be available at `http://localhost:3000`

### 5. With Docker
```bash
docker-compose up
```

---

## 📡 API Endpoints

### Entities

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/entities` | List entities (filter: sector, entity_type, geo_state) |
| GET | `/api/entities/:id` | Get entity with sector taxonomy |
| GET | `/api/entities/:id/financials` | 8 quarters of financial data |
| GET | `/api/entities/:id/obligations` | Current loan obligations |
| GET | `/api/entities/:id/repayment-history` | Repayment track record |
| GET | `/api/entities/stats/summary` | Aggregate entity statistics |

### Scoring

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/scoring/:entityId` | Full entity score (financial + behavioral + sector) |
| GET | `/api/scoring/:entityId/ratios` | Financial ratios only |
| POST | `/api/scoring/batch` | Batch score up to 100 entities |
| GET | `/api/scoring/leaderboard/top` | Top N entities by score |

### Recommendations

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/recommendations` | Submit credit request → get decision + pricing |
| GET | `/api/recommendations/entity/:id` | Get fresh recommendation for entity |
| GET | `/api/recommendations/entity/:id/explanation` | Detailed explainability report |
| POST | `/api/recommendations/batch` | Batch recommendations (up to 50) |

### Wallet

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/wallet/:id/signals` | Purpose compliance, spending drift, punctuality |
| GET | `/api/wallet/:id/summary` | Balance, inflows, outflows |
| GET | `/api/wallet/:id/transactions` | Transaction history with category filter |
| GET | `/api/wallet/:id/credit-context` | Stated loan purpose, collateral, guarantor |

### Sectors

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/sectors` | List all NGX sectors |
| GET | `/api/sectors/profiles/all` | All sector risk profiles (ranked by risk) |
| GET | `/api/sectors/:code/profile` | Risk profile for a specific sector |
| GET | `/api/sectors/:code/entities` | Entities in a sector |

### Audit

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/audit` | Query audit trail (filter by entity, event type, date) |
| GET | `/api/audit/chain/verify` | Verify audit chain integrity |
| GET | `/api/audit/entity/:entityId` | All decisions for an entity |
| GET | `/api/audit/:auditId` | Single record with integrity flag |

---

## 🧮 Scoring Model

### Composite Score (0–100)

| Component | Weight | Source |
|-----------|--------|--------|
| Financial Health | 40% | DSCR, leverage, liquidity, margins, YoY growth |
| Behavioral | 35% | Repayment history + bank statement features |
| Sector Risk | 25% | NSE sector signals (9 sectors, weighted signals) |

### Risk Grades

| Grade | Score | Decision |
|-------|-------|----------|
| A | 80–100 | APPROVE — Prime / 16% p.a. |
| B | 65–79 | APPROVE — Standard / 18% p.a. |
| C | 50–64 | APPROVE — Elevated / 22% p.a. |
| D | 35–49 | APPROVE_WITH_CONDITIONS — 26% p.a. |
| E | 20–34 | REFER to credit committee |
| F | 0–19 | DECLINE |

---

## 🧪 Tests

```bash
npm test                    # Run all tests
npm run test:watch          # Watch mode
```

---

## 📊 Data Files (Pcldata/)

| File | Records | Description |
|------|---------|-------------|
| `entities.csv` | ~200 | Entity profiles with sector classification |
| `financial_statements.csv` | ~1,600 | 8 quarters of P&L + balance sheet per entity |
| `obligations.csv` | ~200 | Current loan obligations |
| `repayment_history.csv` | variable | Historical payment records |
| `bank_features.csv` | ~200 | Bank statement-derived features |
| `credit_context.csv` | ~200 | Stated loan purpose and collateral |
| `sector_risk_signals.csv` | variable | NSE sector-level risk signals |
| `sector_taxonomy.csv` | 45 | 9 sectors × 5 sub-industries |
| `risk_pricing_output.csv` | ~200 | Pre-computed risk/pricing reference |
| `guarantees.csv` | variable | Guarantee data |
| `wallet_transactions.csv` | variable | Wallet transactions |

**Note on financial_statements.csv:** The raw file has duplicate period labels (all "2024"). The system automatically fixes this on load — rows 1-4 per entity → 2023-Q1..Q4, rows 5-8 → 2024-Q1..Q4.

---

## 🔒 Security & Audit

- All credit decisions are SHA-256 hashed and logged in a tamper-evident chain
- Each record links to the previous via `previousHash` + payload (blockchain-anchoring ready)
- Verify chain integrity: `GET /api/audit/chain/verify`

---

## 🏢 Project Context

**Built for PCL Phase 1 Delivery — March 2026**

This system was commissioned by Blockwave Consult for Provident Credit Limited (PCL) to provide data-driven credit assessment for Nigerian SMEs and corporate entities. The platform combines traditional financial analysis with behavioral signals and sector-specific risk profiling to deliver fair, explainable credit decisions.

### Key Features:
- **Multi-factor Scoring:** Combines financial ratios, repayment behavior, and sector risk
- **Explainable AI:** Every credit decision includes detailed reasoning
- **Risk-based Pricing:** Dynamic interest rates aligned with CBN MPR
- **Audit Trail:** Tamper-evident logging for regulatory compliance
- **Batch Processing:** Scale to hundreds of applications per day
- **Nigerian Market Focus:** Sector data from NSE, pricing aligned with CBN policies

---

## 🛠️ Technology Stack

- **Backend:** Node.js, TypeScript, Express
- **Database:** PostgreSQL (production), CSV data store (Phase 1)
- **Testing:** Jest
- **Deployment:** Docker, Docker Compose
- **APIs:** RESTful architecture
- **Security:** SHA-256 hashing, tamper-evident audit chains

---

## 📝 Project Status

**Phase 1:** ✅ Complete (March 2026)
- Core scoring models
- API endpoints
- Audit trail
- Data validation

**Future Phases:**
- Machine learning model integration
- Real-time data feeds
- Mobile application
- Blockchain integration for audit trail

---

*Note: This is a confidential project developed under NDA. Code repository and live demo are not publicly available. This documentation showcases the technical architecture and capabilities without revealing proprietary business logic.*
