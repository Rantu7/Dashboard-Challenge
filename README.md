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



 
