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

# IF Functions

When looking at the columns, i noticed the Coffee Type gave the abbreviation of the coffee name. I will add a new column to give the full name of the coffee so it is easier to understand.

Formual used to add full name: =IF(I3="Rob","Robusta",IF(I3="Exc","Excelsa",IF(I3="Ara","Arabica",IF(I3="Lib","Liberica",""))))

<img width="636" height="478" alt="Screenshot 2025-12-02 at 10 55 31 PM" src="https://github.com/user-attachments/assets/dcd844f3-bd58-44ef-89e9-5d36e0d102ce" />

For Roast Type I would like it to say Dark, Medium, light. Instead of D,M,L.

I named column o Roast Type Name.

Formula used: =IF(J3="M","Medium",IF(J3="L","Light",IF(J3="D","Dark","")))

<img width="384" height="254" alt="Screenshot 2025-12-02 at 11 30 55 PM" src="https://github.com/user-attachments/assets/69300288-11de-4df3-95cd-ba66754afc36" />

# Data Cleaning

# Date Formatting 

For the data I would like it to be dd-mmm-yyyy.

To do so I selected all of the Order Dates then went to format cells and changed it to custom.

<img width="605" height="482" alt="Screenshot 2025-12-02 at 11 35 44 PM" src="https://github.com/user-attachments/assets/10b0f2e8-3c2c-4f79-b931-786aa19d0fd7" />

# Number Formatting

currently we can't see the metric for the size.

<img width="71" height="225" alt="Screenshot 2025-12-02 at 11 39 18 PM" src="https://github.com/user-attachments/assets/8941858d-164a-429e-9baa-bc69d0a4add0" />

To change this I selected all of the cells, went to format cells, and then again went to custom to change it to display kg after the number.

<img width="632" height="391" alt="Screenshot 2025-12-02 at 11 42 16 PM" src="https://github.com/user-attachments/assets/a0b1d413-c9b7-466e-b708-300d76e6bef2" />

Size is now displaying kg after the number 

<img width="81" height="279" alt="Screenshot 2025-12-02 at 11 43 46 PM" src="https://github.com/user-attachments/assets/5fb14116-ad93-484b-9e03-bfc000cf78f3" />

Next we will format Unite Price and Sales to USD.

I selected all rows under Unit Price and Sales then went to numbers and selected USD. 

The Price and Sales columns are now in USD.

<img width="642" height="367" alt="Screenshot 2025-12-02 at 11 48 19 PM" src="https://github.com/user-attachments/assets/121aad40-c443-4030-a3f1-60031f78c555" />

# Checking For Duplicate Values

I selected the entire sheet, then went to the data tab and selected remove duplicates.

<img width="487" height="324" alt="Screenshot 2025-12-02 at 11 58 41 PM" src="https://github.com/user-attachments/assets/8e0bedc8-fb34-4cda-b128-b5af24b86df8" />

<img width="258" height="161" alt="Screenshot 2025-12-02 at 11 59 24 PM" src="https://github.com/user-attachments/assets/ca3d6a0f-5bf4-4b62-8925-be921f17f139" />

I am now comfortable that my data has no duplicates. 

# 4. Analyze

# Converting Range To Table

I selected all the coluns and rows then went to insert and Table. Selected all the rows and checked header. 

<img width="1272" height="421" alt="Screenshot 2025-12-03 at 12 13 32 AM" src="https://github.com/user-attachments/assets/56798efe-8df5-429c-89ce-9ef2081cc3b1" />

I then named the table to "Orders" Table. 

Also changed the table style to something nicer to look at.

# Pivot Table 

Inserting a Pivot Table 

Insert -> Piviot Table -> Range: Orders table -> new sheet -> ok

I named the table and sheet TotalSales and inserted Order Date into rows.

<img width="117" height="135" alt="Screenshot 2025-12-03 at 12 25 03 AM" src="https://github.com/user-attachments/assets/e2e12a40-8d5b-4ac0-b7cc-762925fd4a6d" />

I want years and months so i will have to change the grouping.

<img width="252" height="385" alt="Screenshot 2025-12-03 at 12 27 27 AM" src="https://github.com/user-attachments/assets/89d48895-1937-4aff-98db-4102234c6dc5" />

In table design, i changed report layout to Tabular Form, and turned off Grand Totals and Subtotals.

I added Coffee Type Name to columns. Dragged Sales to Value

In sales i went to format and changed the number to display no decimal points.

<img width="697" height="593" alt="Screenshot 2025-12-03 at 12 34 31 AM" src="https://github.com/user-attachments/assets/32771a2d-27b4-43e0-b2d4-7da63e82cdd5" />

# Pivot Chart 

I am now ready to insert my Pivot Chart.

Insert -> Line Chart 2d

<img width="559" height="432" alt="Screenshot 2025-12-03 at 12 39 59 AM" src="https://github.com/user-attachments/assets/87ac1a9a-3732-43ed-92b4-4f4467b568d9" />

Now i will format the chart. I changed colors, made it look better, and added titles 

<img width="780" height="455" alt="Screenshot 2025-12-03 at 1 02 46 AM" src="https://github.com/user-attachments/assets/09a2b784-2f94-453d-bd8f-766f3fbf371a" />

# Timeline

Next i will insert a timeline.

<img width="352" height="329" alt="Screenshot 2025-12-03 at 1 04 05 AM" src="https://github.com/user-attachments/assets/5e97b624-f110-4c2b-9929-f3c1403876eb" />

Then make a duplicate of the timeline style so i can modify the format and change the colors.

And we end up with this.

<img width="722" height="555" alt="Screenshot 2025-12-03 at 1 28 21 AM" src="https://github.com/user-attachments/assets/d8b6e2ed-88a4-40da-bc27-1fbfe390fea0" />

Next I will be adding slicers to filter the data.

Click on chart -> pivot chart analyzer -> insert slicer -> then selected size and roast type name -> hit okay.

I realized i also want loyalty card member to be added so i went back to the Orders sheet.

In column P1 i added a column named Loyalty Card and filled the cells loyalty card data from the cells in the customers sheet.

<img width="229" height="276" alt="Screenshot 2025-12-03 at 1 56 06 AM" src="https://github.com/user-attachments/assets/f839ca08-a162-4ebc-89d7-c92500d98bb0" />

I then went back to my pivot table and refreshed it. I was now able to add the Loyalty Card slicer.

<img width="725" height="453" alt="Screenshot 2025-12-03 at 1 59 39 AM" src="https://github.com/user-attachments/assets/f44348a1-b28f-4b38-b7df-339637d277c9" />

<img width="750" height="742" alt="Screenshot 2025-12-03 at 2 00 53 AM" src="https://github.com/user-attachments/assets/a269bd81-4dbc-4045-9e2d-706cd3d23ce0" />


Formatting the slicers. Changing colors to match the dashboard and changing size and layout.

<img width="1459" height="852" alt="Screenshot 2025-12-03 at 2 06 53 AM" src="https://github.com/user-attachments/assets/0b02f36c-5f26-4662-bdfb-eed83fb5a3e9" />

Now that im happy with that its time to make the sales by country and top 5 customers bar charts.

# Bar Charts

To start i copy the pivot table into a new sheet to ensure i use the same pivot table so that the slicers work on all the graphs.


# Sales By Country

I add Countrys into the rows and Sales into values.

Insert -> Bar Chart

<img width="804" height="595" alt="Screenshot 2025-12-03 at 2 19 37 AM" src="https://github.com/user-attachments/assets/e73ffb3d-a0ed-4b6d-9e40-18eba60cc017" />

I want the top Sales Counrty to come at the top and lowest at the bottom, so I sort ascending with sum of sales.

<img width="705" height="472" alt="Screenshot 2025-12-03 at 2 22 29 AM" src="https://github.com/user-attachments/assets/89328b1e-be17-464f-b602-865170e0863f" />

Formatting the bar graph adding data lables and changing the sum of sales to currency with no decimal points.

<img width="1228" height="638" alt="Screenshot 2025-12-03 at 2 30 40 AM" src="https://github.com/user-attachments/assets/93ba6d97-76e0-4a6c-9610-3af68f9a32d8" />

# Top Five Customers

I again started by duplicating the sheet. I removed Country and replaced it with Customer Name.

I then added a filter sorting by sum of sales and then to show only the top 10 which i reduced to show only the top 5. I then filtered ascending. 

Formated the graph to match the others and changed the title.

<img width="859" height="373" alt="Screenshot 2025-12-03 at 2 40 44 AM" src="https://github.com/user-attachments/assets/a35fc6fe-da82-493d-9153-7d416bb434fc" />

I now have everything to create my Dashboard.

# Dashboard

I copied and cut all the visuals prevoiusly made and paste them into a new sheet I titled Dashboard.
I used insert a shape to make a banner and placed a title in the center named "Coffee Sales Dashboard"

<img width="1002" height="569" alt="Screenshot 2025-12-03 at 2 56 43 AM" src="https://github.com/user-attachments/assets/4a439d20-a12b-4946-ad35-eaaf79794fb7" />

<img width="1379" height="582" alt="Screenshot 2025-12-03 at 3 11 49 AM" src="https://github.com/user-attachments/assets/5985f8c3-1fd6-44e4-9d1a-29cf3b87ef4c" />

Next thing to do is make my timeline and slicers work on all of the graphs. To do this i clicked on the timeline and then Report Connections and selected all of the sheets. I repeated that step for each slicer.


<img width="614" height="338" alt="Screenshot 2025-12-03 at 3 13 55 AM" src="https://github.com/user-attachments/assets/786c402f-a4be-4d07-beaf-39b613ede5d5" />

# 5. Share

# The Finished Working Dashboard

<img width="1290" height="572" alt="Screenshot 2025-12-03 at 2 46 25 PM" src="https://github.com/user-attachments/assets/98b18861-2390-4d18-bd23-d017fe004f7f" />

Download Dashboard and Excel sheets: [Coffee sales dashboard.xlsx](https://github.com/user-attachments/files/23915464/Coffee.sales.dashboard.xlsx)
