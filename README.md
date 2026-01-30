# AI-Driven-Smart-Inventory-Replenishment-Stock-Out-Risk-Engine

This project demonstrates a complete end-to-end AI inventory system using Databricks Free Edition, following Medallion Architecture (Bronze → Silver → Gold), Delta Lake, MLflow, and AI-driven decision logic.

**Project Overview**

The system:

Processes real-world retail sales data (Kaggle)

Cleans and organizes data in Bronze/Silver/Gold layers

Forecasts product demand using AI

Calculates stock-out risk scores

Generates replenishment recommendations

Produces explainable AI insights for business users

AI Insights & Confidence Level
What is the Confidence Level?

The confidence level is a business-facing indicator representing the severity and urgency of potential stock-outs, derived from stock-out risk scores.

Note: This is not a model probability. It is a human-readable signal for prioritizing actions.

Mapping Risk Score → Confidence Level
Stock-Out Risk Score	Confidence Level	Interpretation
≥ 0.8	HIGH	Immediate action recommended
0.4 – 0.79	MEDIUM	Monitor closely and plan replenishment
< 0.4	LOW	Inventory is sufficient
Why It Matters

Converts technical risk metrics into human-readable decisions

Supports prioritization of actions for inventory planners

Reduces alert fatigue and improves operational trust

Provides auditability of AI decisions

Example

“Product Beverages at Store 3 shows a HIGH confidence stock-out risk because forecasted demand during supplier lead time exceeds current inventory.”

This allows stakeholders to act immediately without understanding the underlying ML model.

**Design Principles**

Human-centered AI: Abstract technical outputs into actionable insights

Explainable & auditable: Supports trust and operational adoption

Production-ready: Fully integrated with Delta Lake and MLflow

Future enhancements could include:

Incorporating forecast uncertainty

Accounting for demand volatility

Leveraging historical stock-out data for better confidence estimation

**Key Features**

Medallion Architecture: Bronze → Silver → Gold

Delta Lake: Reliable, versioned storage

MLflow: Tracks models and experiments

AI Explainability: Insights table translates model outputs to business decisions

Replenishment Engine: Automatically computes reorder points and quantities


┌──────────────────────────────────────┐
│            RAW DATA SOURCES           │
│                                      │
│  • Sales CSV                          │
│  • Daily Inventory Snapshot           │
│  • Supplier Lead Time                 │
└─────────────────────┬────────────────┘
                      │
                      ▼
┌──────────────────────────────────────┐
│        🥉 BRONZE LAYER (Raw)          │
│                                      │
│  • bronze_sales_raw                  │
│  • bronze_inventory_snapshot         │
│  • bronze_suppliers_raw              │
│                                      │
│  (Append-only, no transformations)   │
└─────────────────────┬────────────────┘
                      │
                      ▼
┌──────────────────────────────────────┐
│      🥈 SILVER LAYER (Cleaned)        │
│                                      │
│  • silver_daily_sales                │
│  • silver_inventory_snapshot         │
│  • silver_supplier_lead_time         │
│                                      │
│  (Validated & standardized data)     │
└─────────────────────┬────────────────┘
                      │
                      ▼
┌──────────────────────────────────────┐
│     🥇 GOLD LAYER (AI & Business)     │
│                                      │
│  • Demand Feature Engineering        │
│  • ML Demand Forecast                │
│  • Stock-Out Risk Scoring             │
│  • Replenishment Recommendations     │
│  • AI-Generated Insights              │
│                                      │
│  (Decision-ready outputs)            │
└─────────────────────┬────────────────┘
 

