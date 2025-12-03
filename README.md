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

# VLOOKUP

I use the vlookup formula to populate the Customer Name cell, and then double click to fill the column.
Formual for Customer Name: =VLOOKUP(C2, customers!$A$2:$B$1001, 2, FALSE)

<img width="474" height="478" alt="Screenshot 2025-12-02 at 9 23 07 PM" src="https://github.com/user-attachments/assets/a7740917-7eff-4405-99f2-f4360422b3c7" />

I then used the vlookup to populate the Email column.
Formula for Email: =VLOOKUP(C2, customers!$A$1:$C$1001, 3, FALSE)

<img width="520" height="508" alt="Screenshot 2025-12-02 at 9 36 59 PM" src="https://github.com/user-attachments/assets/2ff6ef0b-42c8-42e1-ba71-c92555b44ee0" />

Because some of the emails values were missing ( the email address was blank ) it gave me a value of 0

To get rid of the 0 value we will adjust the formula, and double click the cell to populate the column. 

New formula for email to remove 0 value: =IF(VLOOKUP(C2, customers!$A$1:$C$1001, 3, FALSE)=0,"",VLOOKUP(C2, customers!$A$1:$C$1001, 3, FALSE))

<img width="279" height="234" alt="Screenshot 2025-12-02 at 9 43 35 PM" src="https://github.com/user-attachments/assets/6c578b1d-e5bb-4295-9e24-7fd4b67c3580" />

Next I will do the Country column.
Formula for Country: =VLOOKUP(C2, customers!$A$2:$G$1001, 7, FALSE)

<img width="562" height="361" alt="Screenshot 2025-12-02 at 9 52 22 PM" src="https://github.com/user-attachments/assets/f3bdf001-ccc0-4a8a-a009-d356d00d7bce" />

I now have all of the necessary customer data. 
I will now move onto the product details. I will gather the data from the Products sheet to populate the Orders sheet now. 

# INDEX MATCH

I am using index match because it will be dynamic and able to populate all of the cells for the product.

Index Match formula: =INDEX(products!$A$2:$G$49,MATCH(orders!$D2,products!$A$2:$A$49,0),MATCH(orders!K$1,products!$A$1:$G$1,0))

<img width="701" height="243" alt="Screenshot 2025-12-02 at 10 30 16 PM" src="https://github.com/user-attachments/assets/2fc578d1-dc68-4f30-b114-1367edab1d38" />

I am now able to drag the cell to populate the other columns.

<img width="314" height="180" alt="Screenshot 2025-12-02 at 10 34 37 PM" src="https://github.com/user-attachments/assets/a23eed69-68bd-4ffd-b216-15dfcaf691f4" />

Populating the rest of the cells. 

<img width="371" height="553" alt="Screenshot 2025-12-02 at 10 37 58 PM" src="https://github.com/user-attachments/assets/9d58fc73-a586-40dd-9d91-2fc55e7c7ac0" />

Lastly, the Sales column.
To populate the Sales column we will multiply the Unit Price by Quantity Sold.

Formula for Sales: =[@[Unit Price]]*[@Quantity]

<img width="595" height="363" alt="Screenshot 2025-12-02 at 10 45 00 PM" src="https://github.com/user-attachments/assets/fe5e0ff3-2374-4bc7-add5-a8f35378cd01" />

When looking at the columns, i noticed the Coffee Type gave the abbreviation of the coffee name. I will add a new column to give the full name of the coffee.

Formual used to add full name: =IF(I3="Rob","Robusta",IF(I3="Exc","Excelsa",IF(I3="Ara","Arabica",IF(I3="Lib","Liberica",""))))

<img width="636" height="478" alt="Screenshot 2025-12-02 at 10 55 31 PM" src="https://github.com/user-attachments/assets/dcd844f3-bd58-44ef-89e9-5d36e0d102ce" />


