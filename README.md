# Walmart-Sales-Analysis

![pic1111](https://github.com/user-attachments/assets/8f4878a3-65dc-4dde-9470-37c41b522301)

## Table of Contents

- [Introduction](#Introduction)
- [Dataset Overview](#Dataset-Overview)
- [Project Objective](#Project-Objective)
- [Data Cleaning](#Data-Cleaning)
- [Data Exploration and Insights](#Data-Exploration-and-Insights)
- [Recommendation](#Recommendation)
- [Conclusion](#Conclusion)

## Introduction
The Walmart sales business relies on data to gain deeper understanding of the business and identify opportunities to optimize strategies, improve customer satisfaction, and increase revenue of the business. SQL was used to query and analyze the data, as well as answer specific questions about the dataset to uncover valuable insights that can inform business decisions and drive growth.

## Dataset overview
The dataset includes the following columns:
Invoice ID: Unique identifier for each sales transaction.
Branch: The specific store or branch where the transaction occurred.
City: The city where the branch is located.
Customer Type: The type of customer( e.g., Member, Normal)
Gender: The customer's gender. 
Product line: The category or type of product sold.
Unit price: The price of a single unit of the product.
Quantity: The number of units sold.
Tax: The amount of tax applied to the sale.
Total: The total amount paid by the customer, including tax.
Date: The date when the transaction occurred.
Time: The time when the transaction occurred.
Payment: The method of payment used by the customer.( e.g., E-wallet, Credit card, Cash)
COGS: (Cost of goods sold). The direct cost of producing and selling the product.
Gross margin Percentage: The percentage of revenue that is gross profit.
Gross income: The revenue generated from sales, minus COGS.
Rating: The customer's rating or satisfaction score for the transaction.

## Project Objective
You are tasked with analyzing this Walmart sales dataset using SQL. Here are business questions for which you will write SQL Queries to gain insights.
Generic Question
1.	How many unique cities does the data have?
2.	In which city is each branch?
Product
1.	How many unique product lines does the data have?
2.	What is the most common payment method?
3.	What is the most selling product line?
4.	What is the total revenue by month?
5.	What month had the largest COGS?
6.	What product line had the largest revenue?
7.	What is the city with the largest revenue?
8.	What product line had the largest VAT?
9.	Fetch each product line and add a column to those product line showing "Good", "Bad". Good if its greater than average sales
10.	Which branch sold more products than average product sold?
11.	What is the most common product line by gender?
12.	What is the average rating of each product line?
Sales
1.	Number of sales made in each time of the day per weekday
2.	Which of the customer types brings the most revenue?
3.	Which city has the largest tax percent/ VAT (Value Added Tax)?
4.	Which customer type pays the most in VAT?
Customer
1.	How many unique customer types does the data have?
2.	How many unique payment methods does the data have?
3.	What is the most common customer type?
4.	Which customer type buys the most?
5.	What is the gender of most of the customers?
6.	What is the gender distribution per branch?
7.	Which time of the day do customers give most ratings?
8.	Which time of the day do customers give most ratings per branch?
9.	Which day of the week has the best avg ratings?
10.	Which day of the week has the best average ratings per branch?

![Screenshot 2025-03-28 124141](https://github.com/user-attachments/assets/4f49e9dd-2ea2-4077-9c50-ff61e365128e)


## DATA CLEANING
I started by renaming the table name from walmartsalesdata.csv to Walmart_salesdata
Rename table `walmartsalesdata.csv` to Walmart_salesdata;

- Rename column
- Rename column Invoice ID to Invoice_ID
```sql 
Alter table Walmart_salesdata
Rename column `Invoice ID` to Invoice_ID;
```
-Rename column Customer Type to Customer_Type
```sql
Alter table Walmart_salesdata
Rename column `Customer Type` to Customer_Type;
```

- Rename column Product line to Product_Line
```sql
Alter table Walmart_salesdata
Rename column `Product Line` to Product_Line;
```

- Rename column Unit Price to Unit_Price
```sql
Alter table Walmart_salesdata
Rename column `Unit Price` to Unit_Price;
```

-Rename column Tax 5% to Tax
```sql
Alter table Walmart_salesdata
Rename column `Tax 5%` to Tax;
```

- Rename column gross margin percentage to gross_margin_percentage
```sql
Alter table Walmart_salesdata
Rename column `gross margin percentage` to gross_margin_percentage;
```

- Rename column gross Income to gross_Income
```sql
Alter table Walmart_salesdata
Rename column `gross Income` to gross_Income;
```

- Change Date column Data type
```sql
Alter table Walmart_salesdata
Modify column Date date;
```

- Added new column Time Category
```sql
Alter table walmart_salesdata
Add column Time_category text;
```
```sql
Update walmart_salesdata
Set time_category = case when time between "00:00:00" and "12:00:00" then "Morning"
when time between "12:00:00" and "16:00:00" then "Afternoon"
else "Evening" end;
```

## Data Exploration and Insights

- Generic Question
1. How many unique cities does the data have?
INSIGHTS: There are 3 unique countries in this dataset.

2. In which city is each branch?
INSIGHTS: Branch A is in Yangon, Branch B is in Mandalay and Branch C is in Naypyitaw.

- Product
1. How many unique product lines does the data have?
INSIGHTS: There are 6 unique products in this dataset.
2. What is the most common payment method?
INSIGHTS: The most common payment method was Ewallet with 345 counts.

3. What is the most selling product line?
INSIGHTS: Electronics accessories with 971 total quantities.

4. What is the total revenue by month?
INSIGHTS: January 116291.87, February 97219.37, March 109455.51.

5. What month had the largest COGS?
INSIGHTS: January had the largest cost of goods sold with a total of 110754.16.

6. What product line had the largest revenue?
INSIGHTS: Food and beverages had the largest revenue with a total of 56144.84.

7. What is the city with the largest revenue?
INSIGHTS: Naypyitaw had the largest revenue with a total of 110568.71.

8. What product line had the largest VAT?
INSIGHTS: Food and Beverages had the largest VAT with a total of 2673.56.

9. Fetch each product line and add a column to those product line showing "Good", "Bad". Good if its greater than average sales.
INSIGHTS: Health and beauty, Home and lifestyle, Sports and travel are categorized as Good Products While Electronic accessories, Food and beverages, Fashion accessories are categorized as BAD.

11. Which branch sold more products than average product sold?
INSIGHTS: Branch C sold more products than the overall average, with an average of 5.58.

12. What is the most common product line by gender?
INSIGHTS: Female (Fashion Accessories) 96 counts.

13. What is the average rating of each product line?
INSIGHTS: Health and beauty 7, Electronic accessories 6.92, Home and lifestyle 6.84, Sports and travel 6.92, Food and beverages 7.11, Fashion accessories 7.03.

- Sales
1. Number of sales made in each time of the day per weekday
INSIGHTS: Morning 733, Afternoon 1486 and evening 1594.

2. Which of the customer types brings the most revenue?
INSIGHTS: Member with a total of 164223.44.

3. Which city has the largest tax percent/ VAT (Value Added Tax)?
INSIGHTS: Naypyitaw received the largest VAT with a total of 5265.18.


4. Which customer type pays the most in VAT?
INSIGHTS: Member paid the most VAT with a total of 7820.16.

- Customer
1. How many unique customer types does the data have?
INSIGHTS: 2.

2. How many unique payment methods does the data have?
INSIGHTS: 3.

3. What is the most common customer type?
INSIGHTS: Member with 501 counts.

4. Which customer type buys the most?
INSIGHTS: Member buys the most amongst the customer type with 2785 total quantities.

5. What is the gender of most of the customers?
INSIGHTS: Female with 501 counts.

6. What is the gender distribution per branch?
INSIGHTS: Branch A Female 161, Branch A Male 179, Branch B Female 162, Branch B Male 170, Branch C Female 178, Branch C Male 150.

7. Which time of the day do customers give most ratings?
INSIGHT: The most ratings was received during the evening hours with the total of 2992.4 ratings.

8. Which time of the day do customers give most ratings per branch?
INSIGHTS: Branch C received the highest rating during Evening hours with the total of 1018 ratings.

9. Which day of the week has the best avg ratings?
INSIGHTS: The best average ratings was received on MONDAY with 7.15.

10. Which day of the week has the best average ratings per branch?
INSIGHTS: Branch B, Monday, Average ratings (7.34).

## Recommendation
1. City Expansion Opportunities: Since the dataset covers three cities (Yangon, Mandalay, Naypyitaw), it may be beneficial to analyze whether expanding to other cities could drive more revenue. Naypyitaw, having the highest revenue, suggests a strong market presence there.
2. Branch Performance: With Branch C (Naypyitaw) selling more products than the average and generating the most revenue, investment in marketing or expansion efforts in this city may yield positive results.
3. Optimize Product Lines: The classification of product lines into “Good” and “Bad” suggests an opportunity to either improve sales strategies for “Bad” products or phase out underperforming ones. For instance, electronic accessories and fashion accessories are selling below average. Promotions or bundling strategies could help increase their sales.
4. Focus on High-Revenue Product Lines: Food and Beverages generated the highest revenue and VAT, indicating a strong market demand. Increasing stock, offering promotions, or introducing complementary products could further boost sales.
5. Improve Sales for Low-Performing Product Lines: Electronic Accessories and Fashion Accessories were among the least successful. Understanding customer preferences, adjusting pricing, or offering discounts could help.
6. Leverage Peak Sales Hours: Sales are highest in the evening, followed by the afternoon. Targeted promotions, discounts, or loyalty rewards during these hours can maximize revenue.
7. Day-Specific Promotions: Monday received the best average ratings, indicating a positive customer experience. Businesses can use this insight to introduce “Monday Specials” or extend customer service best practices from this day to others.
8. Payment Method Preferences: E-wallet was the most used payment method. Encouraging digital transactions through discounts or cashback offers could enhance customer convenience and increase transactions.
9. Focus on Members: Members contribute the most revenue and VAT. Loyalty programs, personalized offers, and exclusive discounts can encourage more non-members to convert.
10. Gender-Specific Targeting: More females are customers, especially in Fashion Accessories. More gender-targeted marketing campaigns can increase sales in this segment.
11. Customer Experience by Branch: Branch C received the highest ratings in the evening. Understanding what drives this positive experience can help replicate it across other branches.
12. VAT Optimization: Naypyitaw had the highest VAT collection, meaning sales are performing well in this city. This branch could be prioritized for expansion or premium product placement.
13. Member VAT Contributions: Since Members pay the highest VAT, encouraging more non-members to join loyalty programs could also increase VAT revenue.

## Conclusion

• Strengthen branch C (Naypyitaw) since it leads in revenue, product sales, and ratings.
• Invest in high-performing product lines (Food and Beverages, Health and Beauty).
• Enhance sales for low-performing product lines (Electronics, Fashion Accessories).
• Leverage digital payment trends by offering incentives for E-wallet transactions.
• Capitalize on peak sales times (evening hours and Mondays) with promotions.
•Encourage membership sign-ups through exclusive discounts and rewards.

By implementing these strategies, the business can optimize sales, enhance customer experience, and drive higher revenue.
