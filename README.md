# Retail Sales Revision – Power BI Dashboard

## Project Overview

This Power BI project is a multi-page interactive sales analytics dashboard built for a retail business. It consolidates data from customers, products, territories, and sales transactions into a single report that enables stakeholders to monitor revenue performance, product trends, return rates, and regional distribution. The report is structured around nine pages, each serving a distinct analytical purpose — from a high-level executive overview down to granular product, customer, and time-series analysis.

The report is designed for business users who need quick, filterable insights without requiring technical knowledge. It uses slicers, dynamic measures, KPIs, maps, and tooltip pages to deliver a seamless self-service analytics experience.

---

## Data Model

The report connects several core tables:

- **Final_Sales** — transactional sales records including order numbers, sales amounts, and stock dates
- **Customers Table** — customer attributes including name, gender, marital status, parental status, annual income, and email address
- **Products** — product details including name, price, cost, color, and a computed order count
- **Product Categories / Product Subcategories** — hierarchical classification of products
- **Territories** — geographic dimensions: continent, country, region, city, and state
- **CALENDAR / DAte** — date table supporting time intelligence (year, month, hierarchy)
- **Returns** — return transaction data with quantities
- **Map** — dedicated table supporting geographic map visuals
- **Measure Table** — a dedicated DAX measure table containing calculated KPIs
- **Measure Selector 2 / Dimensions 2** — field parameter tables enabling dynamic measure and dimension switching

---

## Report Pages

**Page 1 (Data Table)**
A summary table showing total sales and maximum sales grouped by product category, sourced from a summarized intermediate dataset.

**Overview**
The primary executive dashboard. Displays total sales, order count, return quantity, and percentage returns as cards. Includes a bar chart of sales by product subcategory broken down by customer status, a line chart comparing actual versus adjusted sales over time, a KPI visual tracking current sales against prior year targets and prior month orders, a geographic Azure Map showing sales by continent and country, and multiple slicers for category, gender, region, date, price adjustment, and dynamic measure/dimension selection.

**Product Overview**
Focuses on product and customer demographics. Shows product price, product cost, and product name as card visuals. A customer table displays names, emails, gender, parental status, and sales. A ribbon chart breaks total sales by country over yearly and monthly hierarchies. Two donut charts show total sales split by marital status and parental status.

**Tool Tip**
A tooltip page that surfaces on hover in other visuals. Displays subcategory name, total sales, average annual income, and a bar chart of sales split by gender.

**Page 3 (Bar Chart Analysis)**
Three comparative bar charts: a clustered bar chart showing yearly sales by customer status, a grouped bar chart showing subcategory sales by customer status, and a 100% stacked bar chart showing yearly sales proportions by customer status.

**Page 4 – Line and Area**
Time-series visuals: an area chart overlaying total sales with a product order count metric, and a line chart of sales over time. Accompanied by a detailed table showing product name, sales, order number, returns, and year, plus a pivot table breaking sales and order count by product category and year.

**KPI**
A dedicated KPI monitoring page. Three KPI visuals track sales against prior year targets and monthly trends. A card shows total sales. A column chart displays sales by date. A monthly comparison table shows current versus prior month sales. A fourth KPI tracks the prior month sales measure independently.

**Map**
A standalone Azure Map page visualizing sales volume by country, state, and city, with bubble sizing driven by sales amounts and color series by individual sales values.

**Ribbon**
A ribbon chart tracking total sales by product color over yearly and monthly hierarchies, and a pie chart showing sales and customer status counts broken down by country and customer status.

---

## Tools and Technologies Used

- **Microsoft Power BI Desktop** — report authoring, data modelling, and visualization
- **DAX (Data Analysis Expressions)** — calculated measures including total sales, percentage returns, adjusted price, previous year sales, previous month sales, order count, and dynamic KPI titles
- **Power Query (M Language)** — assumed data transformation and shaping during import
- **Azure Maps** — geographic visualization of sales by region, country, and city
- **Field Parameters** — dynamic measure and dimension switching via slicer-driven parameters (Measure Selector, Dimensions)
- **Power BI Themes** — CY24SU10 base theme applied for consistent visual styling
- **Enhanced Tooltips** — custom tooltip page for richer hover-state information on charts

---

## Requirements

To open and use this report:

- Microsoft Power BI Desktop (version compatible with report version 5.68 / CY24SU10 theme, approximately late 2024 release or later)
- Access to the underlying data sources that were used during development (the `.pbix` file contains a cached DataModel, so visuals will render with embedded data, but refreshing requires reconnecting to the original sources)
- An Azure Maps API subscription or organizational Power BI license that enables Azure Maps visuals
- A Power BI Pro or Premium license if the report is to be published and shared via the Power BI Service

---

## Challenges Faced

**Data model complexity**
Connecting sales, returns, customers, products, territories, and a separate calendar table requires careful relationship management to avoid ambiguous filter paths and incorrect aggregations, especially for time intelligence measures like previous year and previous month comparisons.

**Dynamic measure switching**
Implementing field parameters (Measure Selector and Dimensions) so that a single slicer drives which measure or dimension is shown across visuals adds report interactivity but requires careful DAX scaffolding and testing to ensure all visuals respond correctly.

**Return and adjustment metrics**
Calculating percentage returns and adjusted prices accurately across different filter contexts — particularly when both a Returns table and a Final_Sales table are involved — requires handling blank values and division-by-zero cases in DAX.

**Tooltip page configuration**
Setting up a dedicated tooltip page that triggers correctly on hover across multiple visuals, while maintaining consistent filter context and preventing tooltip slicers from affecting the main report pages, requires deliberate page-level configuration.

**Geographic mapping**
Azure Maps visuals require clean, standardized geographic data. Any inconsistencies in country names, region labels, or missing city/state values can cause incorrect pin placement or missing data points on the map.

**Typographical and naming inconsistencies**
The report contains some field and table name inconsistencies observed in the data model (for example, "Adjusted Prce" missing a letter, "DAte" as a table name, "Produt Overview" as a page name). These reflect iterative development and should be standardized in a future revision for maintainability.

---

## Findings and Insights

**Sales performance against targets**
The KPI page and Overview page together allow quick identification of months where sales fall below prior year benchmarks, making it easy for management to spot seasonal underperformance and act before quarter-end.

**Customer segmentation patterns**
The breakdown of sales by gender, marital status, and parental status on the Product Overview page reveals which customer segments contribute disproportionately to revenue. These dimensions can inform targeted marketing and product stocking decisions.

**Subcategory revenue concentration**
The bar charts on the Overview and Page 3 surfaces suggest that a small number of subcategories likely account for the majority of total sales, a pattern consistent with retail Pareto distributions. The customer status series overlay helps identify whether premium or standard customer tiers are driving those top subcategories.

**Geographic concentration**
The Azure Maps visuals on the Overview and Map pages allow visual identification of high-revenue geographies at the continent, country, and regional level. This supports decisions about where to invest in logistics, marketing spend, or expansion.

**Return rate as a quality signal**
The return quantity card and percentage return measure on the Overview page provide an at-a-glance check on product or fulfilment quality. Filtering by subcategory or region can help isolate whether returns are concentrated in specific products or geographies.

**Price sensitivity**
The Price Adjustment % slicer on the Overview page, combined with the adjusted price line chart, enables scenario-style analysis of how pricing changes affect overall sales volume, giving commercial teams a tool for quick what-if exploration.

**Seasonal and monthly trends**
The line, area, pivot, and ribbon charts across multiple pages consistently support monthly and yearly trend analysis. The prior month sales comparison table on the KPI page is particularly useful for identifying momentum shifts at a granular level.

---

## Recommendations

1. **Standardize naming conventions** across all tables, columns, and pages. Correct typos such as "Adjusted Prce," "DAte," and "Produt Overview" to improve readability and reduce confusion for future developers.

2. **Document all DAX measures** with inline comments or a measure description field, particularly for KPI title measures (rderkpi title, salekpi titles) and the dynamic selector parameters whose logic may not be self-evident.

3. **Add row-level security (RLS)** if the report is to be distributed to regional managers or external stakeholders, scoping their view to relevant territories or customer segments.

4. **Consolidate Page 1 and Page 3** or clearly label them — currently both are named with generic identifiers ("Page 1," "Page 3") rather than descriptive titles, making navigation confusing for end users.

5. **Implement incremental data refresh** if the underlying data source grows over time, to avoid full model refreshes that will become slower as transaction history accumulates.

6. **Add a dedicated Returns Analysis page** that brings together return quantity, return rate by category, return rate by region, and trending over time, rather than distributing return metrics across multiple pages.

7. **Version-control the `.pbix` file** using Power BI Projects format (`.pbip`) or by exporting the report definition to source-control-friendly JSON/TMDL files, enabling diff tracking and team collaboration on the data model.
