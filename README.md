# ⚡ EV Market Intelligence Dashboard

A complete **Electric Vehicle market analysis project** featuring a raw dataset with real-world data quality challenges and an interactive Power BI dashboard covering 20 brands across 2020–2026.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Data Analysis](https://img.shields.io/badge/Data%20Analysis-3B82F6?style=for-the-badge&logo=databricks&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)

---

## 📋 Project Overview

This project analyzes the global EV market using a **2,250-row dataset** spanning **20 manufacturers**, **6 countries**, and **4 market segments**. The dataset intentionally contains data quality issues — duplicates, near-duplicates, and inconsistencies — making it a realistic data cleaning and analysis exercise.

### What's Inside

| File | Description |
|------|-------------|
| `EV_Data_Raw.csv` | Raw dataset (2,250 rows) with duplicates, near-duplicates & casing issues |
| `EV_Market_share_dashbord.pbix` | Interactive Power BI dashboard with market analysis |

---

## 📊 Dataset Schema

The dataset contains **24 columns** across these categories:

### Vehicle Identity
`brand` · `model` · `year` · `variant`

### Pricing & Market
`price_usd` · `market_segment` · `country_of_origin` · `annual_sales_units`

### Battery & Range
`battery_capacity_kwh` · `range_miles` · `charging_speed_kw`

### Performance
`acceleration_0_60_mph` · `top_speed_mph` · `horsepower` · `torque_nm`

### Design & Safety
`drive_type` · `body_type` · `seating_capacity` · `cargo_volume_cubic_ft` · `weight_kg` · `safety_rating` · `autopilot_level` · `warranty_years`

### Customer
`customer_rating`

---

## 🧹 Data Quality Challenges

The raw dataset includes intentional data quality issues for cleaning practice:

| Issue Type | Count | Example |
|-----------|-------|---------|
| Exact duplicate rows | ~120 | Identical rows appearing twice |
| Near-duplicate rows | ~80 | Same car, price off by 1–2%, sales ±500 |
| Casing inconsistencies | ~50 | `'bmw'`, `'TESLA'`, `' BYD'`, `'Lucid '` |

### Recommended Cleaning Steps

1. **Trim whitespace** from brand, model, and country columns
2. **Standardize casing** (title case for brands)
3. **Remove exact duplicates** using all key columns
4. **Flag near-duplicates** using brand + model + year + variant grouping
5. **Validate ranges** — check for outliers using IQR method

---

## 🔍 Analysis Areas

This dataset supports analysis across 10+ dimensions:

- **Market Overview** — Brand market share, segment distribution, country comparison
- **Pricing & Value** — Price trends by year/segment, price-per-mile-of-range, value positioning
- **Range & Efficiency** — Miles per kWh, weight vs range, drivetrain impact
- **Performance** — Acceleration tiers, horsepower-per-dollar, performance classification
- **Sales & Demand** — Top sellers, growth trajectories, price-sales correlation
- **Customer Satisfaction** — Rating drivers, safety-rating-to-sales relationship
- **Competitive Intelligence** — US vs China vs Germany vs Korea head-to-head
- **Charging Infrastructure** — Charging speed tier analysis
- **Body Type & Drivetrain** — SUV vs Sedan vs Truck preferences by segment
- **Composite Scoring** — Weighted "Best Buy" index combining range, rating, safety, value

---

## 🚀 Getting Started

### Power BI Dashboard

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
2. Open `EV_Market_share_dashbord.pbix`
3. Explore the interactive visuals with slicers and filters

### Working with the Raw Data

```python
import pandas as pd

df = pd.read_csv('EV_Data_Raw.csv')
print(f"Raw rows: {len(df)}")

# Clean: strip whitespace & standardize casing
df['brand'] = df['brand'].str.strip().str.title()
df['country_of_origin'] = df['country_of_origin'].str.strip().str.title()

# Remove exact duplicates
df_clean = df.drop_duplicates()
print(f"After dedup: {len(df_clean)}")
```

---

## 📈 Brands Covered

| Country | Brands |
|---------|--------|
| 🇺🇸 US | Tesla, Rivian, Lucid, GM/Chevrolet, Fisker, Ford |
| 🇨🇳 China | BYD, NIO, Xiaomi |
| 🇩🇪 Germany | BMW, Mercedes, Volkswagen, Audi, Porsche |
| 🇰🇷 South Korea | Hyundai, Kia |
| 🇯🇵 Japan | Toyota, Honda |
| 🇸🇪 Sweden | Volvo, Polestar |

---

## 🛠️ Tools Used

- **Power BI Desktop** — Dashboard creation and interactive visualization
- **Python (Pandas)** — Data cleaning and transformation
- **SQL** — Analytical queries
- **DAX** — Power BI measures and calculated columns

---

## 📄 License

This project is open source and available for educational and portfolio purposes.

---

*Built as a data analytics portfolio project*
