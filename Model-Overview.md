# Data Model Overview

## Tables

### `Sample - Superstore`
The main table containing order and product records used to calculate sales, profit, quantity, and order-level KPIs.

### `Calendar`
A calculated date table generated from the minimum and maximum `Order Date` values. It adds year, month number, month label, year-month label, and quarter columns.

## Relationship

The model uses an active one-to-many relationship:

```text
Calendar[Date]  (1) ───── (*)  Sample - Superstore[Order Date]
```

The calendar table is on the one side; the source table is on the many side. Date slicers and time-intelligence measures should use fields from `Calendar`.

## Modeling choices

- Distinct orders are counted with `DISTINCTCOUNT` on `Order ID`.
- Profit margin is calculated from aggregated profit and sales.
- Prior-period measures use the calendar table to shift the date context.
- Month labels are sorted by month number rather than alphabetically.
- Year-month labels are sorted chronologically.

## Validation checklist

- [ ] The relationship is active and uses the correct date columns.
- [ ] `Order Date` and `Calendar[Date]` use the Date data type.
- [ ] `Calendar[Month]` is sorted by `Calendar[Month Number]`.
- [ ] `Calendar[Year-Month]` is sorted chronologically.
- [ ] Growth measures do not display misleading values when a comparable prior period is unavailable.
