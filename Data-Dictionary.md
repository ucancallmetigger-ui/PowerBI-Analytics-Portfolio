# Data Dictionary

The report uses the `Sample - Superstore` table. This page covers the fields used directly in the report; it is not a complete inventory of every column in the source file.

| Field | Use in the report | Expected type |
|---|---|---|
| `Order ID` | Distinct order count | Text |
| `Order Date` | Date filtering and time analysis | Date |
| `Sales` | Sales totals and average order value | Decimal number |
| `Profit` | Profit totals and profitability analysis | Decimal number |
| `Quantity` | Total quantity sold | Whole number |
| `Category` | Category comparisons and filtering | Text |
| `Sub-Category` | Product grouping within categories | Text |
| `Product Name` | Product ranking and Top 10 analysis | Text |
| `Region` | Regional comparison and filtering | Text |

## Data preparation

The numeric fields were assigned appropriate numeric types and `Order Date` was set to Date. A separate `Calendar` table was created for date filtering and time-intelligence measures.

## Data limitations

The source is a sample dataset for learning and demonstration. Check the source file's terms before redistributing it. The report does not represent a real company's current sales or financial position.
