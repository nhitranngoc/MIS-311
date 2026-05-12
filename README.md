# MIS-311
# Supermarket Sales Analysis & Business Insights Report
# 1. Project Overview
This project involves conducting a detailed Exploratory Data Analysis (EDA) of sales transactions from a regional supermarket network in New York, Los Angeles, and Chicago. 
The objective is to analyze historical sales data to understand customer purchasing behaviors, assess the performance of various product categories, and identify opportunities to boost profitability and improve operational efficiency.
# 2. Data Description
The dataset was obtained from the supermarket's internal sales system, encompassing various transactions across its branches.

Data Dimensions: 8 columns and 254 individual transaction records.

Variable Definitions:

Sale_id: Unique identifier for each transaction.

Branch: Brand of the supermarket.

City: Location of the branch.

Customer_type: Segmentation of customers (Member vs. Normal).

Product_name: The specific item purchased.

Product_category: Broad classification of the product.

Quantity: The number of units sold.

Total_price: Final transaction amount in USD.
# 3. Data Cleaning & Preparation
To ensure high-quality analysis, a rigorous data cleaning process was performed using Excel:
# Removing duplicate records:
I used the 'Remove duplicate records' feature with Sale_id as the primary key.
<img width="975" height="472" alt="image" src="https://github.com/user-attachments/assets/205dfdb3-a4e3-4c4f-abf9-4b4a51a205db" />
Three duplicate records were identified and removed to avoid double-calculating sales.
<img width="975" height="471" alt="image" src="https://github.com/user-attachments/assets/6a455040-8fb0-487f-abcf-267ced2daca6" />
# Data consistency and standardization:
I discovered significant anomalies in data entry in the Product Category column. Several items were severely misclassified (e.g., "Apples" were incorrectly categorized under "Personal Care" or "Stationery," and "Notebooks" were classified as "Beverages").

<img width="481" height="452" alt="image" src="https://github.com/user-attachments/assets/6f26e284-b154-467f-a7b1-ce15bf8bd35e" />
<img width="490" height="452" alt="image" src="https://github.com/user-attachments/assets/ffe6e034-f2fc-4534-b5b4-eaecb4c9a86a" />
I systematically checked the Product Name column and reassigned any misclassified transactions to their correct, standardized categories. The following strict classification rules were applied:
Apple ➔ Classified only in the Fruits category.
Detergent ➔ Classified only in the Household category.
Notebook ➔ Classified only in the Stationery category.
Orange Juice ➔ Classified only in the Beverages category.
Shampoo ➔ Classified only in the Personal Care category.
  <img width="471" height="435" alt="image" src="https://github.com/user-attachments/assets/ca367319-2eb2-4eeb-b226-0c9ff53f9ff5" />
<img width="472" height="436" alt="image" src="https://github.com/user-attachments/assets/3b606c45-e760-4233-bd9a-7478ec6254a8" />
# Handling Missing Values:
Missing data points were handled using separate methods, tailored to the data to preserve both statistical validity and underlying business logic:
Fill in Categorical Value (Customer Type): Several records were missing customer segment data.
 <img width="596" height="643" alt="image" src="https://github.com/user-attachments/assets/e8818910-f3c2-4a7d-a13c-029f302dec38" />
To maintain dataset balance and avoid unnecessary row deletions, I used "mode imputation" by replacing blank cells with the mode value ("Member").
 <img width="657" height="645" alt="image" src="https://github.com/user-attachments/assets/011df672-7d8a-4dad-abbc-5d0b9a99731d" />
Filling in Numerical Value (Quantity): Missing sales volume data was identified in three specific transactions (Sale_id 20, 44, 61), all related to the product "Detergent".
 <img width="975" height="113" alt="image" src="https://github.com/user-attachments/assets/17ba384c-5326-4c6e-b81e-cf2713a18bed" />
I noticed that the unit price varies between different orders due to various factors (such as branch-specific pricing or applied discounts), so the unit price alone cannot be used to calculate the quantity of detergent sold for those orders. An average unit price needs to be calculated as a basis. I calculated the total detergent sold and its total value, excluding the three missing records, using the "Sum" function. Then I divided the sum of the total price by the total number of detergents.
 <img width="975" height="571" alt="image" src="https://github.com/user-attachments/assets/bfb69053-55d5-48a5-9521-57de5720b223" />
Finally, to get the quantity of the missing orders, I divided the total price of each order by the average unit price, using the round function to round if the number is odd.
 <img width="975" height="152" alt="image" src="https://github.com/user-attachments/assets/7051e373-154a-40ec-a65b-a132f9e14f92" />
# 4. Exploratory Data Analysis & Insights
Insight 1: Revenue Distribution by Product Category
An analysis of total revenue reveals the financial contribution of each product segment. The personal care category is the leading revenue driver ($7,424.13), closely followed by stationery ($6,979.10). This indicates strong consumer demand for essential health and office products. Management should prioritize inventory levels for these categories and consider bundled product packages (e.g., combining stationery with personal care items) to increase the average transaction value.
 <img width="429" height="205" alt="image" src="https://github.com/user-attachments/assets/68d906ce-0604-44a3-b94c-4b4a36b0e019" />
 <img width="977" height="381" alt="image" src="https://github.com/user-attachments/assets/db03a0a4-d71d-4558-8092-b6bc44553ac8" />
Insight 2: Customer Segment Performance & Loyalty Impact
This analysis compares the purchasing power of registered members with that of normal customers (non-registered customers). "Member" customers contribute a significantly higher share of total revenue ($17,939.55) than "Normal" customers ($13,106.73). This gap is most pronounced in the stationery segment. The marketing department should focus on conversion campaigns to encourage regular customers to register as members, as membership demonstrates significantly higher lifetime value for the supermarket.
 <img width="742" height="239" alt="image" src="https://github.com/user-attachments/assets/44d28899-e157-4844-b297-db277e5552bd" />
<img width="977" height="320" alt="image" src="https://github.com/user-attachments/assets/7adbd930-d7e1-4164-b5f9-644b98bfc799" />
