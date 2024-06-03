# E-commerce Sales Dashboard in Power BI

This repository contains a Power BI dashboard for analyzing key KPIs in e-commerce sales. The dashboard provides insights into various aspects of the sales data, such as payment statistics, customer behaviour, review scores, order delivery times, and more.

## Introduction
This Power BI dashboard is designed to provide a comprehensive analysis of e-commerce sales data. It includes various KPIs to help understand sales performance and customer behavior. The key KPIs are:
1. Weekday vs Weekend Payment Statistics
2. Number of Orders with Review Score 5 and Payment Type as Credit Card
3. Average Number of Days Taken for Order Delivery for Pet Shop
4. Average Price and Payment Values from Customers in São Paulo City
5. Relationship between Shipping Days and Review Scores
6. Top 10 Customer Cities
7. Top 10 Sellers
8. Top 10 Product Categories

## Data Collection
The data used for this dashboard was collected from an e-commerce platform's database. The data includes information on orders, customers, payments, reviews, and products.

## Data Cleaning
Data cleaning involved:
- Removing duplicates
- Handling missing values
- Standardizing data formats

## Data Transformation
Data transformation steps included:
- Converting data types
- Creating new columns for analysis
- Aggregating data for summary statistics

## Data Modeling
Data modeling involved creating relationships between tables to ensure accurate data analysis. The main tables used were:
- Orders
- Customers
- Payments
- Reviews
- Products
- Sellers

The relationships were established based on common keys such as order ID, customer ID, and product ID.

## DAX Measures
DAX (Data Analysis Expressions) was used to create measures for various KPIs. Some of the key measures created are:

1. **Weekday vs Weekend Payment Statistics:**
    ```DAX
    WeekdayPayments = CALCULATE(SUM(Payments[PaymentValue]), WEEKDAY(Orders[OrderDate]) <= 5)
    WeekendPayments = CALCULATE(SUM(Payments[PaymentValue]), WEEKDAY(Orders[OrderDate]) > 5)
    ```

2. **Number of Orders with Review Score 5 and Payment Type as Credit Card:**
    ```DAX
    OrdersWithReviewScore5 = CALCULATE(COUNT(Orders[OrderID]), Reviews[ReviewScore] = 5, Payments[PaymentType] = "credit_card")
    ```

3. **Average Number of Days Taken for Order Delivery for Pet Shop:**
    ```DAX
    AvgDeliveryDaysPetShop = AVERAGEX(FILTER(Orders, Orders[ProductCategory] = "pet_shop"), DATEDIFF(Orders[OrderPurchaseDate], Orders[OrderDeliveredCustomerDate], DAY))
    ```

4. **Average Price and Payment Values from Customers in São Paulo City:**
    ```DAX
    AvgPriceSaoPaulo = CALCULATE(AVERAGE(Orders[Price]), Customers[City] = "São Paulo")
    AvgPaymentValueSaoPaulo = CALCULATE(AVERAGE(Payments[PaymentValue]), Customers[City] = "São Paulo")
    ```

5. **Relationship between Shipping Days and Review Scores:**
    ```DAX
    ShippingDays = DATEDIFF(Orders[OrderPurchaseDate], Orders[OrderDeliveredCustomerDate], DAY)
    ```

## Visualizations
The following visualizations were created to represent the KPIs:

1. **Weekday vs Weekend Payment Statistics:**
   - Bar chart comparing total payments on weekdays vs weekends

2. **Number of Orders with Review Score 5 and Payment Type as Credit Card:**
   - Card visual showing the count

3. **Average Number of Days Taken for Order Delivery for Pet Shop:**
   - Card visual showing the average days

4. **Average Price and Payment Values from Customers in São Paulo City:**
   - Multi-row card visual displaying average price and payment values

5. **Relationship between Shipping Days and Review Scores:**
   - Scatter plot showing the correlation between shipping days and review scores

6. **Top 10 Customer Cities:**
   - Bar chart listing the top 10 cities by the number of customers

7. **Top 10 Sellers:**
   - Bar chart listing the top 10 sellers by sales

8. **Top 10 Product Categories:**
   - Bar chart listing the top 10 product categories by sales

## Dashboard
The dynamic dashboard includes all the above visuals and allows users to interact with the data through filters and slicers. Users can drill down into specific KPIs to gain deeper insights into the e-commerce sales data.

## Conclusion
This Power BI dashboard provides a comprehensive analysis of e-commerce sales data, enabling better decision-making and insights into sales performance and customer behavior. The steps outlined above detail the process from data collection to the final dashboard creation. Feel free to explore the visuals and gain insights from the data.
