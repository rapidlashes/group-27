# group-27
KEEP GOING YOU WILL CRACK THE CODE!!

# Part A
 # DATA CLEANING 
ORD -2023-521818 had a duplicate, changed one to ORD-2023-521819(order no. has to be unique)
on the city column we filled blank cells with unknown, we cant possibly tell in which city were the commoditites distributed
I swapped columns with an earlier required date with their order date,  I used the if condition first to identify them ,then sorted them all the the bottom then swapped their cells between column B and C
Calculated GrossRevenue column by  multiplying quantity  price and 1-discount rate
Calculated cost of goods column by multiplying unit cost and quantity price
Gross profit column added by subtracting Revenue from cost of goods
Marginpct calculated by dividing gross profit to gross revenue, NOTE: some products have a big negative margin percentage of upto -25000% , we assumed the distributor sold them at a loss
Standardised order date to month and year  using text function
Added quarters on order date
Merged Location by Region, Country and city using power query
to make the price band column, I had to use the percentile.inc fxn. To get a cut off point for the 0.33 percentile which in our case is the lower percentile, then did the same for the 0.67 percentile which is the middle one.
I then used the nested if function to label unit price values within the first, second and third percentile as low, medium and high respectively


# PART  B 
# 1 Cohort Analysis   
Added First order Month Column and split hierachical region to find country
Created first month each country appears column using minifs and added cohort period column using date functions i.e datedif()
Pivot table showing revenue tracked from each country's start of cohort month created

# 2 SKU ABC analysis
Created a pivot on sku products by sum of gross revenue




# 3 Sales Person Productivity
Created a pivot on  sales persons productivity by sum of sales , revenue , their total order count and distinct order days
Copied the pivot to a fresh sheet in values form
Added new columns in the table comprising of revenue per order,order per month and gross profit per order
Highlighted top 3 and bottom orders with high revenues for each sales person respectively
 

# 4 Channel Mix And Cannibalization
Created a pivot with details of how revenue is created by diff channels in each region
Converted the values to % showing how each revenue comes from the channel
Created another pivot showing the absolute total of each channel in revenue per region in the same sheet
The pivots are essential for interprating revenues contribution by each channel 

# 5 Service Level Proxy
created a column to classify orders that have met the 7 day target using lead time. For this I used the if function, if( leadtimedays<=7, 1,0)
created a pivot table of countries against product categories and added values of the orders meeting the 7 day target and those not in the respective countries.
172 orders met te target, against 632, that amounts to 27% of total orders, computed this as a KPI too.
NOTE; the values were computed as an average in the pivot table.

# 6 .Price compliance (Disc %)
 Added a new column to the data to flag  discount above and below 20%
Created a pivot showing rate of  salesperson give discounts above 20%  in each region
Added a new sheet flaging sales person giving discount above 20% named discount outliers
Highlighted extreme discount given by sales person




# Dashboarding:
finding KPIs;
total revenue is the sum of gross revenue
gross profit is (total revenue-total cost of goods)
margin %  is (gross profit/total revenue)
average order value is (total revenue/no. of orders)

# Dashboard visuals:
1.Revenue by month:computed a line grapph of revenue against std order date(added slicer for months Jan-dec)
2.profit by region:computed a column chart of Region against channle then added values of profit(added slicers for country,channel, region and sales person)
3.top 10 sku by revenue:I had to sort the revenue column by descending order, copied the first 10 rows onto another sheet and computed a bar chart of the SKUs against gross Revenue(added slicer for product category)
4.discount outliers:Box plot with whiskers(will be explained below)

# Scenario Modelling
Re-calculated the gross revenue , cost of goods and gross profit on another sheet (sheet x) called them baseline
Added a new scenario modelling criteria ,where global discount cap is 25%, quantity uplift factor 20%, unit cost inflation factor 15%
 I went back to my data set calculated column for unitcost but this time with an inflation factor of 15%(1+15%)*unitcost
Did the same with the discount %, replacing all products with a %tagediscount of more than 25% with a %tage discount of 25%,retained the rest.
Also recalculated the quantity column with a quantity uplift factor of 20%, (1+20%)*quantity
I went back to (sheetx) where I had calculated the baseline parameters , and recalculated now the scenario parameters of gross revenue, cost of goods and profit
Created a comparison table of the baseline and scenario comparing changes to discount cap , unit cost inflation and quantity uplift


# Discount outliers(box plot)
copy pasted the discount percentage column on another sheet, then went direct to insert and clicked on the statistical chart where I found the box plot 
I then inserted the box plot using the data of discount percentages
box blots are mainly used to show distribution of data


# INSIGHTS
Salesperson who made the least profit is N.rown with a gross profit of 107,713/=
Sales person who made the most profit is M.Rossi with a gross profit of 368,408/=
Only 27% of the total orders have managed to meet the leadtime days target which is less or equal to 7 days
The main channel of product distribution across all regions is generally Direct channel
Product with the largest discount is Accessories, 56.50%
Main channel of distribution of these products in Asia is Direct channel
Majority of these products have a discount percentage range of 7-15%
Most commonly sold electronic product is Printers
Main channel of distribution for these products in Africa is Marketplace
Asia is the region with the largest market of these electronic products


# GROUP MEMBERS:
Calvin Alembi(did KPIs, Dashboard visualsand DAX)
Ahmed Salim(did cleaning, and building report(dashbard and insights)
Moses
Elishiba




