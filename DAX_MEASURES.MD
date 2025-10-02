// Net Revenue Calculation
NetRevenue = 
SUM(Sales[Revenue]) - SUM(Sales[Discount])

// Year-over-Year Growth
YoY Growth % = 
VAR CurrentYear = [Total Revenue]
VAR PreviousYear = 
    CALCULATE(
        [Total Revenue],
        SAMEPERIODLASTYEAR('Date'[Date])
    )
RETURN
    DIVIDE(CurrentYear - PreviousYear, PreviousYear, 0)

// Discount Impact Analysis
Discount Effectiveness = 
DIVIDE(
    [Quantity Sold],
    [Total Orders],
    0
) * 100

// Customer Segmentation
Revenue per Customer = 
DIVIDE(
    [Total Revenue],
    DISTINCTCOUNT(Sales[CustomerID]),
    0
)

// Store Performance Ranking
Store Rank = 
RANKX(
    ALL(Stores[StoreName]),
    [Net Revenue],
    ,
    DESC,
    DENSE
)