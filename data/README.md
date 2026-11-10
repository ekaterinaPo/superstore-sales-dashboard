# Data

## Dataset: Sample Superstore Sales

**Source:** Kaggle — search "Sample Superstore" or use direct link:
https://www.kaggle.com/datasets/vivek468/superstore-dataset-final

**File to download:** `Sample - Superstore.csv`

**Place at:** `data/raw/Sample - Superstore.csv`

The CSV is not committed to this repository (Kaggle licensing). Download it manually before running the notebooks.

### Dataset summary
- ~9,994 rows, 21 columns
- Date range: January 2014 – December 2017
- Geography: United States (49 states)
- Dimensions: Region, State, City, Customer Segment, Product Category, Sub-Category, Ship Mode
- Metrics: Sales, Quantity, Discount, Profit

### Known data quality notes
- **Postal Code** is stored as a number in the source CSV, so leading zeros are dropped (e.g. `6824` should be `06824`). Affects Northeast states (CT, NJ, MA, RI, NH, ME). Not corrected — Postal Code isn't used in any analysis or dashboard visual; `State` carries the geographic breakdown instead.
- **Ship Days** (`Ship Date` − `Order Date`) was checked against Category, Sub-Category, Region, and Profit Margin — no meaningful pattern in any of them (all flat within ~0.4 days; margin correlation ≈ 0). Ship Mode shows the expected tiers (Same Day ≈ 0 days, Standard Class ≈ 5 days), confirming the labels are accurate but not revealing a business finding. Not included as a dashboard visual for this reason.
