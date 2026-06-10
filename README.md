## Retail Sales Performance and Executive Overview 

An interactive, multi-page Power BI analytics dashboard designed to consolidate customer demographics, transaction logs, returns, and regional territories into an actionable business intelligence engine.

### Project Overview

This project transforms fragmented operational data spreadsheets into a unified, relational data model. Spanning across specialized reporting pages, it tracks top-line retail KPIs, monitors product category velocity, analyzes product return rates, and evaluates customer profiling to optimize gross revenue streams.

### Tools & Technologies

Data BI Platform: Microsoft Power BI Desktop

Data Transformation: Power Query / M Language

Modeling & Analytics: DAX (Data Analysis Expressions) for time-intelligence, field parameters, and calculated metrics

Geographic Visualization: Azure Maps API integration

#### Dashboard Preview

!![image alt](https://github.com/rt5899-art/Sales-Overview/blob/main/ss-Sales%20overview.png?raw=true)

### Key Business Insights

* Top-Line Performance: The platform captures a total gross sales engine of 24.91M in global revenue.

* Transaction Velocity: Total cumulative traffic reaches an order count of 25.16K individual sales records.

* Return Rate Balance: System metrics monitor product return quantities and percentage return thresholds to maintain baseline inventory safety flags.

* Product Concentration: Revenue distributions show strong variances across primary product subcategories, driven cleanly by differing customer segments and statuses.

* Demographic Triggers: Cross-filtering sales variables against marital status, parental status, and household annual income values isolates high-value customer personas.

### Strategic Recommendations

Address Data Infrastructure Deficiencies Insight ➔ The foundational model shows iterative column and table spelling mismatches (such as missing characters in price variables and mixed case names like "DAte").

* Action ➔ Implement strict data cataloging rules and refactor table properties within Power Query to ensure system maintainability as the transactional pipeline grows.

Isolate Product Returns Leakage Insight ➔ Return quantities are currently distributed across disparate visual fields without a dedicated root-cause analyzer page.

* Action ➔ Build a localized Returns Analysis matrix to cross-reference product subcategory defects against regional distributor performance to reduce overhead margins.

Cleanse Navigation and Reporting Layouts Insight ➔ The reporting structure relies on unmapped sheet layout names (e.g., "Page 1" and "Page 3") which hampers non-technical stakeholder use.

* Action ➔ Standardize workspace tabs into descriptive, business-centric titles such as Category Performance Matrix or Executive Demographic Breakdown.

Deploy Contextual Field Parameters Insight ➔ Static time-series analysis limits advanced comparison views between current actual values versus prior year baselines.

Action ➔ Build multi-layer DAX field parameter slicers to allow stakeholders to dynamically toggle raw charts between total volume, adjusted dollar adjustments, and prior month velocity.
