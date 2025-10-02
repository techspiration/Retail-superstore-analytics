📊 Project Overview
This Power BI dashboard transforms retail superstore data into actionable business intelligence across six analytical dimensions. Built to support data-driven decision-making for retail operations, marketing strategy, and inventory management.

🎯 Business Impact

Customer Segmentation: Understand purchasing patterns across demographics and loyalty tiers
Revenue Optimization: Identify high-performing products, categories, and regions
Discount Strategy: Analyze the effectiveness of promotional campaigns on sales volume
Seasonal Planning: Leverage trend analysis for inventory and marketing planning
Store Performance: Compare and benchmark store locations for operational excellence


🗂️ Dashboard Structure

📄 Page 1: Customer Insights and Behaviour

Focus: Understanding customer demographics and purchasing patterns
Visualizations:

Revenue by Age Group - Segment analysis comparing "Younger" vs "Older" customer spending
Revenue by Age and Category - Multi-category breakdown across demographics (Apparel, Electronics, Home & Kitchen)
Revenue by Loyalty Member and Brand - Brand performance (Apple, HP, Levi's) analyzed by loyalty membership status
Yearly Revenue by Category - 6-year trend analysis (2018-2023) showing category performance evolution

Key Insights:

Younger demographic generates higher revenue volumes
Electronics consistently outperforms other categories
Loyalty program members show distinct brand preferences
Clear seasonal patterns in category performance


📄 Page 2: Product and Category Performance

Focus: Deep-dive into product mix and category analysis
Visualizations:

Price Analysis by Store and Category - Comparative pricing strategy across Express and Supermarket formats
Regional Revenue by Sub-Category (Bottom 3) - Geographic underperformers (Shirts, Furniture, Jeans) across East, North, South, West
Regional Revenue by Sub-Category (Top 3) - Geographic winners (Decor, Laptop, Cookware) by region
Lowest 3 Product Performers - Identifying bottom SKUs: HP Accessories, Samsung Shirts, Zara Shirts
Top 3 Product Performers - Showcasing star products: Prestige Decor, Levi's Cookware, Apple Mobile

Strategic Value:

Store format pricing optimization opportunities
Regional product assortment recommendations
SKU rationalization insights
Focus areas for promotional investment


📄 Page 3: Store and Regional Performance

Focus: Geographic and store-level operational analysis
Visualizations:

Revenue by Store Type - Express vs Supermarket format performance comparison (~30M vs ~24M)
Revenue by Store and Category - Category mix analysis by store format
Monthly Revenue by City - Granular performance tracking across 7 major cities (Ahmedabad, Bangalore, Chennai, Delhi, Hyderabad, Kolkata, Mumbai, Pune)

Operational Intelligence:

Store format effectiveness by market
City-level seasonality patterns
Category affinity by location type
Expansion and optimization opportunities


📄 Page 4: Discount Impact Analysis

Focus: Promotional effectiveness and discount strategy optimization
Visualizations:

Orders by Loyalty & Discount Type - Cross-analysis of loyalty status with HIGH/LOW discount responsiveness
Orders by Product & Discount Type - Product-level discount effectiveness (Dell Shirts, Apple Jackets, Levi's Jeans, Prestige Decor)
Quantity Sold by Discount(%) - Optimal discount threshold identification showing volume response curve (0-30% range)

Pricing Insights:

Loyalty members respond differently to discount levels
Product categories have varying discount elasticity
Sweet spot identification for promotional depth
Quantity lift analysis by discount percentage


📄 Page 5: Market Trends and Seasonality

Focus: Temporal patterns and forecasting intelligence
Visualizations:

OrderID Analysis by YEAR - Multi-year trend showing dramatic decline (2022) and recovery (2023-2024)
OrderID Analysis by MONTH & CATEGORY - Granular monthly patterns across Apparel, Electronics, and Home & Kitchen with distinct seasonality

Forecasting Power:

Clear identification of market disruption period
Recovery trajectory validation
Category-specific seasonal peaks
Planning cycles for inventory and marketing


📄 Page 6: Sales and Revenue Performance

Focus: Executive summary and financial performance
Visualizations:

Annual Net Revenue by Product Category - 3-year comparison (2022-2024) across all categories
Monthly Net Revenue vs Discount(%) - Correlation analysis between discount depth and revenue impact
Net Revenue Contribution by Discount Type - LOW (53.4%) vs HIGH (46.6%) discount contribution split
Net Revenue by Brand Across Store Types - Brand performance segmentation by retail format (Levi's, Prestige, Sony)
Store-wise Net Revenue Performance (Top 3) - Champions: Ahmedabad, Chennai Store, Ahmedabad Express
Store-wise Net Revenue Performance (Bottom 3) - Focus areas: Hyderabad Store, Ahmedabad Supermarket, Delhi Store 3

Executive Summary Metrics:

Overall revenue trend trajectory
Discount strategy ROI
Store ranking and benchmarking
Brand contribution analysis


🎨 Design Excellence

Color Palette Strategy

Customer Page: Warm pink/coral tones for demographic warmth
Product Page: Professional blue gradient for analytical depth
Store Page: Fresh green tones for operational vitality
Discount Page: Soft peach/orange for promotional energy
Trends Page: Dark navy for sophisticated forecasting
Sales Page: Neutral beige/burgundy for executive polish

UX Features

Consistent header styling across all pages
Clear visual hierarchy with bordered sections
Strategic use of negative space
Color-coded categories for quick scanning
Mobile-friendly layout considerations


🔧 Technical Specifications

Data Model

Primary Dataset: Retail Superstore transactional data
Date Range: 2018-2024 (6+ years of historical data)
Geographic Coverage: 7+ major Indian cities
Product Hierarchy: Category → Sub-category → Brand → Product
Customer Dimensions: Age group, Loyalty status, Geographic location

Key DAX Measures
dax// Net Revenue Calculation
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
Performance Optimization

Star schema data model implementation
Optimized relationships with single-direction filtering
Calculated columns minimized in favor of measures
Aggregation tables for large datasets
Query folding enabled for all transformations


📈 Key Business Insights
🎯 Customer Insights

Younger demographic contributes the majority of revenue
Loyalty members show 15-20% higher average transaction value
Brand affinity varies significantly between loyalty tiers
Electronics category shows highest growth trajectory

💰 Revenue Drivers

Express format outperforms Supermarket by ~20% in revenue density
Top 3 cities (Ahmedabad, Chennai, Bangalore) account for 60%+ of revenue
Prestige and Levi's brands are consistent top performers across locations
Category mix varies significantly by store format

🏷️ Discount Strategy

Optimal discount range: 15-20% for maximum quantity lift
Loyalty members less sensitive to high discounts
LOW discount tier generates 53.4% of net revenue despite volume focus
Product categories respond differently to promotional intensity

📊 Seasonal Patterns

Peak months: March, June, November-December
Q4 surge consistent across all categories
Electronics shows less seasonality than Apparel/Home & Kitchen
Clear post-pandemic recovery trend (2023 onwards)


🚀 Getting Started
Prerequisites

Power BI Desktop (Latest version recommended)
Windows 10/11 or Power BI Service access
Minimum 8GB RAM for optimal performance

Installation

Clone the repository

bash   git clone https://github.com/yourusername/retail-superstore-analytics.git
   cd retail-superstore-analytics

Open the dashboard

Navigate to the dashboard/ folder
Double-click Retail_Superstore_Datasett.pbix
Power BI Desktop will launch automatically


Refresh data (if using your own dataset)

Click Transform Data > Data Source Settings
Update the file path to your dataset location
Click Refresh to load the latest data


Explore interactivity

Use slicers and filters on each page
Click on visual elements for cross-filtering
Navigate between pages using the tab bar