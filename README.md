# Superstore Sales Performance: Python EDA + Power BI Dashboard

**Business question:** Sales grew 51% in four years. Why did profit not grow faster, and what should management change?

**Answer in one line:** Discounts above 20% lose money on almost every sale (97%). They cost $135K, almost a third of the profit the store could have made ($422K instead of $286K).

📄 **Dashboards (PDF):** [Full analytical dashboard, 6 pages](Superstore_Dashboard.pdf) · [Management dashboard, 1 page](Superstore_Dashboard_management.pdf)

## Two dashboards for two audiences

| | Analytical dashboard | Management dashboard |
|---|---|---|
| **Audience** | Analysts, pricing and sales teams | Executives |
| **Question** | Where and why do we lose profit? | How is this year going? |
| **Pages** | Executive Overview, Discount Impact, Product, Customer, Regional, Key Findings & Recommendations | One page: YTD KPIs, monthly trend with next-year forecast, seasonality by year, category, state, region, segment, top products |
| **Filters** | Year, region, segment, category, sub-category | Year |

## Key findings

1. **Big discounts lose money.** Over 20% off, the margin turns negative: 29.5% with no discount, -10% at 21-30%, -77% above 40%. Without these orders, the margin would be 20-23% a year instead of 10-13%.
2. **Ten states lose money, and all of them discount heavily.** Texas, Ohio, Pennsylvania, Illinois and six other states lost $98K together, with average discounts of 28-39%.
3. **Furniture sells well but earns little.** It is 32% of sales but only 6% of profit. Tables and bookcases lose money.
4. **Five products lost $22K.** 3D printers, a laser printer and conference tables, sold at 28-53% off.
5. **A small group of customers brings most of the profit.** The top 20% of customers bring 82% of profit. 155 customers cost more than they bring in.
6. **Customers stay, but new ones stopped coming.** 87.5% retention in 2017, but only 11 new customers that year (595 in 2014).
7. **Sales follow the calendar.** September, November and December bring 43% of yearly sales; January and February only 7%. All three customer segments show the same pattern: the peaks come from more customers ordering, most likely back-to-school and holiday shopping.
8. **Q4 2017 was the biggest quarter, with a lower margin.** The margin fell to 9.8% (16.2% a year earlier).

## Recommendations

1. Cap discounts at 20%. Anything higher needs a manager's approval. Up to $135K of profit is at stake.
2. Test a 20% discount cap in Texas first, and compare it with Virginia (no discounts, 26% margin) and California.
3. Review costs on tables and bookcases. Drop items that lose money at any price ($21K lost).
4. Set a minimum price for expensive machines such as 3D and laser printers.
5. Give the top ~160 customers a personal contact. Review the deals with the 155 loss-making customers.
6. Run acquisition campaigns in January and February, the quiet months, with cheap high-margin items like paper and labels.
7. Plan stock and staff for September and November-December, and don't discount when people are already buying.

## What I built

**Python EDA** ([notebooks/01_eda.ipynb](notebooks/01_eda.ipynb)): data quality checks, profitability by category and region, discount impact, shipping speed, customer cohorts. The EDA found the patterns; the dashboard shows them to the business.

**Power BI data model (star schema):**
- Fact table: `Fact Sales` (one row per order line)
- Dimensions: `Dim Date`, `Dim Customer`, `Dim Product`, `Dim Geography`, `Dim Discount Band`
- Data cleaned and shaped in Power Query (M): types, discount bands, first order date per customer

**DAX:** 125+ measures in one `_Measures` table, including:
- Time intelligence: year-over-year change, YTD, latest-year values
- Discount analysis: `Profit at >20% Discount`, `Margin % excl >20% Discount`, `Profit if Deep Discounts Broke Even`
- Customer analysis: `New Customers`, `Customer Retention %`, `Cohort Retained %`, `Cumulative Profit Share %` (Pareto)
- Dynamic labels and titles that update with the filters

## Data

[Sample Superstore dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final): 9,994 order lines, 2014-2017, US retail (furniture, office supplies, technology). The CSV is not included in this repository. See [data/README.md](data/README.md).

## Tools

Python (pandas, matplotlib, seaborn, plotly) · Power BI · DAX · Power Query (M) · data modeling (star schema)
