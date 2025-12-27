# Garments Production Health & Efficiency Dashboard (Power BI)

## Overview
This Power BI project provides an end-to-end view of **garments production health**—from **work order creation** to **shipment**—so teams can track **production progress, quality, delivery performance, cost control, and profitability** in one interactive report.

It is built for quick analysis using slicers (WO, buyer, product, destination, status, time) without manual Excel reporting.

---

## Report Preview (Screenshots)

### 1) Work Orders
![Work Orders](Report%20Images/1.%20Word%20Orders.jpg)

### 2) Quality
![Quality](Report%20Images/2.%20Quality.jpg)

### 3) Timeline & Delivery
![Timeline & Delivery](Report%20Images/3.%20%20Timeline%20%26%20Delivery.jpg)

### 4) Cost & Profitability
![Cost & Profitability](Report%20Images/4.%20%20Cost%20%26%20Profitability.jpg)

### 5) Executive View
![Executive View](Report%20Images/5.%20Executive%20View.jpg)

---

## What this report helps you answer
- Which **buyers / products / destinations** generate the most **revenue and profit**?
- Are we delivering **on time**? If not, which stage is causing delays?
- Where are **defects** happening most, and which products have the highest **defects per 1000**?
- How much **fabric is used vs wasted**, and what’s driving waste (cutting, defects, rework)?
- Which work orders are **at risk** due to low progress, time pressure, or rising costs?
- How do **planned vs actual** costs compare by production stage?

---

## Folder structure
- **PBIX/**
  - Main Power BI report file (`.pbix`)
- **Database/**
  - Excel-based source tables (facts + dimensions)
- **Documents/**
  - Business case + exported PDF snapshot of the report
- **Report Images/**
  - Report page screenshots (used above)

---

## Data model (high level)
This is a **production-focused star schema**.

### Main fact table
- **Fact_Process**
  - Tracks production progress by date and stage (cutting, sewing, QC, packing, shipping)
  - Includes quantities, defects, fabric usage, operator info, freight/cost fields (as available)

### Key dimensions (examples)
- **Dim_WorkOrders**: WO header (buyer, product, destination, dates, ordered qty, pricing/cost)
- **Dim_ProductionPlan**: planned timeline + planned costs + operator assignments
- **Dim_Product**: product metadata + fabric consumption per piece + targets
- **Dim_Buyer**: buyer profile and grouping
- **Dim_Destination**: delivery destination information
- **Dim_Date**: calendar for slicing and trends
- **Dim_Operator / Dim_Employee**: labor/people mapping
- **Dim_Materials**: materials purchasing and unit prices (where applicable)

---

## Report pages (what you’ll see)

### 1) Work Orders
Focus: **WO volume + production progress**
- Total WOs, completed vs in-progress
- Ordered vs cut vs sewn vs checked vs packed vs shipped
- Work orders by buyer and product
- Trend by order date + detail tables

### 2) Quality
Focus: **QC performance + defect monitoring**
- Quality score, defect rate, defects per 1000
- QC efficiency and top defect products
- Buyer vs quality view
- Operator performance table (comparative view)

### 3) Timeline & Delivery
Focus: **on-time delivery + stage duration**
- On-time % and delayed WOs
- Planned vs actual duration by stage
- Delivery status breakdown
- Process timeline table for WO-level tracking

### 4) Cost & Profitability
Focus: **cost drivers + margins**
- Revenue, profit, margin KPIs
- Planned vs actual costs by stage (cut/sew/QC/pack/ship/others)
- Profit by buyer / product
- WO-level profitability detail table

### 5) Executive View
Focus: **leadership summary**
- Key KPIs in one page (delivery, revenue, profit, QC, shipped qty, waste, labor usage)
- Revenue by country + trend
- Ordered vs delivered summary
- Quick slicing for management review

---

## Common slicers/filters available
- **Work Order (WO_ID)**
- **Buyer**
- **Product**
- **Destination/Country**
- **WO Status** (Completed / Processing)
- **Delivery Status** (On Time / Delayed)
- **Date / Month / Year**

---

## KPI definitions (plain language)
- **Revenue**: sales value based on the model’s pricing logic
- **Gross Profit**: revenue minus total cost (planned/actual depending on page context)
- **Gross Margin %**: gross profit divided by revenue
- **On-Time Delivery %**: WOs delivered on/before committed date
- **Quality Score / Defect Rate**: QC performance indicators used in the model
- **Defects per 1000**: normalized defect metric for fair product comparison
- **Fabric Used / Fabric Waste**: usage and waste indicators based on fabric consumption logic
- **Stage Cost**: cutting/sewing/QC/packing/shipping/others (planned vs actual comparisons)

---

## How to open & refresh (Power BI Desktop)
1. Open the `.pbix` file in **Power BI Desktop**
2. If refresh fails after moving folders:
   - Go to **Transform data → Data source settings**
   - Update paths to the Excel files inside **Database/**
3. Click **Refresh**

Tip: Keep the folder structure unchanged to avoid broken paths.

---

## Notes
- Built on structured/sample garments production datasets (Excel-based).
- Best used with slicers + drilldown (charts → tables) to investigate risk WOs, defects, and margin drivers.
