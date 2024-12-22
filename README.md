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
### Code and Resources Used
**Python version:** 3.10.12  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn
### DATASET

FORECAST RESULT: [*LINK*](https://github.com/abhinavbhandar/supplychain/blob/main/forecast.csv)  
FACT & DIMENSION TABLES: [*LINK*](https://github.com/abhinavbhandar/supplychain/blob/main/Supply%20chain%20tables.rar)  
RAW DATASET: [*LINK*](https://github.com/abhinavbhandar/supplychain/blob/main/DataCoSupplyChainDataset.csv.zip)  

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
