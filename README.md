<div align="center">

# -- ! Myntra Sales Dashboard ! --
### *Interactive Power BI Dashboard for E-Commerce Sales & Product Analytics*

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Measures%20%26%20KPIs-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Data Model](https://img.shields.io/badge/Data%20Model-5%20Tables-4CAF50?style=for-the-badge&logo=databricks&logoColor=white)](https://powerbi.microsoft.com/)
[![E-Commerce](https://img.shields.io/badge/Domain-E--Commerce%20Retail-E91E63?style=for-the-badge&logo=myntra&logoColor=white)](https://www.myntra.com/)

<br/>

> *"Every order is a data point — a good dashboard turns thousands of them into a decision."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🔄 Project Workflow](#-project-workflow)
- [🛒 Part A — Sales Overview Page](#-part-a--sales-overview-page)
- [📦 Part B — Product Analysis Page](#-part-b--product-analysis-page)
- [🛠️ Tech Stack](#️-tech-stack)
- [📈 Results & Insights](#-results--insights)
- [🏆 Advantages](#-advantages)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Myntra Sales Dashboard** is an interactive, two-page **Power BI** report that analyzes fashion e-commerce orders. It shows how orders and revenue are spread across brands, categories and city tiers, how sales move over time, and how products and inventory sizes perform. The report is designed at **1920 × 1080** with KPI cards, filter slicers, a page navigator and custom icons.

This project is designed to:
- Track **total orders** and **total revenue** at a glance
- Compare performance by **brand**, **category** and **city tier**
- Analyze **sales trends** by month and day using a date hierarchy
- Review **product-level** orders and revenue, order status and size-wise inventory
- Practice **data modeling**, **DAX measures** and **dashboard design** in Power BI

---

## 🎯 Problem Statement

> **Objective:** Build an interactive dashboard that helps a fashion e-commerce team understand where orders and revenue come from and which products and sizes drive them.

Order data on its own is a long flat table. This dashboard turns it into a clear story: which brands and categories sell the most, which city tiers bring in revenue, how sales change over time, and how inventory is spread by size.

| 📂 Table | 📄 Type | 🔍 Description |
|----------|---------|----------------|
| myntra_orders_master | Fact | Orders with product, brand, category, city tier, order status and quantity |
| DimDate | Dimension | Date table with a Year / Month / Day hierarchy for trend analysis |
| Brand_Group | Dimension | Brand labels used for the brand performance chart |
| Inventory_Unpivot | Fact | Inventory by size, reshaped (unpivoted) for charting |
| MeasuresTable | Measures | Holds all DAX measures and KPIs |

The goal is to demonstrate **end-to-end BI skills** — from data preparation to measures to a clean, navigable report.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 📑 **2 Report Pages** | Sales Overview and Product Analysis, linked by a page navigator |
| 🎛️ **3 Slicers** | Filter by City Tier, Category and Brand on the Sales Overview page |
| 🔢 **KPI Cards** | Total Orders, Total Revenue and Total Products |
| 📊 **Orders by Brand & Category** | Bar and column charts of order counts |
| 🍩 **Distribution Donuts** | Orders by city tier, order status and category |
| 📈 **Time Trends** | Area charts of revenue by month and quantity by month and day |
| 🏙️ **City Tier Revenue** | Revenue in crores (Cr) for each city tier |
| 🏷️ **Brand Performance** | Revenue in crores by brand group |
| 📏 **Size-wise Inventory** | Column chart of inventory by size |
| 🧾 **Product Table** | Product, brand, category, orders count and revenue in rupees |

---

## 🏗️ Project Structure

```
📦 myntra-sales-dashboard/
│
├── 📄 Myntra_dashboard.pbix   ← Power BI report (data model + 2 pages)
│
└── 📄 README.md               ← Project documentation
```

---

## 🔄 Project Workflow

```
Raw Myntra Orders Data
      │
      ▼
┌─────────────────────────────┐
│   Load & Clean Data         │  ← Orders master, Inventory (unpivoted), Brand groups
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   Build Data Model          │  ← DimDate + MeasuresTable (DAX)
└────────────┬────────────────┘
             │
     ┌───────┴────────┐
     ▼                ▼
┌─────────────┐   ┌──────────────────┐
│  Page 1     │   │     Page 2       │
│  Sales      │   │   Product        │
│  Overview   │   │   Analysis       │
└──────┬──────┘   └────────┬─────────┘
       │                   │
       ▼                   ▼
┌─────────────────────────────┐
│  Slicers: City Tier         │
│  Category · Brand           │
└────────────┬────────────────┘
             │
             ▼
   KPI Cards + Charts Update
             │
             ▼
   Insights for Business Team ✅
```

---

## 🛒 Part A — Sales Overview Page

### 📝 1. What does this page show?

The **Sales Overview** page answers: *how many orders and how much revenue are we getting, and from which brands, categories and city tiers?*

---

### 🗺️ 2. Visuals — Overview

| Visual | Type | Fields Used |
|--------|------|-------------|
| 🧾 Total Orders | KPI Card | `Total Orders` |
| 💰 Total Revenue | KPI Card | `Revenue Display` |
| 🏷️ Orders by Brand | Clustered Bar | `Brand_Name`, `Total Orders` |
| 🧥 Orders by Category | Clustered Column | `Category`, `Total Orders` |
| 🏙️ Orders by City Tier | Donut | `City_Tier`, `Total Orders` |
| 📈 Revenue Trend | Area Chart | `DimDate` (Month), `Total Revenue` |
| 📈 Quantity Trend | Area Chart | `DimDate` (Month, Day), `Quantity` |

---

### 🎛️ 3. Slicers

> Three slicers filter the visuals on this page.

| Slicer | Source Column |
|--------|---------------|
| City Tier | `myntra_orders_master[City_Tier]` |
| Category | `myntra_orders_master[Category]` |
| Brand | `myntra_orders_master[Brand_Name]` |

---

## 📦 Part B — Product Analysis Page

### 🔍 4. What does this page show?

The **Product Analysis** page answers: *which products, brands and sizes drive revenue, and how are orders distributed by status and category?*

---

### 🗺️ 5. Visuals — Overview

| Visual | Type | Fields Used |
|--------|------|-------------|
| 🔢 Total Products | KPI Card | `Total Products` |
| 🏙️ City Tier Analysis (Revenue) | Clustered Column | `City_Tier`, `Revenue Cr` |
| 🏷️ Brand Performance (Revenue) | Clustered Bar | `Brand_Label` (Brand_Group), `Revenue Cr` |
| 📏 Size-wise Inventory | Clustered Column | `Size`, `Inventory` (Inventory_Unpivot) |
| 🍩 Product Distribution | Donut | `Order_Status`, `Total Orders` |
| 🍩 Product Distribution | Donut | `Category`, `Total Orders` |
| 🧾 Product Table | Table | `Product_Name`, `Brand_Name`, `Category`, `Orders Count`, `Revenue Rs` |

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| 📊 **Power BI Desktop** | Latest | Report authoring and data modeling |
| 🧮 **DAX** | Built-in | Measures such as Total Orders, Total Revenue, Revenue Cr, Revenue Rs, Orders Count, Total Products |
| 🗃️ **Data Model** | 5 tables | Orders master, DimDate, Brand_Group, Inventory_Unpivot, MeasuresTable |
| 🎨 **Fluent 2 Theme** | Built-in | Base theme for the report |
| 🧭 **Page Navigator** | Built-in | Switching between the two pages |
| 🖼️ **Custom Icons** | PNG | Myntra logo, rupee, cart, cube, calendar and chart icons |

---

## 📈 Results & Insights

After opening the report, the following outputs are available:

- ✅ **Headline KPIs** — Total orders, total revenue and total products
- 🏷️ **Brand & Category Ranking** — Which brands and categories get the most orders
- 🏙️ **City Tier Split** — Order share and revenue (in Cr) for each city tier
- 📈 **Sales Trends** — Revenue by month and quantity by month and day
- 📏 **Inventory by Size** — Which sizes hold the most stock
- 🧾 **Product-level Detail** — Orders count and revenue (Rs) for each product

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎓 **Single View** | Orders, revenue, products and inventory in one report |
| 🎛️ **Easy Filtering** | City Tier, Category and Brand slicers |
| 🔄 **Reusable Model** | A dedicated MeasuresTable keeps all DAX measures in one place |
| 📅 **Date Hierarchy** | Drill from month to day in the trend charts |
| 🖥️ **Clean Layout** | Consistent 1920 × 1080 design with KPI cards and a page navigator |
| 🧪 **Extensible** | Easy to add pages such as Returns, Customers or Discounts |
| 📖 **Readable Visuals** | Revenue shown in crores (Cr) and rupees (Rs) for Indian business reporting |
| 🛡️ **Large Data Ready** | Built on a full orders master table, not a small sample |

---
## SALES OVERVIEW
<img src="assets/page 1.png">

---

## PRODUCT ANALYSIS

<img src="assets/page 2.png">

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full details.

```
MIT License — Free to use, modify, and distribute with attribution.
```

---

## 👤 Author

<div align="center">

### Divyesh Jadav

[![GitHub](https://img.shields.io/badge/GitHub-yourhandle-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/yourhandle)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/your-profile/)

> *"Every dashboard starts with a question — and ends with a better decision."*

**🎓 Role:** Data Analyst | Power BI Enthusiast \
**📍 Location:** India\
**🛠️ Skills:** Power BI · DAX · Data Modeling · Dashboard Design · Data Visualization

</div>

---

## 🙏 Acknowledgements

Special thanks to the following resources and communities that made this project possible:

- 📚 [Power BI Documentation](https://learn.microsoft.com/en-us/power-bi/) — Official Power BI reference
- 🧮 [DAX Guide](https://dax.guide/) — Complete DAX function reference
- 🎨 [Power BI Report Design Guidance](https://learn.microsoft.com/en-us/power-bi/guidance/) — Layout and design best practices
- 🖥️ [Microsoft Learn — Power BI](https://learn.microsoft.com/en-us/training/powerplatform/power-bi) — Beginner to advanced courses
- 💬 [Power BI Community](https://community.fabric.microsoft.com/) — Problem-solving support
- 📖 [Kaggle Learn](https://www.kaggle.com/learn) — Data and analytics courses

---

<div align="center">

---

*Made with ❤️ and ☕ — Last updated: 4 November, 2026*

</div>
