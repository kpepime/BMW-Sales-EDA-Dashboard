# BMW Global Sales EDA & Dashboard (2010–2024)

> **Tools:** PostgreSQL & Power BI  
> **Dataset:** 50,000 rows. 11 columns. 7 regions. 15 years  
> **Source:** [Kaggle: BMW Sales 2010–2024](https://www.kaggle.com/datasets/y0ussefkandil/bmw-sales2010-2024)

---

## Links

| | |
|---|---|
| Live Dashboard | [View on Power BI](https://app.powerbi.com/view?r=eyJrIjoiYzU4NmIzNzktYmFiMC00NTQyLWFhNGEtZWI0YjY0MTE4NjBhIiwidCI6IjM1YmEzNjIzLWQzNDgtNDAxMi04OTkwLWMxNWI2YThlNGRkNCJ9) |
| EDA Queries | [01_EDA_queries.sql](https://github.com/Khaythefirst/BMW-Sales-EDA-Dashboard/blob/main/SQL%20(BMW)%20files/01_EDA_queries.sql) |
| Business Questions | [02_Business_questions_queries.sql](https://github.com/Khaythefirst/BMW-Sales-EDA-Dashboard/blob/main/SQL%20(BMW)%20files/02_Business_questions_queries.sql) |
| Power BI File | [BMW GLOBAL SALES DASHBOARD.pbix](https://github.com/Khaythefirst/BMW-Sales-EDA-Dashboard/blob/main/BMW%20GLOBAL%20SALES%20DASHBOARD.pbix) |

---

## Project Overview

This project performs a full exploratory data analysis on BMW's global sales data from 2010 to 2024, with the goal of surfacing actionable insights for sales strategy, model prioritisation, and regional distribution.

Three analytical dimensions are covered:

- **Sales & Revenue Trends**: year-over-year performance, cyclical patterns, peak and trough years
- **Model & Fuel Type Performance**: which models and fuel types drive the most revenue and volume
- **Regional Performance**: how BMW performs across 7 regions and which model–fuel combinations lead in each market

All data exploration and transformation was performed in PostgreSQL. Findings are presented in an interactive 3-page Power BI dashboard.

---

## Dashboard Preview

![BMW Global Sales Dashboard](https://github.com/user-attachments/assets/4a19cda5-f6e0-4587-8048-c13bef3e1fc1)

---

## Data Structure

| Column | Type | Description |
|---|---|---|
| `Model` | Text | BMW model name (e.g. 7 Series, X1, i8) |
| `Year` | Integer | Sales year (2010–2024) |
| `Region` | Text | Geographic sales region (7 regions) |
| `Color` | Text | Vehicle colour |
| `Fuel_type` | Text | Hybrid / Petrol / Diesel / Electric |
| `Transmission` | Text | Manual / Automatic |
| `Engine_size_L` | Numeric | Engine displacement in litres |
| `Mileage_KM` | Numeric | Vehicle mileage in kilometres |
| `Price_USD` | Numeric | Sale price in USD |
| `Sales_Volume` | Integer | Units sold |
| `Sales_Classification` | Text | Volume tier classification |

> No duplicates or null values were found in the raw dataset. All columns were standardised for consistency before analysis.

---

## Key Findings

### Sales & Revenue Trends

BMW's sales followed a cyclical pattern across the 15-year period, with meaningful peaks and recoveries rather than steady linear growth.

- **2022 was the peak year**, $1.34 trillion in revenue and 17.9 million units sold, the strongest performance in the dataset
- **2023 was the weakest year**, $1.22 trillion in revenue and 16.2 million units, a sharp contraction following the 2022 high
- **2020 also saw a significant drop**, consistent with the global disruption that year
- **2024 showed strong recovery** after the 2023 trough, demonstrating recurring resilience
- The YoY pattern suggests BMW's sales are sensitive to external macro conditions but consistently recover, no year represents a permanent decline

### Model & Fuel Type Performance

| Metric | Leader | Value |
|---|---|---|
| Top model by revenue | 7 Series | $1.79 trillion |
| Top model by units sold | 7 Series | 23.79 million units |
| Years in top 5 | 7 Series | 11 of 15 years |
| Top fuel type by revenue | Hybrid | $4.82 trillion |
| Weakest model | M3 | Lowest in both sales and revenue |

- The **7 Series** is BMW's single strongest performer across every dimension — revenue, volume, and consistency
- Within the 7 Series, **hybrid variants lead** at 6.2 million units, followed by diesel (6.1M), petrol (5.8M), and electric (5.7M)
- **Hybrid vehicles dominate across all fuel types**, generating more total revenue than petrol, diesel, or electric combined
- The top 5 models, 7 Series, 3 Series, i8, X1, and 5 Series, account for a disproportionate share of total revenue

### Regional Performance

| Region | Revenue Share | Units Sold | Top Model | Top Fuel Type |
|---|---|---|---|---|
| Asia | 17.10% | 42.97M | X1 | Hybrid |
| Europe | 16.77% | 42.56M | i8 | Hybrid |
| North America | 16.74% | 42.40M | 7 Series | Electric |
| Middle East | 16.66% | 42.33M | 7 Series | Petrol |
| South America | 16.38% | 41.55M | X6 | Diesel |
| Africa | 16.35% | 41.57M | 5 Series | Petrol |

- Revenue distribution is **remarkably balanced** across all six regions, the gap between highest (Asia, 17.1%) and lowest (Africa, 16.35%) is less than one percentage point
- Despite similar revenue shares, **model and fuel type preferences diverge sharply by region**, reflecting differences in economic context, infrastructure, and consumer behaviour
- Hybrid dominance is concentrated in **Asia, Europe, and North America**, higher-income markets with stronger EV infrastructure
- **Petrol and diesel hold their ground** in the Middle East, Africa, and South America — markets where hybrid infrastructure is less developed

---

## Recommendations

**1. Match fuel type distribution to regional economic context**
Hybrid models lead in Asia, Europe, and North America. Pushing hybrids into South America and Africa before infrastructure supports them risks unsold inventory. BMW should scale hybrid marketing in regions where it already leads, and reinforce petrol and diesel positioning where those fuel types dominate.

**2. Protect and extend the 7 Series franchise**
With $1.79 trillion in lifetime revenue and consistent top-5 presence across 11 years, the 7 Series is BMW's most reliable revenue engine. Any decline in 7 Series performance should trigger immediate investigation, it is not replaceable in the short term.

**3. Investigate the M3's underperformance**
The M3 ranks last in both sales and revenue despite being a flagship performance model. This may reflect pricing, positioning, or distribution gaps. A targeted diagnostic by region and year could identify whether this is a global issue or concentrated in specific markets.

**4. Use 2022 as the performance benchmark, not 2020 or 2023**
Both 2020 and 2023 were outlier downturns. Planning against average performance across the full 15-year period — anchored to the 2022 peak as the realistic ceiling — gives a more defensible strategic baseline than using trough years.

---

## Repository Structure

```
BMW-Sales-EDA-Dashboard/
├── SQL (BMW) files/
│   ├── 01_EDA_queries.sql # Data exploration — structure, distributions, trends
│   └── 02_Business_questions_queries.sql # Targeted business questions
├── BMW GLOBAL SALES DASHBOARD.pbix # Power BI file (download to interact)
├── Dashboard Image.png # Static dashboard preview
└── README.md
```

---

## Tools & Methods

- **PostgreSQL**: data ingestion, standardisation, EDA queries, business question analysis
- **Power BI**: 3-page interactive dashboard, DAX measures, slicers and cross-filtering
- **SQL techniques used**: window functions (`RANK()`, `LAG()`, `OVER()`), CTEs, conditional aggregation, YoY change calculations, regional segmentation
