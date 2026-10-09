# Retail Sales Pulse — CBIM MUC01

## Project Overview
**Retail Sales Pulse** is a retail sales analysis and weekly reporting project. It uses six months of historical sales data from a CSV file and the latest weekly sales data from a JSON API response to identify store performance, category trends, revenue anomalies, and areas that need operational attention.

The notebook covers both exploratory data analysis (EDA) and a data pipeline that validates, transforms, and summarizes weekly sales data.

## Business Problem
Retail operations managers need a clear, repeatable way to:
- Compare sales performance across stores and product categories.
- Identify low-performing stores and unusual revenue drops.
- Track historical trends and weekday/monthly patterns.
- Detect categories whose weekly revenue falls significantly below historical performance.
- Produce a concise weekly report to support operational decisions.

## Data Sources
- **Historical data:** `MUC01_Retail_Sales_Dataset.csv` — used for six-month EDA and historical baselines.
- **Weekly data:** `MUC01_Weekly_Sales_API_Response.json` — a JSON response containing the latest weekly transaction records and metadata.
- **Corrupt JSON test input:** Used in the notebook to test pipeline validation and error handling.

> Place the required data files in the notebook's working directory before running the relevant cells. The notebook expects these filenames.

## Tools and Libraries
- Python
- pandas
- NumPy
- Matplotlib
- Seaborn
- JSON processing and Python data validation

## Notebook Workflow

### Part 1 — Exploratory Data Analysis
1. Load and inspect the historical CSV dataset.
2. Review data shape, columns, data types, summary statistics, missing values, duplicates, and invalid or negative values.
3. Analyze revenue by store.
4. Compare product-category revenue over time.
5. Explore weekday and monthly sales patterns.
6. Identify unusually low weekly revenue using historical comparisons.
7. Summarize business findings and recommendations.

### Part 2 — Data Pipeline and Validation
1. Inspect the weekly JSON response structure and metadata.
2. Parse transaction records from the JSON `data` field.
3. Compare the metadata record count with the actual number of records received.
4. Validate records before processing and test handling of corrupt input.
5. Transform and aggregate weekly sales by store and category.
6. Compare weekly category revenue with the historical baseline.
7. Generate a weekly operations summary and pipeline status.

## Key Findings Recorded in the Notebook
The following figures are documented in the notebook and should be interpreted in the context of the provided datasets:

- **Highest six-month store revenue:** S01 — Vijayawada, approximately ₹5.91 crore.
- **Lowest six-month store revenue:** S12 — Kakinada, approximately ₹2.20 crore.
- **Highest monthly revenue:** January, approximately ₹8.48 crore.
- **Highest average daily revenue by weekday:** Saturday, approximately ₹35.24 lakh.
- **Category trend to investigate:** Electronics revenue declined by about 25% from January to June.
- **Potential store-week anomalies:** S05, S10, S02, and S04 were flagged for unusually low weekly revenue compared with their historical patterns.

### Example Weekly Operations Summary
The notebook records this example summary from the weekly JSON processing:

| Metric | Result |
|---|---|
| Weekly revenue | ₹1.50 crore |
| Top store | S03 — Guntur (₹20.38 lakh) |
| Bottom store | S10 — Nellore (₹6.27 lakh) |
| Top category | Electronics (₹57.65 lakh) |
| Lowest category | Personal Care (₹15.58 lakh) |
| Records processed | 4,291 |
| Pipeline status | Completed successfully |

These are the notebook's recorded results, not live or independently refreshed figures.

## Category Alert Logic
The notebook includes a category alert when the current week's revenue is more than **20% below** its historical six-month weekly average. This helps highlight categories that may need investigation.

Possible follow-up checks include inventory availability, pricing, promotions, customer demand, local events, and competitor activity. These are investigation ideas rather than confirmed causes.

## Business Recommendations
- Investigate the causes of the performance gap between high- and low-revenue stores.
- Review inventory, pricing, promotions, and local demand for stores with unusually low revenue.
- Investigate the decline in Electronics revenue and monitor the category's weekly performance.
- Use historical baselines to distinguish unusual changes from normal sales variation.
- Run the validation pipeline before generating reports so incomplete or corrupt input is not silently processed.
- Review the weekly summary regularly and assign follow-up actions to the relevant store or category owners.

## How to Run
1. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```
2. Place the notebook and required CSV/JSON input files in the same working directory, using the filenames listed in **Data Sources**.
3. Open `Vigneshbabu_MUC01_notebook.ipynb` in Jupyter Notebook, JupyterLab, or a compatible notebook environment.
4. Run the cells in order, from the beginning.
5. Review the charts, validation results, anomaly checks, category alerts, and final weekly operations summary.

If the notebook uses a local or external API response that is not included with the project, provide the expected JSON file before running those cells.

## Expected Output
- Dataset quality and structure checks.
- Store-level and category-level revenue analysis.
- Monthly and weekday trend analysis.
- Potential revenue anomaly identification.
- Weekly store and category aggregations.
- Category alerts against historical baselines.
- A weekly operations summary with record count and pipeline status.

## Project Details
- **Notebook:** `Vigneshbabu_MUC01_notebook.ipynb`
- **Project:** CBIM Problem Canvas — Retail Sales Pulse
- **Primary stakeholder:** Operations Head / Retail Management

## Notes
- Revenue figures and insights depend on the supplied datasets.
- An anomaly is a signal for investigation, not proof of its cause.
- The pipeline's validation rules should be reviewed before production use, especially around missing fields, invalid values, record-count mismatches, and corrupt JSON.
