# Automotive Fuel Efficiency & Performance Analysis

**Tools:** Python (Pandas, NumPy, Matplotlib) | Excel (formula-driven dashboard, native charts)
**Data:** 406 vehicles, model years 1970-1982 (public "cars" dataset, shipped with the `vega_datasets` package, originally from StatLib / UCI Auto-MPG)

## Business question
What drives a car's fuel efficiency, how did efficiency change between 1970 and 1982, and how do USA, Japanese and European manufacturers compare?

## Approach
1. **Data cleaning**: removed 8 rows with no MPG (the target metric), imputed 6 missing horsepower values with the median of the same cylinder group, parsed dates into model year, standardised brand names (e.g. `chevy` -> `chevrolet`, `vw` -> `volkswagen`, `maxda` -> `mazda`), checked for duplicates (none). 406 -> 398 analysis-ready rows.
2. **Feature engineering**: power-to-weight ratio (HP per 1,000 lbs), efficiency class (Low <20 / Medium 20-30 / High 30+ MPG), model-year era bands, high-efficiency flag.
3. **Analysis**: group aggregations by origin, cylinders, year and era; correlation matrix; linear regression of MPG on weight.
4. **Visualisation**: 5 charts in `charts/`, built with a colour-blind-safe palette.
5. **Excel dashboard** (`output/Auto_Efficiency_Dashboard.xlsx`): KPI cards, origin / year / cylinder tables built with `COUNTIFS`, `AVERAGEIFS` and `COUNTIF` formulas that recalculate live from the Data sheet, plus native line and bar charts.

## Key findings
| Finding | Result |
|---|---|
| Average fleet MPG | **23.5** |
| Efficiency by origin | **Japan 30.5 MPG**, Europe 27.9, USA 20.1 (Japan ~52% higher than USA) |
| Models reaching 30+ MPG | **Japan 59.5%**, Europe 31.4%, USA 9.2% |
| Efficiency trend | Average MPG rose from **17.7 (1970) to 31.0 (1982), about +75%** |
| Weight is the strongest driver | Correlation with MPG **-0.83**; each extra **1,000 lbs costs about 7.7 MPG**; weight alone explains ~69% of MPG variation (R-squared 0.69) |
| Light vs heavy cars | Lightest quartile averages **32.3 MPG** vs **14.8 MPG** for the heaviest quartile |
| Engine size | 4-cylinder **29.3 MPG**, 6-cylinder 20.0, 8-cylinder 15.0 |
| Brands (5+ models) | Highest: Honda 33.8 MPG. Lowest: Chrysler 17.3 MPG |

## Recommendations
- Weight reduction is the most effective lever for efficiency; power and engine size move together with weight, so they largely act through it.
- USA models lagged the others in every era but closed part of the gap after 1977 (30+ MPG share: 0% -> 4% -> 24%).

## Limitations
- The dataset has no model-year 1981 records, and yearly sample sizes range from 27 to 60 vehicles, so single-year averages (e.g. 1980) are noisy. Trends are more reliable than individual years.
- Correlation is not causation; weight, engine size and horsepower are strongly related to each other (r above 0.85).
- Fuel prices, vehicle prices and sales volumes are not in the data, so no revenue or cost conclusions are drawn.

## Project structure
```
analysis.py                         full pipeline (run this)
requirements.txt
data/cars_raw.csv                   original data
data/cars_clean.csv                 cleaned data with engineered features
charts/*.png                        5 visualisations
output/Auto_Efficiency_Dashboard.xlsx   formula-driven Excel dashboard
output/metrics.json                 every figure quoted above
```

## How to run
```
pip install -r requirements.txt
python analysis.py
```
