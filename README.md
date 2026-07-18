# DHL Supply Chain Africa — Revenue & Customer Analytics Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Excel](https://img.shields.io/badge/Microsoft%20Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![DAX](https://img.shields.io/badge/DAX-D40511?style=for-the-badge&logoColor=white)

## Project Overview

An interactive two-page Power BI dashboard analyzing shipment revenue performance and customer behavior for DHL Supply Chain Africa operations across 7 origin cities and 8 destination cities spanning January 2023 to June 2024.

This is a portfolio project built on a realistic fictional dataset modeled after DHL's African logistics operations.

---

## Dashboard Preview

### Page 1 — Revenue Performance
<img width="1600" height="569" alt="Dashboard_Page1" src="https://github.com/user-attachments/assets/a71d17e5-0a6a-4d5b-adf3-fd9b53814f65" />


### Page 2 — Customer Behavior Analysis
<img width="1600" height="567" alt="Dashboard_page2" src="https://github.com/user-attachments/assets/12bc0ccd-6036-4f26-9ac4-c1f1751cb679" />


---

## Dashboard Pages

### Page 1 — Revenue Performance
Tracks revenue trends, service type breakdown, and top-performing routes.

**Key Metrics:**
- Total Revenue
- Total Shipments
- Average Revenue per Shipment
- Revenue vs Target

**Visuals:**
- Monthly Revenue Trend (Line Chart)
- Revenue by Service Type (Clustered Bar Chart)
- Top 10 Routes by Revenue (Clustered Bar Chart)
- Revenue by Origin City (Clustered Bar Chart)

**Slicers:** Year | Service Type | Quarter

---

### Page 2 — Customer Behavior Analysis
Explores customer segmentation, repeat patterns, and industry distribution.

**Key Metrics:**
- Total Customers
- Repeat Customer Rate
- B2B Shipments
- B2C Shipments

**Visuals:**
- B2B vs B2C Breakdown (Donut Chart)
- Repeat vs One-Time Customers (Donut Chart)
- Shipments by Industry (Clustered Bar Chart)
- Shipment Volume by Month (Line Chart)
- Average Order Value by Segment (Stacked Column Chart)

**Slicers:** Customer Segment | Delivery Status | Industry

---

## Dataset

The dataset was generated specifically for this project and contains **1,200 rows** across **15 columns** covering 18 months of fictional DHL shipment data.

| Column | Description |
|---|---|
| shipment_id | Unique shipment identifier |
| date | Shipment date |
| customer_id | Unique customer identifier |
| customer_segment | B2B or B2C |
| industry | Customer industry sector |
| service_type | Express, Freight, eCommerce Logistics, Cold Chain, Customs Brokerage |
| origin_city | City of origin (Lagos, Accra, Nairobi, Cairo, etc.) |
| destination_city | Destination city (London, Dubai, New York, etc.) |
| route | Full origin to destination route |
| weight_kg | Shipment weight in kilograms |
| revenue_usd | Revenue generated in USD |
| delivery_status | Delivered, In Transit, Delayed, Returned |
| is_repeat_customer | Whether the customer has shipped before |
| monthly_revenue_target_usd | Monthly revenue target |

---

## Tools & Technologies

- **Power BI Desktop** — Dashboard design and visualization
- **DAX** — Custom measures and calculations
- **Microsoft Excel** — Data source
- **Python (Pillow, openpyxl)** — Dataset generation and formatting

---

## DAX Measures

```dax
Total Revenue = SUM('Shipment Data'[revenue_usd])

Total Shipments = COUNTROWS('Shipment Data')

Avg Revenue per Shipment = AVERAGE('Shipment Data'[revenue_usd])

Revenue vs Target =
SUM('Shipment Data'[revenue_usd]) -
SUM('Shipment Data'[monthly_revenue_target_usd])

Repeat Customer Rate =
DIVIDE(
    COUNTROWS(FILTER('Shipment Data', 'Shipment Data'[is_repeat_customer] = "Yes")),
    COUNTROWS('Shipment Data')
) * 100

Total Customers = DISTINCTCOUNT('Shipment Data'[customer_id])

B2B Shipments =
COUNTROWS(FILTER('Shipment Data', 'Shipment Data'[customer_segment] = "B2B"))

B2C Shipments =
COUNTROWS(FILTER('Shipment Data', 'Shipment Data'[customer_segment] = "B2C"))
```

---

## Key Insights

- **Freight** is the highest revenue-generating service type at **$1.34M**
- **Cairo to Shanghai** is the top revenue route at **$57K**
- **Lagos** generates the highest revenue among all origin cities at **$0.30M**
- **52%** of customers are repeat customers, with B2B driving most repeat business
- **Manufacturing** is the top industry by shipment volume with **196 shipments**
- B2B and B2C average order values are very similar — **$1,589 vs $1,560** — suggesting consistent pricing across segments
- Revenue is **below monthly targets**, indicating an opportunity to optimize high-value service types like Freight and Cold Chain

---

## Color Theme

| Element | Color | Hex |
|---|---|---|
| Bar Charts | DHL Red | #D40511 |
| Line Charts | DHL Yellow | #FFCC00 |
| Secondary Red | Coral | #FF6B6B |

---

## How to Use

1. Download the `DHL_Supply_Chain_DashBoard.pbix` file
2. Open with **Power BI Desktop** (free download from Microsoft)
3. Dataset is embedded — no additional files needed
4. Use slicers to filter by Year, Service Type, Quarter, Segment, Delivery Status, or Industry

---

## Author

**Loveth Adams**

Data Analyst

*This is a portfolio project. The dataset is fictional and created solely for demonstration purposes.*
