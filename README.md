# Part 1: Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

The objective of this project was to clean, validate, and prepare retail order data for business analysis and reporting. The raw dataset contained various data quality issues including inconsistent text formatting, mixed date formats, duplicate records, missing values, invalid discounts, and order status inconsistencies. A cleaned and validated dataset was created along with supporting reports and pivot-based business summaries.

---

# Dataset Description

The dataset contains order-level retail sales transactions and includes information such as:

* Order ID
* Order Date
* Ship Date
* Customer Name
* Customer Segment
* Region
* State
* City
* Category
* Sub-Category
* Ship Mode
* Quantity
* Unit Price
* Cost
* Discount
* Sales
* Profit
* Payment Status
* Order Status

The raw dataset was preserved and all cleaning activities were performed on a separate cleaned version.

---

# Tools Used

* Microsoft Excel
* Excel Formulas
* Pivot Tables
* Conditional Formatting
* Data Validation
* Text to Columns
* Sorting and Filtering

Key Excel Functions Used:

* TRIM()
* SUBSTITUTE()
* IF()
* COUNTIF()
* COUNTBLANK()
* YEAR()
* TEXT()
* DATEVALUE()

---

# Cleaning Steps Performed

### Text Cleaning

* Removed leading and trailing spaces.
* Standardized text formatting and capitalization.
* Corrected inconsistent category and sub-category values.
* Standardized customer, region, state, city, and shipping information.

### Date Cleaning

* Converted mixed date formats into a consistent dd-mmm-yyyy format.
* Validated order and ship dates.
* Flagged invalid dates and shipping records.
* Calculated shipping_delay_days.

### Missing Value Handling

* Missing Region values replaced with "Unknown".
* Missing Ship Mode values replaced with "Unknown".
* Missing Discount values replaced with 0 when valid.

### Duplicate Handling

* Identified exact duplicate records.
* Removed duplicate records where appropriate.
* Flagged conflicting duplicate Order IDs for review.

### Calculated Columns Created

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

# Business Rules Applied

| Rule                        | Action Taken                            |
| --------------------------- | --------------------------------------- |
| Missing Region              | Filled with "Unknown"                   |
| Missing Ship Mode           | Filled with "Unknown"                   |
| Missing Discount            | Replaced with 0 when valid              |
| Negative Discount           | Flagged as Invalid                      |
| Discount Above 50%          | Flagged as Invalid                      |
| Cancelled Orders            | Excluded from completed sales summaries |
| Failed Payments             | Excluded from completed sales summaries |
| Refunded Orders             | Summarized separately                   |
| Ship Date Before Order Date | Flagged as Invalid Shipping Record      |

---

# Summary of Data Quality Issues Found

The following issues were identified during data validation:

* Missing Region values
* Missing Ship Mode values
* Missing Discount values
* Duplicate records
* Duplicate Order IDs
* Invalid discounts
* Mixed date formats
* Missing dates
* Invalid shipping records
* Cancelled orders
* Failed payments
* Refunded transactions

Detailed counts are available in `outputs/data_quality_report.xlsx`.

---

# Summary of Final Pivot Reports

The following pivot summaries were created:

### 1. Sales and Profit by Region

Analysis of revenue and profitability across business regions.

### 2. Sales and Profit by Category and Sub-Category

Comparison of product category performance.

### 3. Order Count by Ship Mode

Distribution of orders across shipping methods.

### 4. Profit Margin by Customer Segment

Comparison of profitability across customer segments.

### 5. Refunded / Cancelled / Failed Orders by Region

Analysis of problematic transactions requiring business review.

### 6. Monthly Sales Trend

Monthly sales performance over time.

Sorting and filtering were applied to selected pivot reports to improve analysis.

---

# Key Business Insights

* Certain regions generated significantly higher sales and profit than others.
* Product category performance varied considerably across sub-categories.
* Standard shipping was the most frequently used shipping method.
* Profit margins differed across customer segments.
* Refunded, cancelled, and failed transactions represented potential operational improvement opportunities.
* Monthly sales trends identified periods of stronger business performance.

---

# Assumptions and Limitations

## Assumptions

* Slash-formatted dates were interpreted as MM/DD/YYYY.
* Dates were standardized to dd-mmm-yyyy format.
* Maximum valid discount was assumed to be 50%.
* Missing Region and Ship Mode values were replaced with "Unknown".
* Cancelled, Failed, and Refunded records were retained for audit purposes.

## Limitations

* Ambiguous date values required assumptions regarding source date format.
* Conflicting duplicate records could not be automatically resolved without business confirmation.
* Data validation was limited to available fields and business rules provided.

---

# Screenshots Included

The repository includes the following screenshots:

| Screenshot File          | Description                              |
| ------------------------ | ---------------------------------------- |
| raw_data_preview.png     | Raw dataset before cleaning              |
| cleaned_data_preview.png | Cleaned dataset with calculated columns  |
| pivot_summary_1.png      | Sales and Profit by Region pivot summary |
| pivot_summary_2.png      | Monthly Sales Trend pivot summary        |

All screenshots are included in the `screenshots/` folder and are readable for evaluation.

---

# Repository Structure

```text
part1_data_cleaning/
├── data/
│   ├── raw_orders.xlsx
│   └── cleaned_orders.xlsx
├── outputs/
│   ├── data_quality_report.xlsx
│   ├── pivot_summary.xlsx
│   └── cleaning_log.md
├── screenshots/
│   ├── raw_data_preview.png
│   ├── cleaned_data_preview.png
│   ├── pivot_summary_1.png
│   └── pivot_summary_2.png
└── README.md
```
