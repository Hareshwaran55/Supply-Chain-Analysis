# Supply Chain Shipment Operations Analysis (Pandas Project)

A pandas-based data cleaning and analysis project simulating shipment, cost, and delivery-performance data for a multi-region supply chain network. Built for practicing real-world data cleaning, EDA, and advanced pandas techniques (groupby, pivot tables, window functions, time-series analysis).

## 📁 File

[`supply_chain_analysis.py`](supply_chain_analysis.py) (pipeline script) + [`supply_cahin_data.xlsx`](supply_chain_data.xlsx) (raw) → [`supply_chain_data_cleaned.xlsx`](supply_chain_data_cleaned.xlsx) (cleaned output)

## 📊 Dataset Structure

The dataset is a single shipment-level table, **6,000 cleaned rows** (from 6,150 raw rows) across **25+ columns**, covering:

| Field group      | Example columns                                              |
|-------------------|---------------------------------------------------------------|
| Shipment info    | `Shipment_ID`, `Product_ID`, `Product_Category`, `Quantity`   |
| Parties          | `Supplier_ID`, `Supplier_Name` (80 suppliers), `Warehouse_ID` (20 warehouses), `Region` |
| Timeline         | `Shipment_Date`, `Expected_Delivery`, `Actual_Delivery`, `Delay_Days` |
| Cost             | `Unit_Cost`, `Total_Cost`                                      |
| Logistics        | `Shipping_Mode`, `Carrier`, `Delivery_Status`                  |
| Quality          | `Defect_Rate`, `Inspection_Status`, `Supplier_Rating`           |
| Inventory        | `Warehouse_Stock`, `Reorder_Level`                              |
| Payment          | `Payment_Status`                                                |

## 🔑 Headline KPIs

| Metric | Value |
|---|---|
| Total Shipments (cleaned) | 6,000 |
| Total Shipment Cost | ₹4,511.25 Cr |
| Average Delay | 1.92 days |
| On-Time Delivery Rate | 45.7% |
| Distinct Suppliers | 80 |
| Distinct Warehouses | 20 |

## 📈 Key Insights

- **Delivery status:** Of 6,000 shipments, 3,573 (59.6%) were fully **Delivered**, 1,054 (17.6%) were **Delayed**, 749 (12.5%) still **In Transit**, 386 (6.4%) **Returned**, and 238 (4.0%) marked **Lost** — meaning over a fifth of all shipments hit friction beyond a simple delay.
- **Shipping mode:** Volume is nearly evenly split across Air (1,550), Road (1,508), Sea (1,488), and Rail (1,454) shipments — but **Sea generated the highest total cost (₹1,202 Cr)** despite not having the most shipments, while **Road carried the lowest total cost (₹1,060 Cr)** on a similar volume, suggesting Sea shipments skew toward higher-value or bulkier cargo.
- **Carrier performance:** Delhivery handled the most shipments (1,032) and posted the **lowest average delay (1.81 days)**, while Fedex had the **highest average delay (2.06 days)** despite handling fewer shipments (990) — indicating carrier choice measurably affects delivery reliability.
- **Payment status:** Paid (1,989), Overdue (1,937), and Pending (1,924) shipments are nearly evenly split three ways — meaning roughly **two-thirds of all shipment payments are not yet settled** (Overdue + Pending combined), a notable cash-flow signal.
- **Product category:** Packaging leads both in shipment count (1,039) and revenue (₹798 Cr), while Pharmaceutical carries the **highest average defect rate (4.25%)** among all categories — worth flagging for quality review given the sensitivity of pharma goods.
- **Regional split:** East region leads in both shipment count (1,540) and cost (₹1,162 Cr), and also has the **highest average delay (1.97 days)** — the busiest region is also the slowest, hinting at potential capacity strain in East-region logistics.
- **Inspection outcomes:** 2,010 shipments (33.5%) **Failed** inspection versus 1,904 (31.7%) that **Passed**, with the remainder still **Pending** — a fail rate this close to the pass rate signals a quality-control issue worth investigating at the supplier or category level, not just a few isolated incidents.
- **Supplier spread:** Across 80 suppliers, average ratings range from **3.24 to 3.75** (out of 5) — a fairly narrow band, meaning no single supplier stands out as dramatically better or worse; performance gaps are likely driven more by shipping mode and route than by supplier alone.

### Top 5 Suppliers (by average rating, min. 5 shipments)

| Rank | Supplier | Avg. Rating | Shipments |
|---|---|---|---|
| 1 | Orion Industries 50 | 3.75 | 66 |
| 2 | Pacific Components 60 | 3.71 | 70 |
| 3 | Sigma Supplies 17 | 3.70 | 69 |
| 4 | Sigma Supplies 10 | 3.69 | 71 |
| 5 | Metro Manufacturing 39 | 3.69 | 73 |

### Bottom 5 Suppliers (by average rating, min. 5 shipments)

| Rank | Supplier | Avg. Rating | Shipments |
|---|---|---|---|
| 1 | Pacific Components 25 | 3.24 | 69 |
| 2 | Orion Industries 76 | 3.27 | 66 |
| 3 | Sigma Supplies 71 | 3.29 | 77 |
| 4 | Pacific Components 37 | 3.30 | 77 |
| 5 | Apex Industries 52 | 3.34 | 66 |

## ✅ Conclusion

This dataset illustrates a large, multi-region supply network where shipment volume, cost, and delivery reliability don't move in lockstep — Sea shipments cost the most despite average volume, the busiest region (East) is also the slowest, and carrier choice noticeably affects delay outcomes even at similar shipment counts. The near-even split between Paid, Overdue, and Pending payment statuses and the close Failed-vs-Passed inspection split are the two findings most worth acting on operationally: the former as a cash-flow signal, the latter as a quality-control signal, particularly for Pharmaceutical shipments given their higher defect rate. On-time delivery at ~46% leaves substantial room for improvement compared to typical logistics benchmarks, and is a natural next area to drill into by carrier, region, and shipping mode.

## 🛠️ How to Use

1. Place `supply_chain_data.xlsx` in the same folder as `supply_chain_analysis.py`.
2. Run `python supply_chain_analysis.py` to clean the data and generate `supply_chain_data_cleaned.xlsx`.
3. Explore the printed console output for Stage 1–4 results (data understanding, cleaning validation, EDA, advanced pandas).
4. Open `supply_chain_data_cleaned.xlsx` directly in Excel to build your own pivot tables or charts on top of the cleaned data.

## ⚠️ Note

All data is synthetically generated for demonstration/practice purposes and does not represent a real logistics company's shipment records.
