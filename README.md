# Sales Overview Power BI Dashboard

An enterprise-grade Power BI Desktop solution designed to deliver end-to-end sales performance tracking, product profitability diagnostics, customer segmentation analysis, and interactive "What-If" scenario planning.

##  Key Features

* **Executive KPI Tracking:** Instant visibility into global revenue streams, order fulfillment pipelines, and item return distributions.
* **Dynamic Measures & Dimensions (Field Parameters):** Advanced toggle switches allowing users to dynamically change report visuals between different analytical dimensions and core business metrics.
* **What-If Scenario Simulation:** Integrated price adjustment parameters to simulate revenue fluctuations and project margins dynamically.
* **Geospatial Intelligence:** Location-based density and performance mapping using interactive Azure Map components.
* **Granular Drill-Downs:** Dedicated tooltips and conditional navigation paths providing itemized breakdowns without cluttering primary views.

---

##  Dashboard Architecture

The report contains specialized reporting surfaces and underlying configuration layouts:

### 1. Overview Page
The primary cockpit for executives to monitor macro performance trends.
* **High-Level KPI Cards:** Displays critical data points including `Total Sales`, `Order Volume`, `Return Quantity`, and `% Return`.
* **Geospatial Mapping:** Features an **Azure Map** visualizing performance metrics layered across `Continent`, `Country`, and `Region`.
* **Temporal Trends:** A detailed **Line & Area Chart** plotting `Sales` vs. `Adjusted Price` across a fully customizable `CALENDAR` timeline.
* **Categorical Breakdown:** A **Horizontal Bar Chart** classifying sales performance by `Product Subcategory` cross-filtered by Customer Status.
* **Interactive Slicers:** Universal slicing panel enabling global multi-select filters for Category, Customer Gender, Territory Regions, Date Ranges, and dynamic dimensions.

### 2. Product Overview Page
Deep dive into product metrics, catalog positioning, and associated customer demographics.
* **Financial Metrics:** Tracking cards evaluating `Product Name`, `Product Price`, and `Product Cost` structures.
* **Rankings & Competitiveness:** A **Ribbon Chart** mapping `Total Sales` transitions over consecutive months and years to reveal seasonal trends and product shifts.
* **Customer Profiles:** Combined **Donut Charts** exploring order concentrations against customer attributes (e.g., Marital Status, Parent/Household status).
* **Client Matrix:** An interactive **Data Table** listing itemized customer logs including `First Name`, `Email Address`, and `Gender`.

### 3. Core Supporting Layouts
* **Tool Tips Page:** Context-aware hover tooltips configuring visual drill-downs for main charts.
* **KPI & Map Sheets:** Dedicated back-end analytical pages containing optimized layouts for tracking specialized geographical metrics.

---

##  Data Model & Formulas

The dashboard relies on a star/snowflake schema variant containing core dimensions and transaction facts linked together. 

### Key Equations Used (DAX Logic)
The core business KPIs are governed by standard financial definitions modeled inside the `Measure Table`:

* **Return Percentage:**
    $$\% \text{ Return} = \frac{\text{Sum of Return Quantity}}{\text{Total Ordered Units}} \times 100$$

* **Adjusted Revenue Model:**
    $$\text{Adjusted Price} = \text{Base Product Price} \times \left(1 + \text{Price Adjustment } \% \right)$$

* **Time Intelligence Comparisons:**
    * `Prev yr sales`: Evaluates revenue performance against parallel historical periods: $\text{Sales}_{t-1}$.
    * `Prev mon order`: Tracks transactional volume velocity vs. the immediate preceding month.

### Main Tables Ingested
* `Final_Sales` & `Returns` (Transaction Facts)
* `Customers Table` (Demographics: Full Name, Gender, Marital Status)
* `Products`, `Product Categories`, & `Product Subcategories` (Catalog Hierarchy)
* `Territories` (Geographic Hierarchy: Continent $\rightarrow$ Country $\rightarrow$ Region)
* `CALENDAR` (Time-Intelligence dimension)
* `Price Adjustment %` (Scenario simulation parameter table)

---

##  Setup and Installation

To explore or modify this dashboard locally:

1. **Prerequisites:** Ensure you have the latest version of [Microsoft Power BI Desktop](https://powerbi.microsoft.com/desktop/) installed.
2. **Clone the Repository:**
   ```bash
   git clone [https://github.com/rt5899-art/Sales-Overview.git](https://github.com/rt5899-art/Sales-Overview.git)# Sales-Overview

  ##  Author
   rt5899-art
