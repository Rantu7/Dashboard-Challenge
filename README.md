# <p align="center">Store Sales Dashboard & Analysis by Rantu Adhikary</p>
# <p align="center">![Screenshot_19](https://github.com/user-attachments/assets/d43b8ebb-00f7-4e02-86f3-5237a519438e)</p>
## Overview
This Sales Data Analysis Project, undertaken as part of a Data Innovators Challenge, addresses a series of business questions categorized into three progressively challenging levels. 

Level 1: Basic Insights
Focused on identifying key performance indicators (KPIs), statistical metrics, and basic data summaries. This level establishes a solid understanding of the dataset.

Level 2: Intermediate Insights
Investigates relationships and correlations among variables to uncover trends and patterns within the data.

Level 3: Critical Thinking Insights
Tackles complex business questions requiring deep analysis, logical reasoning, and interpretation to provide strategic insights.

This project aims to solve the 3 levels of business questions by building an interactive dashboard in Power BI and dives deeper to find more insights and recommendations.

 ## The Data
The data set was provided by the host of the competition, which contained one .csv file. The file was downloaded and then imported into Power BI for the analysis. The data contains 16 columns and around 10000 rows. Brief description about the columns in the data files are given in the table below:
1. Customer ID: Unique identifier for each customer.
2. Age: The age of the customer.
3. Gender: Gender of the customer (Male, Female, Other).
4. Location: The city or region where the customer resides.
5. Product Category: The category of the product purchased.
6. Purchase Amount ($): The total amount spent by the customer in dollars.
7. Time Spent on Website (min): The total time the customer spent on the website, measured in minutes.
8. Device Type: The type of device the customer used to access the 
9. Payment Method: The method the customer uses for payment 
10. Discount Availed: Whether the customer gets a discount during their purchase (True or False).
11. Number of Items Purchased: The total number of items the customer purchased.
12. Return Customer: Whether the customer is a returning customer (True or False).
13. Review Score (1-5): The customer's rating of the product or service, on a scale from 1 to 5.
14. Delivery Time (days): The number of days it took for the delivery to be completed.
15. Subscription Status: The type of subscription the customer holds (e.g., Free, Premium, Trial).
16. Customer Satisfaction: The satisfaction level of the customer, categorized as Low, Medium, or High.


## Data Preparation/Cleaning
The dataset was loaded into Power BI’s power query and cleaned to prepare for the next step. Data cleaning included the following steps:
•	Removed duplicates

•	Removed unnecessary columns

•	Checked blank and null values

•	Fixed data types

•	Added a conditional column to group some data

## Solving The Problems
## LEVEL 1

###	Find Mean, Median , Mode (Age)
![1](https://github.com/user-attachments/assets/a98ee4ce-27b9-42ef-ba2a-bb0774e0caa7)

DAX for this problem:

   ```dax
Mean Age = AVERAGE(ecommerce_customer_behavior_dataset[Age])
   ```

   ```dax
Median Age = MEDIAN(ecommerce_customer_behavior_dataset[Age])
  ```

 ```dax
Mode Age = 
MINX (
    TOPN(
        1,
        ADDCOLUMNS(
            VALUES (ecommerce_customer_behavior_dataset[Age]),
            "Frequency", CALCULATE(COUNT(ecommerce_customer_behavior_dataset[Age]))
        ),
        [Frequency],
       0
    ),
    ecommerce_customer_behavior_dataset[Age]
)
  ```


###	Find variance, standard deviation, and z-score (Purchase Amount)

![2](https://github.com/user-attachments/assets/78e094d4-498c-4765-bcb5-af84e94318aa)


![2-2](https://github.com/user-attachments/assets/d1169f4a-83a2-4c02-8ef9-30fb3f0eb642)

DAX for this problem:

```dax
Variance = VAR.P(ecommerce_customer_behavior_dataset[Purchase Amount ($)])
   ```

   ```dax
Standard_Deviation = STDEV.P(ecommerce_customer_behavior_dataset[Purchase Amount ($)])
  ```

 ```dax
Z Score = DIVIDE(([Summation] - [Mean Purchase]), [Stdev purchase])
  ```



###	What are the top three product categories based on the number of purchases?

![3](https://github.com/user-attachments/assets/05e4d090-bb7e-427f-9f29-7dae6968dba6)

Toys , Books and Electronics appeared to be the top most purchased product categories. 


### 	How many customers are classified as return customers?

![4](https://github.com/user-attachments/assets/7c2161fe-71f8-4298-88ac-8a8fd0a55073)

Total 5004 customers are resturn customers.



### 	What is the average review score given by customers?

![5](https://github.com/user-attachments/assets/ee1f0a6b-57aa-4692-a8ef-1c76c58aa213)



### 	How does the average delivery time vary between subscription statuses? (Free, Premium)?

![6](https://github.com/user-attachments/assets/cd4e71b5-e4c4-4f51-bcbb-d006b9385f99)

| Subscription Status       | Avg. Delivery Time (days)      |
|---------------------------|--------------------------------|
| Free                      | 6.96                           |
| Premium                   | 7.07                           |
| Trial                     | 7.00                           |



### How many customers are subscribed to the service?

![7](https://github.com/user-attachments/assets/8aa84602-3064-487d-b2c1-cad835489389)

### 	What percentage of customers used devices to make purchases? (Mobile, Laptop, Tablet)

![8](https://github.com/user-attachments/assets/2893d4fc-9dfb-4879-a457-d73289ddfc26)

Mobile: 33.74%, Desktop: 33.48%, Tablet: 32.78%


### 	What is the average purchase amount for customers who availed discounts compared to those who didn’t?

![9](https://github.com/user-attachments/assets/e5974bc8-74d5-4c57-a943-949c60dc5893)


0.51k Purchases were made by customers with discounts and 0.5k for those who did not.


### 	What is the most common payment method used by customers?

![10](https://github.com/user-attachments/assets/50402bfa-f8f1-4c73-b59e-6b71aa36cafe)

Bank transfer with 1.05 million total purchase amount.

### 


 
