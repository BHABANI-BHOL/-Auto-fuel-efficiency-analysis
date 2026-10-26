# -Auto-fuel-efficiency-analysis
A data analysis pipeline evaluating vehicle fuel efficiency (MPG), examining the relationship between car weights, cylinder counts, origins, and efficiency trends with visualizations and an Excel dashboard.

# Auto Fuel Efficiency Analysis 🚗⛽

A comprehensive data science project analyzing vehicle fuel efficiency trends, correlations, and performance metrics. This repository includes raw and cleaned datasets, automated Python analysis scripts, high-resolution visualizations, summary metrics, and an Excel dashboard.

---

## 📊 Project Structure

```text
auto-fuel-efficiency-analysis/
│
├── analysis.py              # Main Python script for data processing and analysis
├── requirements.txt         # Required Python packages and dependencies
├── README.md                # Project documentation
│
├── data/                    # Dataset directory
│   ├── cars_raw.csv         # Raw, unprocessed vehicle dataset
│   └── cars_clean.csv       # Cleaned and preprocessed dataset
│
├── charts/                  # Generated data visualizations
│   ├── 01_mpg_trend_by_origin.png
│   ├── 02_weight_vs_mpg.png
│   ├── 03_mpg_by_cylinders.png
│   ├── 04_high_efficiency_share.png
│   └── 05_correlation_heatmap.png
│
└── output/                  # Final deliverables and reports
    ├── metrics.json         # Summary statistics and calculated metrics
    └── Auto_Efficiency_Dashboard.xlsx # Excel-based analytical dashboard
