## SUPPLY CHAIN ANALYSIS  


### STEP-1: [EDA & Data Pre-processing](https://github.com/abhinavbhandar/supplychain/blob/main/SupplyChainAnalytics.ipynb)
### STEP-2: [Demand Forecasting(ARIMA)](https://github.com/abhinavbhandar/supplychain/blob/main/Sales_Forecast_ARIMA.ipynb)
### STEP-3: [Dashboard Link](https://app.powerbi.com/view?r=eyJrIjoiMTY4NWVkODEtODQ3Ny00YzkwLWI2MDYtNWIyYTg5OWNhNjM1IiwidCI6IjRjMzMwZTYyLWY1YWEtNDQ4MS04YzVlLTIxZmU0MmFlZDgxYyJ9)

---

### **SUBJECT**  
The client is experiencing a significant decline in sales over the past two months and aims to uncover the root causes. This analysis will target customer churn, future sales trends, and supply chain inefficiencies to optimize operations and enhance customer satisfaction.

---

### **TASK**  
1. Reduce customer churn.  
2. Improve logistics management.  
3. Increase product sales.  
4. Enhance customer satisfaction.  
5. Achieve cost reduction.  

---

### **ACTION**  
1. Utilized the **ARIMA model** to forecast monthly sales for 2018.  
2. Conducted **customer churn analysis** to identify patterns of customer activity and regions with low retention rates.  
3. Performed **logistics analysis** to pinpoint top-performing product categories and inefficiencies.  
4. Investigated the sales decline in **November and December 2017** due to competitive market factors.  
5. Analyzed risks from supplier dependencies and proposed solutions to mitigate disruptions.  
6. Identified and recommended the discontinuation of products with consistently low sales.  

---

### **RESULT**  
1. Sales are forecasted to increase by **5.91%** in 2018.  
2. Retention rates in Africa, Asia, and Oceania are below **40%**, highlighting regions with high churn.  
3. Customer activity peaks at **4 PM and 10 PM**, especially on weekends.  
4. November and December sales dropped due to external competition, notably Alibaba's **Singles Day** event generating $25.3 billion in sales.  
5. Uniform monthly discounts were identified as ineffective; festival or time-limited sales are recommended.  
6. Over **50% of orders** experienced delayed delivery.  
7. Products such as **CDs, baby products, soccer, and basketball items** have low demand and contribute to losses.  

---

### **SOLUTION**  
1. Introduce **festival-based sales** targeting Africa, Asia, and Oceania to boost retention.  
2. Implement **region-specific marketing campaigns** during weekends from **4 PM to 10 PM**.  
3. Diversify suppliers and establish risk assessment protocols to mitigate supply chain disruptions.  
4. Optimize delivery routes to reduce delays.  
5. Discontinue low-demand products like CDs, baby products, soccer, and basketball items.  

---
## Code and Resources Used

**Python version:** 3.10.12  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, pmdarima, statsmodel, warnings, datetime  
**Data Source:** [Kaggle](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis)  
  
---

## Tools and Platforms Used

**Power BI**  
Purpose: For creating interactive dashboards and data visualization to analyze supply chain trends and performance metrics.
Key Features Used: Data import, transformation, DAX calculations, and custom visualization creation.
  
**Google Colab**  
Purpose: For collaborative Python scripting, data preprocessing, statistical analysis, and building predictive models in a cloud-based environment.
Key Features Used: Jupyter notebook interface, GPU/TPU acceleration, and integration with libraries like statsmodels and pandas.
  
**Microsoft Excel**  
Purpose: For preliminary data exploration and manual data cleaning for creating dataset for predictive modeling.
Key Features Used: Functions, conditional formatting, and simple visualizations.

**Git Hub**  
Purpose: Used for hosting project documentation, versioning, and sharing notes related to the project. 

---

## Dataset

Original Dataset: [*LINK*](https://github.com/abhinavbhandar/supplychain/blob/main/DataCoSupplyChainDataset.csv.zip)  
Fact & Dimension Tables: [*LINK*](https://github.com/abhinavbhandar/supplychain/blob/main/Supply%20chain%20tables.rar)  
Forecast Result: [*LINK*](https://github.com/abhinavbhandar/supplychain/blob/main/forecast.csv)  

---

## metadata
|index|Column Name|Non-Null Count|Dtype|Memory Usage|
|---|---|---|---|---|
|Type|Type|180519|object|11405789|
|Days for shipping \(real\)|Days for shipping \(real\)|180519|int64|1444280|
|Days for shipment \(scheduled\)|Days for shipment \(scheduled\)|180519|int64|1444280|
|Delivery Status|Delivery Status|180519|object|12888838|
|Late\_delivery\_risk|Late\_delivery\_risk|180519|int64|1444280|
|Category Id|Category Id|180519|int64|1444280|
|Category Name|Category Name|180519|object|12583709|
|Customer City|Customer City|180519|object|11681264|
|Customer Country|Customer Country|180519|object|11830836|
|Customer Fname|Customer Fname|180519|object|11241887|
|Customer Id|Customer Id|180519|int64|1444280|
|Customer Lname|Customer Lname|180511|object|11320664|
|Customer Segment|Customer Segment|180519|object|11885330|
|Customer State|Customer State|180519|object|10650758|
|Department Name|Department Name|180519|object|11560513|
|Latitude|Latitude|180519|float64|1444280|
|Longitude|Longitude|180519|float64|1444280|
|Market|Market|180519|object|11517193|
|Order City|Order City|180519|object|12365509|
|Order Country|Order Country|180519|object|12771693|
|order date \(DateOrders\)|order date \(DateOrders\)|180519|datetime64\[ns\]|1444280|
|Order Id|Order Id|180519|int64|1444280|
|Order Item Discount|Order Item Discount|180519|float64|1444280|
|Order Item Discount Rate|Order Item Discount Rate|180519|float64|1444280|
|Order Item Product Price|Order Item Product Price|180519|float64|1444280|
|Order Item Profit Ratio|Order Item Profit Ratio|180519|float64|1444280|
|Order Item Quantity|Order Item Quantity|180519|int64|1444280|
|Sales|Sales|180519|float64|1444280|
|Order Profit Per Order|Order Profit Per Order|180519|float64|1444280|
|Order Region|Order Region|180519|object|12570443|
|Order State|Order State|180519|object|13600780|
|Order Status|Order Status|180519|object|12027020|
|Product Card Id|Product Card Id|180519|int64|1444280|
|Product Image|Product Image|180519|object|22916476|
|Product Name|Product Name|180519|object|16629539|
|Product Status|Product Status|180519|int64|1444280|
|shipping date \(DateOrders\)|shipping date \(DateOrders\)|180519|datetime64\[ns\]|1444280|
|Shipping Mode|Shipping Mode|180519|object|12604681|  

---

## Data Cleaning
After loading the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Remove duplicates
*	Drop null values 
*	Made columns for employer provided salary and hourly wages 
*	Convert date columns to datetime format 
*	Standardize text fields 
*	drop unwanted columns 

---

## EDA  
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

| **Shipping Performance Analysis** | **Order Pattern Analysis** |  
|:----------------------------------:|:---------------------------:|  
| ![Shipping Performance](https://github.com/user-attachments/assets/86f23d14-1df2-4e39-b38a-957782ce4164) | ![Order Pattern](https://github.com/user-attachments/assets/039252ad-015f-4f83-b2ef-d1febafa23fe) |  
| **Product Performance Analysis** | **Geographical Analysis** |  
| ![Product Performance](https://github.com/user-attachments/assets/b45bc7cb-2c75-43c9-be8d-d53dad0205b2) | ![Country Performance](https://github.com/user-attachments/assets/bb53f3f6-9ef7-420b-b15e-cc58115bffd0)  


---
### SALES ANALYSIS:  
**SALES KPI:**  

*Total Sales* =  
SUM(fact_orders[Sales])  

*Total Profit* =  
SUM(fact_orders[Order Profit Per Order])  

*Total Cost* =  
[Total Sales] - [Total Profit]  

*Total Orders* =  
DISTINCTCOUNT(fact_orders[Order Id])  

*LastMonthSales* =  
CALCULATE([Total Sales],(DATEADD(fact_orders[Oder Date].[Date] ,-1,MONTH)))  

*MoM Sales %* =  
DIVIDE(
    [Total Sales]-[LastMonthSales]
    ,[LastMonthSales], 0)  

![image](https://github.com/user-attachments/assets/027a52ca-86bb-4ebd-9a54-e8de8c027370)

---

### LOGISTICS ANALYSIS: 
  
**LOGISTICS KPI:**  
*Lead Time* =  
AVERAGEX(
    fact_shipping,
    fact_shipping[Days for shipping (real)]
)  

*Line Fill Rate* =  
DIVIDE(
    CALCULATE(
        COUNTROWS(fact_orders),
        fact_orders[Order Status] = "COMPLETE" || fact_orders[Order Status] = "PENDING_PAYMENT"
    ),
    COUNTROWS(fact_orders)
)  

*OTIF %* =  
DIVIDE(
    CALCULATE(
        COUNTROWS(fact_shipping),
        FILTER(
            fact_shipping,
            fact_shipping[Days for shipping (real)] <= fact_shipping[Days for shipment (scheduled)]
        ),
        FILTER(
            fact_orders,
            fact_orders[Order Status] = "COMPLETE" || fact_orders[Order Status] = "PENDING_PAYMENT"
        )
    ),
    COUNTROWS(fact_shipping)
)  

*Backorder Rate* =  
DIVIDE(
    CALCULATE(
        COUNTROWS(fact_orders),
        fact_orders[Order Status] = "PENDING"
    ),
    COUNTROWS(fact_orders)
)  

![image](https://github.com/user-attachments/assets/24ab8ccc-59c6-410d-9815-d8e7d5011463)

---

### CUSTOMER CHURN ANALYSIS:  
**CUSTOMER KPI:**
*Retention Rate* =  
COUNTROWS(FILTER(GROUPBY( fact_orders, fact_orders[Customer Id]), [Total Orders] > 1))/DISTINCTCOUNT(fact_orders[Customer Id])  

*Active Users* =  
DISTINCTCOUNT(fact_orders[Customer Id])  

*Order Frequency* =  
DIVIDE(
    DISTINCTCOUNT('fact_orders'[Order ID]),
    DATEDIFF(
        MIN(dim_date[Date]),
        MAX('dim_date'[Date]),
        MONTH
    ),
    0
)  

*On-Time Delivery %* =  
DIVIDE(
    CALCULATE(
        COUNTROWS(fact_shipping),
        fact_shipping[Days for shipping (real)] <= fact_shipping[Days for shipment (scheduled)]
    ),
    COUNTROWS(fact_shipping)
)  

![image](https://github.com/user-attachments/assets/38441698-9038-4d16-b185-dc86046c62c0)

---

### DATA MODEL: SNOWFLAKE SCHEMA  
![image](https://github.com/user-attachments/assets/bbc4ca3a-4727-4eec-8a4d-0c25c9ade6f1)

---

### CONCLUSION

the analysis highlights critical areas impacting sales and operational efficiency within the supply chain. Key findings include customer churn in specific regions, inefficiencies in logistics, and external competition causing sales dips during peak periods. By implementing targeted marketing, optimizing delivery, diversifying suppliers, and discontinuing underperforming products, the client can address these challenges and improve overall performance.

LINK: 

[EDA & Data Pre-processing](https://github.com/abhinavbhandar/supplychain/blob/main/SupplyChainAnalytics.ipynb),
[Demand Forecasting(ARIMA)](https://github.com/abhinavbhandar/supplychain/blob/main/Sales_Forecast_ARIMA.ipynb),
[Dashboard Link](https://app.powerbi.com/view?r=eyJrIjoiMTY4NWVkODEtODQ3Ny00YzkwLWI2MDYtNWIyYTg5OWNhNjM1IiwidCI6IjRjMzMwZTYyLWY1YWEtNDQ4MS04YzVlLTIxZmU0MmFlZDgxYyJ9)
