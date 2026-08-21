# Northwind Outdoor Supply Operations Dataset

Northwind Outdoor Supply is a regional outdoor gear retailer operating in the southeastern United States, with fulfillment warehouses in Hickory NC, Asheville NC, Charlotte NC, and Greenville SC. The company sells across four channels — Retail Store, Online, Phone, and Marketplace — serving individual consumers, corporate accounts, guide services, and school programs.

## File Inventory

| File | Format | Records | Description |
|------|--------|---------|-------------|
| customers.csv | CSV | 2,600 | Customer accounts with segment, region (geographically correct), loyalty tier, and contact info |
| orders.csv | CSV | 15,000 | Orders with state-appropriate tax rates, channel-correct timestamps, and resolved statuses |
| order_items.csv | CSV | ~52,000 | Line items with quantity, unit price, discount, and line total (math verified) |
| products.csv | CSV | 240 | Product catalog with cost, retail price, weight, and vendor link |
| product_catalog.json | JSON | 240 | Extended product data with tags, season attributes, and online availability |
| inventory.csv | CSV | 525 | Warehouse-level stock with reorder tracking and replenishment status |
| warehouses.csv | CSV | 4 | Warehouse reference: Hickory, Asheville, Charlotte, Greenville |
| employees.csv | CSV | 60 | Employee roster with role/department aligned, unique names, and active date ranges |
| vendors.csv | CSV | 30 | Vendor directory with unique names and active status |
| support_tickets.csv | CSV | 4,200 | Support tickets with realistic resolution times, category skew, and timestamps |
| support_notes.txt | TXT | 8,395 | Agent case notes with category-appropriate content and agent attribution |
| website_analytics.tsv | TSV | 35,000 | Web events following correct funnel logic; device/campaign distributions realistic |
| audit.log | LOG | 18,000 | System audit trail Jan–Dec 2025; business-hours weighted; active employees only |
| monthly_sales_report.docx | DOCX | — | FY2025 Annual Operations Report (January–December 2025) |
| q1_financial_summary.pdf | PDF | — | FY2025 Annual Financial Summary with full-year metrics and category breakdown |

## Date Range

Operational data covers **January 2025 – December 2025**. Customer accounts span **2024–2025**.

## Key Relationships

- `orders.customer_id` → `customers.customer_id`
- `orders.employee_id` → `employees.employee_id`
- `order_items.order_id` → `orders.order_id`
- `order_items.product_id` → `products.product_id`
- `products.vendor_id` → `vendors.vendor_id`
- `inventory.product_id` → `products.product_id`
- `inventory.warehouse_id` → `warehouses.warehouse_id`
- `product_catalog.product_id` → `products.product_id`
- `website_analytics.product_id` → `products.product_id`
- `audit_log.employee_id` → `employees.employee_id`

## Notes

Tax rates are state-appropriate: NC 7.00%, SC 8.00%, TN 9.50%, VA 5.70%. Free shipping applies to orders over $75; smaller non-retail orders carry a flat shipping fee. Financial math is verified: line totals = quantity × unit_price × (1 − discount_rate); order total = subtotal + tax + shipping.
