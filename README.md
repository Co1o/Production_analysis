# Solar Manufacturing Production Planning Analytics & Capacity Risk Modeling

This portfolio project transforms a wide-format production planning workbook into an analytics-ready dataset used to evaluate manufacturing capacity utilization, production volatility, customer allocation, and short-term output forecasts.

The repository is designed for **GitHub publication**. All identifying fields in the dataset have been anonymized, and only aggregated planning outputs are included.

## Project Goals
- Convert a manually maintained scheduling workbook into a daily, line-level analytics dataset.
- Measure estimated line utilization and identify unstable planning periods.
- Analyze customer and product mix concentration across time.
- Create a lightweight 7-day operational forecast for planned output.
- Deliver a dashboard that communicates planning risk in a business-friendly format.

## Repository Structure
```text
solar-production-planning-analytics
├── README.md
├── requirements.txt
├── data
│   └── processed
│       ├── production_plan_daily_anonymized.csv
│       ├── daily_line_metrics.csv
│       ├── monthly_customer_summary.csv
│       ├── monthly_line_summary.csv
│       └── next_7d_line_forecast.csv
├── src
│   ├── data_processing.py
│   ├── capacity_metrics.py
│   ├── forecasting.py
│   └── analysis.py
├── dashboard
│   └── app.py
├── notebooks
│   └── 01_project_walkthrough.ipynb
└── reports
    └── production_insights.md
```

## Dataset
The published dataset contains anonymized planning records with the following fields:
- `date`
- `plant_id`
- `customer_id`
- `format_id`
- `cell_spec_id`
- `power_w`
- `line`
- `planned_pcs`
- `planned_mw`

### Anonymization
The following fields were replaced with neutral identifiers before publication:
- plant names → `Plant_XX`
- customer / order names → `Customer_XX`
- module format labels → `Format_XX`
- cell specification labels → `CellSpec_XX`

## Analytics Workflow
1. **Data restructuring**  
   Parse month-based scheduling blocks from the workbook and unpivot daily quantities into a long-format table.

2. **Capacity analytics**  
   Aggregate daily output by production line and estimate utilization against an observed-capacity benchmark.

3. **Risk detection**  
   Use 7-day rolling standard deviation to flag periods with elevated planning volatility.

4. **Customer allocation analysis**  
   Measure total planned MW by customer and track concentration in the order mix.

5. **Short-term forecast**  
   Generate a simple line-level baseline forecast using the trailing 14-day mean.

## Dashboard
Run locally:
```bash
pip install -r requirements.txt
streamlit run dashboard/app.py
```

Dashboard tabs:
- Overview
- Capacity
- Customer Mix
- Risk
- Forecast

## Tech Stack
- Python
- Pandas
- OpenPyXL
- Plotly
- Streamlit

## Example Resume Bullets
**Solar Manufacturing Production Planning Analytics & Capacity Risk Modeling**  
- Built analytics workflows on anonymized solar manufacturing planning data to evaluate capacity utilization, production volatility, and customer allocation across production lines.  
- Developed interactive dashboards and baseline forecasting workflows to identify bottlenecks, monitor planning instability, and support production planning decisions.

## Notes for Public GitHub Use
- The repository contains **anonymized, publication-ready data only**.
- Do not upload the original workbook or any internal file containing unmasked customer names or plant identifiers.


## Included Figures

The `reports/figures/` folder contains export-ready charts for portfolio presentation:

- Monthly planned output (MW)
- Monthly output by line
- Top customers by planned MW
- Daily utilization by line
- Volatility heatmap
- Next 7 days forecast by line
