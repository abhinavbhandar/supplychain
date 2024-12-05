# SUPPLY CHAIN ANALYSIS

### [EDA & Data Pre-processing](https://github.com/abhinavbhandar/supplychain/blob/main/SupplyChainAnalytics.ipynb)
### [SALES Forecasting(ARIMA)](https://github.com/abhinavbhandar/supplychain/blob/main/Sales_Forecast_ARIMA.ipynb)
### [Dashboard Link](https://app.powerbi.com/view?r=eyJrIjoiMTY4NWVkODEtODQ3Ny00YzkwLWI2MDYtNWIyYTg5OWNhNjM1IiwidCI6IjRjMzMwZTYyLWY1YWEtNDQ4MS04YzVlLTIxZmU0MmFlZDgxYyJ9)

### SUBJECT
The client is experiencing a significant decline in sales over the past two months and wants to understand the underlying causes. This analysis will focus on customer churn, predicting future sales trends, and addressing inefficiencies in the supply chain to enhance operations and improve customer satisfaction.
### TASK
* Reducing Customer Churn
* Improve Logistics Management
* Increase Product Sales
* Improve Customer Satisfaction
* Cost Reduction
### ACTION
* Utilize the ARIMA model to forecast the monthly sales of year 2018.
* Perform Customer churn Analysis to find patterns of customer activity and regions with less customer retention rate.
* Perform Logistics Analysis to find top performing product categories.
* Perform in-depth analysis to find the sudden decrease in sales for the month of November and December of year 2017.
* Disruption caused by dependency on single or unreliable suppliers.
* Stop manufacturing of least orders products.
### RESULT
* Sales is expected to increase by 5.91% in 2018.
* customers from Africa, Asia and Oceania are more likely to leave as they have retention rate less than 40%.
* Customers are mostly active at 4 PM and 10 PM and during Weekends.
* Sales decrease in the month of November and December due to external factor: Large offers, time-limited sales and discount on multiple products by Alibaba on year end sales (Nov 11 Largest Singles Day sales ever - Alibaba says its sales alone were $25.3 billion, America was the biggest contributer after china).
* Discount rate is monotonus for each month, there should be festival sales or limited time sales to increase sales.
* More than 50% of orders are tagged with late delivery.
* CDs, Baby products, Soccer and Basketball products are ordered in less quantity and cause loss.
### SOLUTION
* Festival based sales for the customers of Africa, Asia and Oceania to increase retention rate
* Discount rate is monotonus for each month, there should be festival sales or limited time sales to increase sales.
* Region based marketing on weekends during 4 PM to 10 PM.
* Route optimization to reduce delivery time.
* Marking and removing high-risk suppliers and moving towards diversifying suppliers, implementing risk assessments, and negotiating long-term contracts with contingencies.
* Stop manufacturing of CDs, Baby products, Soccer and Basketball products.

SALES ANALYSIS:  
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

LOGISTICS ANALYSIS:  
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

CUSTOMER CHURN ANALYSIS:  
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





DATA MODEL: SNOWFLAKE SCHEMA
![image](https://github.com/user-attachments/assets/bbc4ca3a-4727-4eec-8a4d-0c25c9ade6f1)
