# Operational Performance & Profitability Tracker  
(Excel • Power Query • Power Pivot)

## 📌 Project Overview
This project analyzes **operational performance, profitability, and revenue leakage due to returns** using a publicly available Superstore transactional dataset.

Rather than focusing only on topline revenue, the analysis answers deeper business questions:
- Are we growing profitably or just increasing revenue?
- Which products, customers, and regions drive profits vs losses?
- How much revenue and profit are silently lost due to returns?
- Where should management take corrective action?

The project follows a **production-style Excel analytics pipeline**:  
**Raw Data → Power Query (ETL) → Power Pivot Data Model → DAX Measures → Executive Dashboard**

---

## 🛠 Tech Stack
- **Tool:** Microsoft Excel  
- **Data Transformation:** Power Query (M)  
- **Data Modeling & Measures:** Power Pivot (DAX)  
- **Visualization:** Excel Pivot Charts & Dashboard  
- **Data Source:** Public Superstore dataset (`sample-superstore.xlsx`)

---

## 📂 Data Architecture & Design

### 🔹 Raw Data Layer
- Source Excel file ingested **without modification**
- File: `sample-superstore.xlsx`
- Sheets:
  - Orders
  - Returns
  - People

> Mirrors real-world ingestion pipelines where raw data is never mutated.

---

### 🔹 Fact & Dimension Modeling

| Table Name | Type | Description |
|-----------|------|-------------|
| `fact_orders` | Fact | Sales transactions with financial metrics |
| `fact_returns` | Fact | Returned orders modeled separately |
| `dim_people` | Dimension | Regional ownership (manager by region) |
| `Date` | Dimension | Dedicated calendar table for stable time analysis |

**Key design decisions:**
- Sales and returns are **never mixed**
- Returns modeled as a **separate fact table**
- No forced many-to-many relationships
- Logical linking handled via **DAX (TREATAS)**
- Dedicated Date table ensures stable filtering and trends

---

## 🔧 Power Query (ETL) Highlights
All cleaning and transformation logic is handled in **Power Query**, not Excel formulas.

### fact_orders
- Data type standardization
- Text cleaning (trimmed fields)
- Business columns created:
  - Discount Amount
  - Net Sales
  - Estimated Cost
  - Profit Margin %

### fact_returns
- Clean extraction of returned Order IDs
- No aggregation or deletion

### dim_people
- Region-to-person mapping for reporting

---

## 📐 DAX Measures (Business Logic)
Key measures include:
- Total Net Sales
- Total Profit
- Profit Margin %
- Total Orders
- Returned Orders
- Return Rate %
- Returned Net Sales
- Net Sales After Returns
- Profit After Returns
- Loss-Only Profit (for loss analysis)

All revenue leakage from returns is calculated **analytically rather than by removing data.**

---

## 📊 Executive Dashboard

### Dashboard Components

#### KPI Summary
- Net Sales  
- Net Sales After Returns  
- Total Profit  
- Profit After Returns  
- Profit Margin %  
- Return Rate %

#### Core Visuals
- Revenue & Profit Trend  
- Profitability by Region  
- Product Profitability (Category / Sub-Category)  
- Top Loss-Making Products  
- Top Loss-Making Customers  

#### Slicers
- Year  
- Month  
- Region  
- Category  
- Segment  

📸 **Dashboard Screenshot:**  
![Executive Dashboard](dashboard_screenshots/01_executive_dashboard.jpg)

---

## 💡 Key Insights (Data-Backed)

- **Overall Profitability**
  - Total Net Sales: **$1,974,619**
  - Total Profit: **$286,397**
  - Overall Profit Margin: **15%**

- **Revenue Leakage Due to Returns**
  - Return Rate: **6%**
  - Revenue lost due to returns: **$155,609**
  - Profit reduced from **$286,397 to $263,165** after returns  
  - Returns caused a **$23,232 direct profit impact**

- **Regional Performance**
  - **West region is the most profitable** with **$108,418 profit**
  - **Central region shows weakest profitability** with only **$39,706 profit**
  - East region delivers strong margins with **$91,523 profit**
  - Significant regional variance indicates need for localized strategies

- **Product-Level Profitability**
  - Office Supplies and Technology categories generate most of the profit
  - Furniture category contains major loss pockets:
    - **Tables: –$17,725**
    - **Bookcases: –$3,473**
  - Copiers are the most profitable sub-category with **$55,618 profit**

- **High-Risk Products**
  - Losses are highly concentrated in a few expensive items:
    - Cubify CubeX 3D Printer Double Head: **–$8,880**
    - Lexmark MX611 Printer: **–$4,590**
    - Cubify CubeX Triple Head Printer: **–$3,840**
  - Top 10 loss-making products contribute a disproportionate share of total losses

- **Customer Profitability Risk**
  - A small group of customers drive significant losses:
    - Cindy Stewart: **–$6,626**
    - Grant Thornton: **–$4,109**
    - Luke Foster: **–$3,584**
  - Indicates opportunity for pricing review and return policy controls

- **Trend Observations**
  - Strong seasonality with revenue peaks in **November–December**
  - Certain months show profit volatility despite high sales, indicating margin instability

---

## 🔍 Business Conclusion

Although the business generates healthy overall margins, **returns and a small subset of products and customers create significant hidden profit leakage.**  
Targeted actions on high-loss products, better return controls, and regional strategy adjustments can meaningfully improve realized profitability.

---

## 🧠 Skills Demonstrated
- Power Query ETL (M language)
- Fact vs dimension modeling in Excel
- Multi-fact modeling (Orders + Returns)
- DAX measures for executive KPIs
- Revenue leakage & profitability analysis
- Executive dashboard design
- Business-first analytical thinking

---

## 🚀 Future Enhancements
- Month-over-Month and Year-over-Year growth analysis
- Customer lifetime value (CLV) metrics
- Product-level return rate analysis
- RFM segmentation
- Migration to Power BI or SQL warehouse

---

## 👤 Author
**Indranil Bhosale**  
Aspiring Data Analyst  
Excel • Power Query • Power Pivot • Analytics
