# Sales-Report

# Overview
This project is a comprehensive analysis of Amazon sales data, aimed at uncovering key trends, customer behavior, and geographical distribution of sales. The analysis focuses on various aspects of the sales data, including overall performance, product popularity, fulfillment methods, customer segmentation, and geographical insights. The goal is to provide actionable recommendations to optimize sales strategies, improve customer satisfaction, and enhance overall business performance.This dashboard helps Amazon optimize its business operations by analyzing sales data. It allows stakeholders to identify key sales trends, customer preferences, product performance, and fulfillment delays. By identifying areas of improvement, Amazon can enhance customer satisfaction, boost sales, and streamline supply chain management.Since the analysis reveals that certain products have longer fulfillment and shipping times, as well as inconsistent sales patterns across categories, actions can be taken to improve operational efficiency.

# Problem Statement
The objective of this project is to analyze Amazon's sales data to gain insights into sales trends, customer behavior, and geographical distribution. The analysis is designed to:

1. Understand Sales Performance:  Analyze sales trends and patterns over time to identify growth opportunities.
2. Product Analysis: Determine the popularity of different product categories and sizes, and identify top-selling items.
3. Fulfillment Analysis: Investigate the efficiency of different fulfillment methods and their impact on delivery times.
4. Customer Segmentation: Segment customers based on buying behavior, location, and other factors to target marketing efforts effectively.
5. Geographical Analysis: Explore the distribution of sales across different regions to identify areas of high demand and growth potential.
6. Business Recommendations: Provide actionable insights and recommendations to improve overall business performance based on the analysis.
# Project Structure
1. Data : Contains the raw and processed datasets used for analysis.
2. Notebooks : Jupyter notebooks detailing the data analysis and visualization processes.
3. Scripts : Python scripts for data processing, analysis, and visualization.
4. Reports : Contains the final report summarizing the key findings, insights, and recommendations.
README.md: This file, providing an overview of the project and instructions for use.

### Steps followed 

- Step 1: Load Amazon sales dataset (CSV file) into Power BI Desktop.

- Step 2: Open Power Query Editor and in the "View" tab, check the "Column Distribution," "Column Quality," and "Column Profile" options to inspect data quality.

- Step 3: Ensure column profiling based on the entire dataset, ensuring data completeness and accuracy.

- Step 4: Handle missing or erroneous values in key fields such as ship-service-level, fulfillment-status, and Amount. Null values were ignored while calculating overall averages and fulfillment times.

- Step 5: Calculate average shipping time using the formula:

           Average_Shipping_Time = df['ship-postal-code'].mean()

- Step 6: In the report view, select a suitable theme for visualization consistency.

- Step 7: Add visual filters (Slicers) for fields like Category, Fulfillment By, B2B, and Shipping Region.

- Step 8: Add two card visuals for Total Sales Amount and Total Units Sold. Use filtering options to exclude irrelevant data.

- Step 9: Bar chart representing customer segments and fulfillment channels (e.g., B2B vs. B2C), filtered by different sales channels such as fulfilled-by.

- Step 10: Use the Ratings visual to show customer satisfaction across various product attributes such as Ease of purchase, Shipping speed, and Product quality.

Visualizations & Measures
- Step 11: Calculate total number of sales transactions using the formula:

    
        Total_Transactions = len(df['Order ID'])

Display as a card visual to show the count of transactions.
- Step 12: Create sales groups (if available for customer demographic data) to classify customers by sales brackets:

    
      Sales_Group = np.where(df['Sales'] <= 25, "0-25",
                     np.where(df['Sales'] <= 50, "25-50",
                              np.where(df['Sales'] <= 75, "50-75", "75-100")))

- Step 13: Add bar or pie charts to show the distribution of product categories and top-selling items. 

- Step 14: New measure for calculating the total revenue generated:
    
      Total_Revenue = df['Amount']
Snap of new calculated column ,

![image](https://github.com/user-attachments/assets/a38e2fc8-27c8-4e2a-8edf-ede8d38026f8)

        
- Step 15 : New measure was created to find total count of Order ID.

Following DAX expression was written for the same,
        
        Count of Customers = COUNT(Amazon Sales Report[Order ID])
        
A card visual was used to represent count of customers.

![image](https://github.com/user-attachments/assets/eee44abb-f1be-492e-bd9a-20ed8dc8380d)
        
 - Step 16 : New measure was created to find  % of customers,
 
 Following DAX expression was written to find % of customers,
 
         % Customers = (DIVIDE(Amazon Sales Report[Count of Customers], 129880)*100)
 
 A card visual was used to represent this perecntage.
 
 Snap of % of customers who preferred Sales types
 
 ![image](https://github.com/user-attachments/assets/305537dc-c319-41fd-a3e6-d044477da55d)

 
 - Step 17 : New measure was created to calculate total distance travelled by Ships & a card visual was used to represent total distance.
 
 Following DAX expression was written to find total distance,
 
         Total Distance Travelled = SUM(Amazon Sale Report[Total Revenue])
    
 A card visual was used to represent this total distance.
 
 
 ![Snap ](https://github.com/user-attachments/assets/9548b8d5-ee06-4b30-9d11-2ec009b2af85)
 
 - Step 18 : The report was then published to Power BI Service.
# Snapshot of Dashboard (Power BI Service)

![image](https://github.com/user-attachments/assets/2b8ebfce-672e-45f2-ac3e-d6e50fcf12c4)

![image](https://github.com/user-attachments/assets/b4eaa22c-7cec-4713-aba0-ec8d3f11bf46)


 
 # Report Snapshot (Power BI DESKTOP)

 
![image](https://github.com/user-attachments/assets/97238c49-53ae-4b40-9017-c6a656819480)
# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total Number of Customers = 129880

   Number of satisfied Customers (OrderID) = 28159 (21.68 %)

   Number of satisfied Customers (Ship-state) = 28269 (21.76 %)

   Number of neutral/unsatisfied customers (Ship-city) = 35822 (27.58 %)

   Number of neutral/unsatisfied customers (ship-postal-code) = 37630 (28.97 %)


           thus, higher number of customers are neutral/unsatisfied.
           
### [2] Average Ratings

    a) Product Quality - 0.90/5
    b) Delivery Service - 465399.51/5
    c) Customer Service - 623.79/5
    d) Return Process - 559.19/5
    e) Value for Money - 580847.92/5
    
  
  while calculating average rating, null values have been ignored as they were not relevant for some customers. 
  
  These ratings will change if different visual filters will be applied.  
  
  ### [3] Average Delay 
  
      a) Average delay in arrival(minutes) - 623.79
      b) Average delay in departure(minutes) - 559.19
Average delay will change if different visual filters will be applied.

 ### [4] Some other insights
 
 ### Sales Distribution by Category
 
 1.1) 10.50% of total sales the Blazzer.
 
 1.2) 0.64% of total sales the Perfume.
 
 1.3) 27.35% of total sales the Shirt.
 
 1.4) 0.34% of total sales the Socks.

 1.5) 53.33% of total sales the T-shirt.

 1.6) 6.99% of total sales the Trousers.

 1.7) 0.63% of total sales the Wallet. 
 
         thus, maximum total sales by T-shrit.
 

         
### Sales Type

2.1) 56.36 % Sales have Sale type 'ship-state'.

2.2) 56.44 % sales have Sale type 'ship-city'.
       
       thus, more customers have customer type 'ship-city'.


