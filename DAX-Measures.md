# DAX Measures

This document records the main measures used in the report. Keep it aligned with the definitions in the PBIX if the model changes.

## Core measures

### Total Sales
```DAX
Total Sales = SUM('Sample - Superstore'[Sales])
```

### Total Profit
```DAX
Total Profit = SUM('Sample - Superstore'[Profit])
```

### Total Orders
```DAX
Total Orders = DISTINCTCOUNT('Sample - Superstore'[Order ID])
```

### Profit Margin
```DAX
Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
```
Format as Percentage.

### Average Order Value
```DAX
Average Order Value = DIVIDE([Total Sales], [Total Orders], 0)
```

### Total Quantity
```DAX
Total Quantity = SUM('Sample - Superstore'[Quantity])
```

## Time-based measures

### Previous Month Sales
```DAX
Previous Month Sales =
CALCULATE(
    [Total Sales],
    DATEADD('Calendar'[Date], -1, MONTH)
)
```

### Sales MoM Growth %
```DAX
Sales MoM Growth % =
DIVIDE(
    [Total Sales] - [Previous Month Sales],
    [Previous Month Sales]
)
```
Format as Percentage. The result can be blank when the prior-month value is unavailable or zero.

### Previous Year Sales
```DAX
Previous Year Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)
```

### Sales YoY Growth %
```DAX
Sales YoY Growth % =
DIVIDE(
    [Total Sales] - [Previous Year Sales],
    [Previous Year Sales]
)
```
Format as Percentage. The result can be blank when the comparable prior-year value is unavailable or zero.

## Category margin

### Category Profit Margin
```DAX
Category Profit Margin =
DIVIDE([Total Profit], [Total Sales], 0)
```
Use this measure in a visual grouped by `Category`. The category filter context evaluates sales and profit for each category.

## Calendar table

```DAX
Calendar =
ADDCOLUMNS(
    CALENDAR(
        MIN('Sample - Superstore'[Order Date]),
        MAX('Sample - Superstore'[Order Date])
    ),
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month", FORMAT([Date], "MMM"),
    "Year-Month", FORMAT([Date], "yyyy-MM"),
    "Quarter", "Q" & FORMAT([Date], "Q")
)
```

## Model requirements

- Create an active one-to-many relationship from `Calendar[Date]` to `'Sample - Superstore'[Order Date]`.
- Set `Order Date` and `Calendar[Date]` to the Date data type.
- Sort `Calendar[Month]` by `Calendar[Month Number]`.
- Sort `Calendar[Year-Month]` chronologically.
- Use the calendar table for date-based visuals and time-intelligence calculations.

## Interpretation

- `Profit Margin` is aggregated profit divided by aggregated sales.
- `Average Order Value` is total sales divided by distinct order IDs.
- Growth percentages compare the current filter context with a prior period. The selected dates and other filters affect the result.
