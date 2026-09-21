# AtliQ Hotels Data Analysis

Exploratory data analysis of a hotel chain's booking data using Python (pandas, matplotlib), covering data cleaning, transformation, and business-insight generation.

## Problem Statement

AtliQ Grands owns multiple five-star hotels across four Indian cities (Delhi, Mumbai, Hyderabad, Bangalore). Facing declining market share and revenue in the luxury/business hotel category, the revenue management team wants data-driven insights to guide decision-making — without an in-house analytics team to produce them.

This notebook explores three months of booking data (~134,500 bookings) to answer specific business questions around occupancy, revenue, and guest satisfaction.

## Datasets

Located in `datasets/`:

| File | Description |
|---|---|
| `fact_bookings.csv` | Individual booking-level transactions (~134K rows) |
| `fact_aggregated_bookings.csv` | Daily bookings vs. capacity per property/room type |
| `dim_hotels.csv` | Property metadata (name, category, city) |
| `dim_rooms.csv` | Room category → room class mapping |
| `dim_date.csv` | Calendar dimension (week, weekday/weekend flag) |
| `new_data_august.csv` | Supplementary August booking data used to demonstrate appending new data |

## What the notebook does

1. **Data Import & Exploration** — load the source files, inspect shape, unique values, and distributions.
2. **Data Cleaning** — remove invalid guest counts, remove revenue outliers (3-sigma rule), fill missing capacity values with the median, and drop records where bookings exceed capacity.
3. **Data Transformation** — compute an occupancy percentage column and merge fact/dimension tables into an analysis-ready dataset.
4. **Insights Generation** — answer 10 business questions (see below).
5. **Key Findings** — summarized takeaways at the end of the notebook.

## Key Findings

- **Occupancy by room class:** Presidential (RT4) leads at 59.28%, only marginally ahead of Premium, Elite, and Standard — occupancy is fairly even across room classes.
- **Occupancy by city:** Delhi highest (61.51%), Bangalore lowest (56.33%).
- **Weekday vs weekend:** Weekends run much higher — 72.34% vs. 50.88% on weekdays.
- **Revenue by city:** Mumbai leads by a wide margin (₹668.6M) despite *not* having the best occupancy or rating; Delhi is lowest on revenue (₹294.4M) despite leading on both.
- **Revenue by month:** May 2022 strongest (₹581.8M), June lowest (₹553.9M).
- **Revenue by property:** Atliq Exotica tops the chain (₹320.3M); Atliq Seasons trails badly (₹66.1M).
- **Average rating by city:** Delhi highest (3.78), Bangalore lowest (3.41).
- **Revenue by booking platform:** "Others" dominates (₹699.3M), followed by MakeYourTrip (₹340.8M); direct booking channels (online + offline combined) bring in noticeably less than third-party platforms.

**Takeaway:** Delhi over-indexes on guest satisfaction and occupancy but under-monetizes relative to Mumbai — worth investigating pricing/positioning. Heavy reliance on third-party platforms over direct channels is also worth flagging given acquisition-cost implications.

## How to run

```bash
pip install -r requirements.txt
jupyter notebook hotel_analysis.ipynb
```

Run all cells top to bottom (`Kernel → Restart & Run All`) to reproduce the analysis.

The notebook was developed with Python 3.14.7. Use Python 3.14 or a compatible later
version where the listed dependencies are available.

## Tools

Python, pandas, matplotlib, Jupyter Notebook
