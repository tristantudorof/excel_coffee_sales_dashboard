# Excel Coffee Sales Dashboard

This project explores and analyzes coffee order trends to uncover insights that can help coffee shops make smarter decisions based on customer preferences and sales behavior.

# Project Skills

• Cleaning and preparing raw coffee order data.
• Data Transformation
• Filtering, Sorting and Excel Functions ( Vlookup, IF )
• Pivot Tables and Pivot Chart
• Data Visulisation and Dashboard creation
• Analyzing purchase trends


# Business Task

Build an interactive sales dashboard to showcases coffee sales and analyze, to identify sales trends.

# 1. Ask

• What country had the highst amount of sales?

• Who were the top five customers? 

• What is the best selling type of coffee?

# 2. Prepare

Dataset: [coffeeOrdersData.xlsx](https://github.com/user-attachments/files/23893265/coffeeOrdersData.xlsx)  Raw dataset containing detailed coffee orders.

In Excel, 3 sheets are included in the data set, Products, Customers, and Orders.


# 3. Process

Data gathering, 

The orders sheet has columns F through M where the data is not populated. The data sits in the other tables and we will have to use xlookup to get our data. The missing data includes, Customer Name, Email, Country, Coffee Type, Roast Type, Size, Unit Price, and Sales.

The customers sheet contains all of the customer data, the primary key or unique key for the sheet is the customer_id which is linked to individual customers.

The product sheet has the primary key, product_id which has info on specific coffees.

I start by going back to the orders sheet and gather customer data using VLOOKUP. I will have to write 3 formulas to populate the data, individual formulas for Customer Name, Email, and Country.
Then I will use INDEX MATCH to gather the product data.
INDEX MATCH will be dynamic so I will write a single formula to populate all of the columns.

#VLOOKUP

i use the vlookup formula to populate the Customer Name column.
Formual for Customer Name: =VLOOKUP(C2, customers!$A$2:$B$1001, 2, FALSE)

<img width="474" height="478" alt="Screenshot 2025-12-02 at 9 23 07 PM" src="https://github.com/user-attachments/assets/a7740917-7eff-4405-99f2-f4360422b3c7" />

