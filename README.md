# Greenweez-logistic-analytics
Logistics analysis and parcel tracking with Google Sheets: delivery metrics, carrier performance, dashboards, and parcel lookup.
# Greenweez Logistics Analytics

A Google Sheets project developed as part of the Workintech **Logistics Data Analysis and Parcel Tracking** challenge.

The project explores order processing times, carrier performance, cancellations, and parcel tracking using a historical dataset from 2021.

## Dashboard

[Open the Google Sheets analysis](https://docs.google.com/spreadsheets/d/1j7uZ3fsD378RecTBezfqxZ--kxIMJY5-5yhGuD_L2yU/edit?usp=sharing)

## Dataset

The source workbook contains **4,199 orders**, four carriers, and three priority levels.

Source fields:
- `parcel_id` and `orders_id`
- `carrier` and `Priority`
- `purchase_date`, `shipping_date`, and `delivery_date`
- `Status`

Order IDs are unique, but parcel IDs repeat. Counts therefore use `orders_id`, and the parcel lookup returns all records matching a parcel ID.

## Analysis

- Calculated shipping, delivery, and total lead times.
- Summarized order counts and average durations by carrier and priority.
- Compared cancellation rates and order shares across carriers.
- Visualized order status distribution.
- Analyzed in-transit orders by purchase date.
- Built an interactive parcel lookup with a message for unmatched IDs.

## Metric Definitions

| Metric | Definition |
|---|---|
| Shipping time | Shipping date − purchase date |
| Delivery time | Delivery date − shipping date |
| Total lead time | Delivery date − purchase date |
| Cancellation rate | Cancelled orders ÷ total orders |

Duration metrics use calendar days. Delivery and total lead-time averages include only records with a delivery date. Missing delivery dates are not replaced with zero.

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

**Chrono Pickup** accounts for the largest order share at **52.1%**. **DPD Pickup** has the highest cancellation rate at **3.93%**, while **Chrono Home** has the lowest at **2.13%**. These descriptive differences do not establish the causes of cancellations.

## Parcel Lookup

In the `parcel_info_page` sheet, enter a parcel ID in **B1** to display matching records.

Examples:
- `1001` returns two records.
- `1004` returns four records.
- An unmatched ID displays a “parcel

- 
