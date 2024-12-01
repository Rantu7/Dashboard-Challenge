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
## LEVEL 1: Basic Insights

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




## LEVEL 2 : Intermediate Insights

### What are the average review scores of users of the most common payment method?

![payment](https://github.com/user-attachments/assets/21f74b10-ce89-43c2-9edf-b836bc97ac35)

![bank review](https://github.com/user-attachments/assets/a6fac4ae-67f4-4838-be22-9c88a180a229)

Average review for Bank payment method is 2.99


### 	What is the correlation between time spent on the website and purchase amount? Do customers who spend more time on the website purchase more items?


![12](https://github.com/user-attachments/assets/c63df85a-904d-4e3c-a344-c529d4580801)

There is no consistent correlation between time spent on the website and the purchase amount. The graph shows fluctuations, suggesting that spending more time on the website doesn’t necessarily lead to higher purchase amounts.


### 	What percentage of customers are satisfied (rating of 4 or 5) and are also return customers?

![13](https://github.com/user-attachments/assets/e103f8d2-2905-40a6-8365-730529d464d1)

(2008/10000) *100 = 20.08% customers



### 	What is the relationship between the number of items purchased and customer satisfaction?

![14](https://github.com/user-attachments/assets/7e9cea94-8d51-4b38-a9c4-612081f7e05e)

Customers with Medium satisfaction purchased the highest average amount of items at 5.06, followed by Low and Highly satisfied customers with 4.99 and 4.95 items respectively.



### 	Which location has the 2nd highest average purchase amount?

![15](https://github.com/user-attachments/assets/22030da9-bbfc-490c-8030-148e67f1acaf)

Mymensingh at 507.89 average purchase amount.


## LEVEL 3: Critical Thinking Insights

### How do payment methods influence customer satisfaction and return rates?

![Q2](https://github.com/user-attachments/assets/7e403f1f-6606-4084-8214-beaa322dfb38)

To solve this problem a stacked bar chart was selected.  Each bar represented the number of return customers based on three levels of satisfaction – Low, Medium and High. Return customers who used Bank transfer, Debit Card and Credit card are more likely to be highly satisfied customers compared to other payment methods.


### 	How does the location influence both purchase amount and delivery time?

![Q3](https://github.com/user-attachments/assets/6d293859-bfee-4812-8018-ef8b646e7c0e)

No major relationship was found. For Khulna, average purchase amount was highest while the average delivery time was found to be the lowest among other locations. A similar pattern was found in Rajshahi, where it faced the highest average delivery time but the purchase amount was significantly low.



### 	What factors contribute most to a customer being classified as a return customer?

To identify the factors that determine whether a customer is a return customer, the Return Customer slicer on the dashboard was activated and deactivated to find any change in other graphs and charts.  No exact factor was found. However, Payment method, Location, Product category and Device type showed slight change due to the return customer filter.


## More Insights 

1. Review scores are relatively high when delivery times are above 7.05 days. However, lower or higher delivery times show slightly lower review scores. Thus, an optimal delivery window of around 7.05 days should be maintained for high customer satisfaction.
 ![in1](https://github.com/user-attachments/assets/ce628278-3b4a-4a7a-a771-651f2d15a2c3)


2. It seems like, highly satisfied customers purchase the lowest amount of items in average. It should be investigated why customers with higher satisfaction purchase fewer items. Moreover, maintaining medium satisfaction levels appears to encourage more purchases, so balancing customer expectations and satisfaction may yield higher sales.

![in2](https://github.com/user-attachments/assets/b3b916f5-2f4b-45ed-aa3f-962c502d480a)


3.  ![in3](https://github.com/user-attachments/assets/9eafcc01-6f7e-4219-a8c4-2886b039cbde)

This graph shows that Premium subscribers buy the least amount of items (4.96) in average. However, this amount is almost equal to customers with Trial subscription status (4.98). So there is a concern about the customers not finding it worth their money, if they become a premium user.

4. 	Although lowest portion of the clients are from other genders, they comprise the highest portion of return customers. Lowest return rate can be seen among female customers. A reason behind this could be investigated by looking at low customer rating among female clients. However, it was observed that majority of the lowest ratings came from male customers. Hence, the company should think about how to attract female sellers or try to improve the services or products for female consumers.

5. ![Screensho](https://github.com/user-attachments/assets/e454853d-29e8-4537-a99b-3dbb72019173)

   Out of three devices, Customers spent the most amount of time on their mobile devices followed by Desktop and finally Tablets. User experience should be more optimized for desktop and tablets to hold the attention of the users of these two. More focus should be concentrated on the advertisements and content strategy for desktop and tablet devices. 


6. The demographic analysis revealed that individuals aged 18-30 constituted the highest-spending customer segment, with total purchases amounting to 1.14 million. The 51-60 age group followed closely, spending 1 million. The 31-50 age group exhibited the lowest spending, with purchases not exceeding 0.96 million. To optimize sales, a strategic focus on products targeting the 31-50 demographic is recommended.

## Thank YOU! 
  



 
