# Superstore Sales EDA

This project presents an in-depth Exploratory Data Analysis (EDA) of the Superstore Sales dataset. The dataset has been intentionally modified to introduce inconsistencies, missing values, and data quality issues to simulate real-world business data scenarios. The goal is to clean and transform the data, engineer new features, detect trends, and prepare the dataset for potential modeling and decision-making applications.

## Objective

- Clean and preprocess the dataset by identifying and fixing inconsistencies  
- Engineer additional variables for deeper business insight  
- Identify patterns in sales, shipping, discounts, and customer behavior  
- Build visualizations to support business decisions  
- Prepare the data for future modeling tasks (e.g., forecasting or segmentation)

## Dataset Description

- **Rows**: Multiple transaction records  
- **Columns**: 21 fields including numerical, categorical, and datetime variables  
- **Key Columns**:  
  - `Order ID`, `Order Date`, `Ship Date`, `Ship Mode`  
  - `Customer ID`, `Segment`, `Region`, `State`, `Postal Code`  
  - `Product ID`, `Category`, `Sub-Category`, `Product Name`  
  - `Sales Price`, `Quantity`, `Discount`, `Profit`  

> Note: The `Customer Name` field has been masked to protect personally identifiable information (PII).

## Data Cleaning and Transformation

- Removed duplicate records  
- Normalized `Order Date` and `Ship Date` formats  
- Validated year in `Order ID` against `Order Date`  
- Imputed missing values:  
  - `Ship Mode` imputed based on calculated `Days to Ship`  
  - `Quantity` imputed using context-specific logic  
- Standardized postal codes to 5-digit strings  
- Replaced state abbreviations with full names  
- Converted `Sales Price` and `Quantity` to appropriate numeric types  
- Masked customer names for privacy  

## Feature Engineering

New variables were created to enhance the analysis:

- `Original Price`: Price before discounts  
- `Total Sales`: Sales Price × Quantity  
- `Total Profit`: Profit × Quantity  
- `Discount Price` and `Total Discount`  
- `Shipping Urgency`: Categorized based on Days to Ship  
- `Days Since Last Order`: Customer recency  
- Aggregated customer-level metrics (e.g., total sales, quantity, discount)  

## Outlier Detection

- Custom `remove_outliers()` function developed using the 3×IQR rule  
- Applied to `Sales Price` and `Profit` columns  
- 3×IQR was used (rather than 1.5×) due to the high variance in the dataset  

## Customer Segmentation

- Customers segmented into quintiles based on total sales and profit  
- Cross-tabulation of sales and profit quintiles to identify high-value segments  
- Distribution visualizations created to support strategic recommendations  

## Analysis and Visualization Dashboard

### Sales and Profit Analysis

- Top 10 most profitable and loss-generating products  
- Sales vs. Profit correlation and regression trend  
- Joint distribution plots of sales and profit  

### Shipping and Delivery

- Distribution of shipping urgency  
- Profitability by shipping method and shipping duration  
- Regional preference and performance by shipping mode  

### Regional Insights

- Sales and profit by state and region  
- State-level profitability rankings  
- Correlation between state (encoded) and profit  

### Discount and Pricing Strategy

- Discount impact on profitability  
- Comparison of original and discounted prices by category  

### Time Series Analysis

- Trends in sales and profit over time  
- Order frequency by month  
- Year-over-year growth in revenue and profitability  

## Key Insights

- Steep discounts often reduce profitability despite increasing sales volume  
- Urgent and same-day shipping options may affect profit margins  
- A small group of customers contribute disproportionately to overall profit  
- Some states and customer segments are consistently more profitable  

