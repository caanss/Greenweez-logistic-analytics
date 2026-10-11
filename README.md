# Greenweez Logistics Analytics

A Google Sheets project developed as part of the Workintech **Logistics Data Analysis and Parcel Tracking** challenge.

This project explores order processing times, carrier performance, cancellations, and parcel tracking using a historical dataset from 2021.

## Dashboard

[Open the Google Sheets analysis](https://docs.google.com/spreadsheets/d/1j7uZ3fsD378RecTBezfqxZ--kxIMJY5-5yhGuD_L2yU/edit?usp=sharing)

To test the parcel lookup, make a personal copy of the workbook and enter a parcel ID in cell **B1** of the `parcel_info_page` sheet.

## Dataset

The source workbook contains **4,199 unique orders**, **3,373 distinct parcel IDs**, four carriers, and three priority levels.

| Field | Description |
|---|---|
| `parcel_id` | Parcel identifier; not unique in this dataset |
| `orders_id` | Unique order identifier |
| `carrier` | Shipping carrier and service |
| `Priority` | High, Medium, or Low |
| `purchase_date` | Purchase date |
| `shipping_date` | Shipping date |
| `delivery_date` | Delivery date; blank for undelivered orders |
| `Status` | Delivered, In Transit, In Progress, or Cancelled |

Repeated parcel IDs can have different order details. These records were retained, and order counts use `orders_id`.

## Analysis

- Calculated shipping, delivery, and total lead times.
- Summarized order counts and average durations by carrier and priority.
- Compared cancellation rates and order shares across carriers.
- Visualized order status distribution.
- Analyzed in-transit orders by purchase date.
- Built a parcel lookup that returns all matching records.

## Metric Definitions

| Metric | Definition |
|---|---|
| Shipping time | Shipping date − purchase date |
| Delivery time | Delivery date − shipping date |
| Total lead time | Delivery date − purchase date |
| Cancellation rate | Cancelled orders ÷ total orders |

All durations use calendar days. Delivery and total lead-time averages include only records with a delivery date. Missing delivery dates are not replaced with zero.

## Key Findings

| Metric | Result |
|---|---:|
| Total orders | 4,199 |
| Average shipping time | 10.17 days |
| Average delivery time | 5.52 days |
| Average total lead time | 15.93 days |
| Cancellation rate | 3.26% |
| Delivered orders | 2,852 |
| In-transit orders | 770 |
| In-progress orders | 440 |
| Cancelled orders | 137 |

Shipping time averages cover all orders, while delivery and total lead-time averages cover delivered orders. These averages should not be added together because their populations differ.

**Chrono Pickup** handles the largest order share at **52.1%**.

| Carrier | Cancellation rate |
|---|---:|
| Chrono Home | 2.13% |
| Chrono Pickup | 3.25% |
| DPD Home | 3.25% |
| DPD Pickup | 3.93% |

DPD Pickup has the highest cancellation rate, while Chrono Home has the lowest. These descriptive differences do not establish the causes of cancellations.

## Parcel Lookup

Enter a parcel ID in **B1** of the `parcel_info_page` sheet.

The lookup uses `FILTER` to return every matching record and `IFNA` to display a message when no match exists.

| Test input | Expected result |
|---|---|
| `1001` | Two matching records |
| `1004` | Four matching records |
| `999999` | “Bu paket kimliği bulunamadı” message |

These cases were tested during workbook development.

## Tools and Skills

- Google Sheets
- Pivot tables and charts
- Date calculations
- Conditional formulas
- `COUNTIF` for repeated-ID counts
- `FILTER` and `IFNA` for parcel lookup
- Data quality checks for missing values, duplicate IDs, and date order

## Limitations

-The workbook represents a historical snapshot, not live shipment tracking.
-Product details and shipment tracking URLs are absent from the source dataset.
-No promised delivery dates or service-level targets are provided, so late-delivery rates cannot be calculated.
-In Progress and Cancelled records also contain shipping dates. Their operational meaning requires clarification.

Data Source

Workintech challenge workbook:

Challenge - Greenweez - parcel data dosyasının kopyası.xlsx
