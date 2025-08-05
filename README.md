
POWER BI
DAX FORMULAS  
15
 Essential
 DAX Functions
 Every Power BI Developer Must Master!
02
 AGGREGATION FUNCTIONS: 
codebasics.io
 Aggregation functions involve summarizing or combining numerical data to 
provide insights such as totals, averages, counts, minima, and maxima. 
1
 SUM: 
Returns the sum of all the numbers in a column. 
Syntax:
 Example: 
‘Sales’ Table:
 SUM(ColumnName)
 Calculate the total quantity sold. 
Transaction ID
 1
 2
 3
 4
 5
 Explanation:
 Quantity
 2
 1
 Product ID
 Quantity
 Price
 Region
 A 2 500 North
 B 1 800 South
 A 3 450 North
 C 1 900 West
 B 2 850 South
 SUM
 3
 1
 2
 Qty Sold=SUM(Sales[Quantity])
 9
 Qty Sold=SUM(2+1+3+1+2)
 Qty Sold=9
03
 2
 AVERAGE:
 codebasics.io
 Returns the average (arithmetic mean) of all the numbers in a column. 
Syntax:
 Example: 
‘Sales’ Table:
 AVERAGE(ColumnName)
 Calculate the average price of transactions. 
Transaction ID
 1
 2
 3
 4
 5
 Product ID
 A
 B
 A
 C
 B
 Quantity Price
 Region
 2 500 North
 1
 800
 South
 3 450 North
 1
 900
 West
 2 850 South
 Explanation:
 Price
 500
 800
 450
 900
 AVERAGE
 AVG Price=
 AVERAGE(Sales[Price])
 700
 850
 AVG Price=
 (500+800+450+900+850)/5
 AVG Price=700
04
 3
 codebasics.io
 MIN: 
Returns the smallest value in a column, or between two scalar expressions. 
Syntax:
 Example: 
‘Sales’ Table:
 MIN(ColumnName) or MIN(Expression1, Expression2) 
Find the smallest price.
 Transaction ID
 1
 Product ID
 A
 Quantity Price
 Region
 2 500 North
 2
 3
 4
 5
 Explanation:
 Price
 500
 800
 450
 900
 B
 A
 C
 B
 MINIMUM
 1
 800
 South
 3 450 North
 1
 900
 West
 2 850 South
 MIN Price=
 MIN(Sales[Price])
 450
 850
 MIN Price=
 MIN(500,800,450,900,850)
 MIN Price=450
05
 4
 MAX: 
codebasics.io
 Returns the largest value in a column, or between two scalar expressions. 
Syntax:
 Example: 
‘Sales’ Table:
 MAX(ColumnName) or MAX(Expression1, Expression2) 
Find the largest price. 
Transaction ID
 1
 Product ID
 A
 Quantity Price
 Region
 2 500 North
 2
 3
 4
 5
 Explanation:
 Price
 500
 800
 450
 900
 B
 A
 C
 B
 MAXIMUM
 1
 800
 South
 3 450 North
 1
 900
 West
 2 850 South
 MAX Price=
 MAX(Sales[Price])
 900
 850
 MAX Price=
 MAX(500,800,450,900,850)
 MIN Price=900
06
 "X" FUNCTIONS FOR AGGREGATION:
 codebasics.io
 The major drawback of basic aggregate functions is that they cannot perform 
f
 iltering/row-by-row evaluation while aggregating values. 'X' functions help in 
overcoming this drawback. 
The "X" functions perform two main steps:
 They iterate over each row in the specified table or a set of rows. 
Iteration:
 Aggregation:
 SUMX: 
After applying the given expression to each row, they 
aggregate these individual results into a single value. 
Returns the sum of an expression evaluated for each row in a table. 
Syntax:
 Example: 
‘Sales’ Table:
 SUMX(Table, Expression)
 Calculate the total sales value (Quantity * Price for each transaction). 
Transaction ID
 1
 2
 3
 4
 Product ID
 A
 B
 A
 Quantity
 2
 1
 Price
 500
 Region
 800
 3
 C
 5
 Explanation:
 Quantity
 2
 B
 Price
 500
 Applying
 condition
 Quantity*
 Price
 1
 3
 1
 2
 800
 450
 1
 2
 450
 900
 850
 North
 South
 North
 West
 South
 1000
 800
 900
 850
 1350
 900
 SUM
 1700
 Total Price=
 SUMX(Sales,Sales[Quantity]*Sales[Price])
 Total Price=
 2*500+1*800+3*450+1*900+850
 5750
 Total Price=
 100+800+1350+900+1700
 Total Price=5750
 The other 'X' functions in DAX, such as AVGX, MINX, MAXX, and others, work similarly 
to SUMX by allowing for row-by-row evaluation of an expression across a table or 
table expression, and then performing the respective aggregation operation based 
on the results of that evaluation. 
07
 FILTER FUNCTIONS: 
codebasics.io
 Filtering functions are a crucial part of DAX, providing the capability to 
manipulate data context, which is fundamental for creating dynamic and 
context-sensitive calculations. 
5
 CALCULATE: 
Modifies the filter context for a given expression.
 Syntax:
 Example: 
‘Sales’ Table:
 CALCULATE(Expression, [Filter1, Filter2,…]) 
Calculate the total quantity sold for the 'North' region. 
Transaction ID
 1
 Product ID
 Quantity
 Price
 A 2 500 North
 2
 3
 4
 5
 Explanation:
 Transaction ID
 1
 B 1 800 South
 A 3 450 North
 Product ID
 A
 3
 Quantity
 2
 3
 SUM
 Region
 C 1 900 West
 B 2 850 South
 Quantity
 2
 A
 3
 5
 Price
 500
 400
 Region
 North
 North
 North QTY= 
CALCULATE(SUM(Sales[Quantity]),
 Sales[Region]="North")
 North QTY= 2+3
 North QTY= 5
08
 6
 FILTER: 
codebasics.io
 Returns a table that includes only the rows that meet a certain condition. 
Syntax:
 Example: 
FILTER(Expression,Filter)
 Filters transactions over North region.
 ‘Sales’ Table:
 Transaction ID
 1
 2
 3
 4
 5
 Product ID
 A
 B
 A
 C
 B
 Quantity
 2
 1
 3
 1
 North QTY= 
FILTER(Sales,Sales[Region]=”North”)
 Explanation:
 Transaction ID
 Price
 500
 800
 450
 900
 2
 Product ID
 1
 3
 A
 Quantity
 850
 Price
 Region
 North
 South
 North
 West
 South
 Region
 2
 A
 3
 500
 400
 North
 North
09
 7
 Syntax:
 Example: 
‘Sales’ Table:
 Transaction ID
 Explanation:
 Total QTY= 
CALCULATE(SUM(Sales[Quantity]), ALL(Region)
 Total QTY=2+1+3+1+2
 Total QTY=9
 Without Filters:
 codebasics.io
 ALL: 
Returns all rows in a table or all values in a column ignoring any filters that might 
have been applied. 
ALL(TableName or ColumnName, [Column1,…]) 
Calculate the total quantity ignoring the Region filter.
 Product ID
 1
 Quantity
 Price
 A 2 500 North
 2
 3
 4
 5
 B 1 800 South
 A 3 450 North
 Region
 C 1 900 West
 B 2 850 South
 Qty Sold=SUM(Sales[Quantity])
 Qty Sold=SUM(2+1+3+1+2)
 Qty Sold=9
 With
 Filters:
10
 8
 Syntax:
 Example: 
‘Sales’ Table:
 Transaction ID
 Explanation:
 Total QTY= 
CALCULATE(SUM(Sales[Quantity]), ALLEXCEPT(Region)
 Total QTY=2+1+3+1+2
 Total QTY=9
 With Other Filters:
 codebasics.io
 ALLEXCEPT:
 Removes all context filters in the table except filters that have been applied to the 
specified columns. 
ALLEXCEPT(TableName, Column1,[Column2,…]) 
Calculate the total quantity ignoring all filters except the Region filter.
 Product ID
 1
 Quantity
 Price
 A 2 500 North
 2
 3
 4
 5
 B 1 800 South
 A 3 450 North
 C 1 900 West
 Region
 B 2 850 South
 With Region Filter:
11
 codebasics.io
 TABLE MANIPULATION FUNCTIONS: 
These functions return a table or manipulate existing tables.
 9
 DISTINCT: 
Returns a table containing only distinct rows.
 Syntax: DISTINCT(TableName)
 Returns a column of unique values. 
Syntax:
 Example: 
‘Sales’ Table:
 DISTINCT(ColumnName) 
List unique product IDs sold. 
Transaction ID
 1
 Product ID
 A
 Quantity
 2
 Price
 500
 Region
 North
 2 B 1 800 South
 3 A 3 450 North
 4 C 1 900 West
 5
 Explanation:
 B
 2
 Products=DISTINCT(Sales[ProductID]) 
Product ID
 A
 B
 850
 South
 C
12
 MATH AND TRIG FUNCTIONS:
 codebasics.io
 These are functions in DAX that allow for the execution of mathematical and 
trigonometric operations on data. 
10
 ABS:
 Returns the absolute value of a number. 
Syntax: ABS(Number) 
Example: 
11
 ABS(10-15) 
5 
DIVIDE:
 Performs division and returns an alternate result or BLANK on division by 0. 
Syntax: DIVIDE(Numerator, Denominator, [AlternateResult]) 
Example: 
= DIVIDE(8,2,0) 
= 4 
Example: 
DIVIDE(3,0,0) 
= 0 
13
 LOGICAL FUNCTIONS:
 codebasics.io
 Logical functions act upon an expression to return information about the values 
or sets in the expression. 
12
 IF:
 Checks a condition, and returns one value if True, and another value if False. 
Syntax: IF(LogicTest, ResultIfTrue, [ResultIfFalse])
 Example: 
‘Sales’ Table:
 Categorize transactions as 'High' or 'Low' based on price. 
Transaction ID
 1
 2
 3
 4
 5
 Explanation:
 Price
 500
 800
 Product ID
 A
 B
 A
 C
 B
 Applying
 condition
 450
 900
 Quantity
 2
 1
 1
 Price
 500
 800
 Region
 North
 South
 3 450 North
 900
 2
 850
 Category = IF(Sales[Price] >= 800, "High", "Low")
 Category
 Low
 High
 Low
 High
 850
 High
 West
 South
14
 13
 SWITCH: 
codebasics.io
 Evaluates an expression against a list of values and returns the result 
corresponding to the first matching value. 
Syntax: SWITCH(Expression, Value1, Result1, Value2, Result2, …,
 [DefaultResult]) 
Example: 
‘Sales’ Table:
 Categorize transactions as 'High Price' or ‘Medium Price’ or 'Low Price' 
based on price.
 Transaction ID
 1
 2
 3
 4
 5
 Explanation:
 )
 Price
 500
 800
 450
 Product ID
 A
 B
 A
 C
 B
 Quantity
 2
 1
 1
 2
 Price
 500
 800
 Region
 North
 South
 3 450 North
 900
 850
 West
 South
 Price Category = SWITCH(TRUE(),
    Sales[Price] >= 800, "High Price",
    Sales[Price] >= 500 && Sales[Price] < 800, "Medium Price",
    Sales[Price] < 500, "Low Price",
    "Undefined" // Default case if no other conditions are met
 Applying
 condition
 900
 850
 Price Category
 Medium Price
 High Price
 Low Price
 High Price
 High Price
15
 RELATIONSHIP FUNCTIONS:
 codebasics.io
 Relationship functions facilitate data flow between tables when there is an 
established relationship between them. 
15
 RELATED: 
Returns a related value from another table.
 Syntax: RELATED(ColumnName) 
Example: 
‘Sales’ Table:
 Retrieve related product details for sales transactions. 
Transaction ID
 1
 2
 3
 4
 5
 ‘Products’ Table:
 Product ID
 A
 Product ID
 A
 B
 A
 Quantity
 2
 1
 3
 C
 B
 1
 2
 Price
 500
 800
 450
 Product Name
 Widget
 B
 C
 Explanation:
 Transaction ID
 1
 Gadget
 Other
 900
 850
 Quantity
 Electronics
 Home
 Electronics
 Region
 North
 South
 North
 West
 South
 Product Details = RELATED(Products[ProductName])
 Product ID
 A
 Quantity
 2
 Price
 500
 Region
 North
 2 B 1 800 South
 3 A 3 450 North
 Category Price Category Product Category
 Low
 Medium Price
 High
 Low
 4 C 1 900 West
 5 B 2 850 South
 High
 High Price
 Low Price
 High Price
 High Price
 Widget
 Gadget
 Widget
 Other
 Gadget
 High
16
 15
 RELATEDTABLE: 
codebasics.io
 Retrieves a table of rows related to the current row context based on an existing 
relationship. 
Syntax: RELATEDTABLE(TableName) 
Example: 
Retrieve related average price for each category. 
‘Products’ Table:
 Product ID
 A
 B
 Product Name
 Widget
 Quantity
 Electronics
 Gadget
 C
 ‘Sales’ Table:
 Transaction ID
 1
 Explanation:
 Product ID
 A
 Other
 Product ID
 A
 Home
 Electronics
 Quantity
 Price
 2
 500
 Region
 North
 2 B 1 800 South
 3 A 3 450 North
 4 C 1 900 West
 5 B 2 850 South
 AVG Price=
 CALCULATE(AVERAGE(Sales[Price]),RELATEDTABLE(sales_data))
 Product ID
 Widget
 B
 C
 Gadget
 Category
 Electronics
 AVG Price
 Home
 Other
 Electronics
 475
 825
 900
Enab l i ng Career s
 Found this interesting?
 Dive deeper!
 Check this Free Power BI Project
 Join our YT community of 1M learners
 codebasics. io


## 🚀 About Me
I'm a full stack developer...


![Logo](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/th5xamgrr6se0x5ro4g6.png)


POWER BI
DAX FORMULAS  
15
 Essential
 DAX Functions
 Every Power BI Developer Must Master!
02
 AGGREGATION FUNCTIONS: 
codebasics.io
 Aggregation functions involve summarizing or combining numerical data to 
provide insights such as totals, averages, counts, minima, and maxima. 
1
 SUM: 
Returns the sum of all the numbers in a column. 
Syntax:
 Example: 
‘Sales’ Table:
 SUM(ColumnName)
 Calculate the total quantity sold. 
Transaction ID
 1
 2
 3
 4
 5
 Explanation:
 Quantity
 2
 1
 Product ID
 Quantity
 Price
 Region
 A 2 500 North
 B 1 800 South
 A 3 450 North
 C 1 900 West
 B 2 850 South
 SUM
 3
 1
 2
 Qty Sold=SUM(Sales[Quantity])
 9
 Qty Sold=SUM(2+1+3+1+2)
 Qty Sold=9
03
 2
 AVERAGE:
 codebasics.io
 Returns the average (arithmetic mean) of all the numbers in a column. 
Syntax:
 Example: 
‘Sales’ Table:
 AVERAGE(ColumnName)
 Calculate the average price of transactions. 
Transaction ID
 1
 2
 3
 4
 5
 Product ID
 A
 B
 A
 C
 B
 Quantity Price
 Region
 2 500 North
 1
 800
 South
 3 450 North
 1
 900
 West
 2 850 South
 Explanation:
 Price
 500
 800
 450
 900
 AVERAGE
 AVG Price=
 AVERAGE(Sales[Price])
 700
 850
 AVG Price=
 (500+800+450+900+850)/5
 AVG Price=700
04
 3
 codebasics.io
 MIN: 
Returns the smallest value in a column, or between two scalar expressions. 
Syntax:
 Example: 
‘Sales’ Table:
 MIN(ColumnName) or MIN(Expression1, Expression2) 
Find the smallest price.
 Transaction ID
 1
 Product ID
 A
 Quantity Price
 Region
 2 500 North
 2
 3
 4
 5
 Explanation:
 Price
 500
 800
 450
 900
 B
 A
 C
 B
 MINIMUM
 1
 800
 South
 3 450 North
 1
 900
 West
 2 850 South
 MIN Price=
 MIN(Sales[Price])
 450
 850
 MIN Price=
 MIN(500,800,450,900,850)
 MIN Price=450
05
 4
 MAX: 
codebasics.io
 Returns the largest value in a column, or between two scalar expressions. 
Syntax:
 Example: 
‘Sales’ Table:
 MAX(ColumnName) or MAX(Expression1, Expression2) 
Find the largest price. 
Transaction ID
 1
 Product ID
 A
 Quantity Price
 Region
 2 500 North
 2
 3
 4
 5
 Explanation:
 Price
 500
 800
 450
 900
 B
 A
 C
 B
 MAXIMUM
 1
 800
 South
 3 450 North
 1
 900
 West
 2 850 South
 MAX Price=
 MAX(Sales[Price])
 900
 850
 MAX Price=
 MAX(500,800,450,900,850)
 MIN Price=900
06
 "X" FUNCTIONS FOR AGGREGATION:
 codebasics.io
 The major drawback of basic aggregate functions is that they cannot perform 
f
 iltering/row-by-row evaluation while aggregating values. 'X' functions help in 
overcoming this drawback. 
The "X" functions perform two main steps:
 They iterate over each row in the specified table or a set of rows. 
Iteration:
 Aggregation:
 SUMX: 
After applying the given expression to each row, they 
aggregate these individual results into a single value. 
Returns the sum of an expression evaluated for each row in a table. 
Syntax:
 Example: 
‘Sales’ Table:
 SUMX(Table, Expression)
 Calculate the total sales value (Quantity * Price for each transaction). 
Transaction ID
 1
 2
 3
 4
 Product ID
 A
 B
 A
 Quantity
 2
 1
 Price
 500
 Region
 800
 3
 C
 5
 Explanation:
 Quantity
 2
 B
 Price
 500
 Applying
 condition
 Quantity*
 Price
 1
 3
 1
 2
 800
 450
 1
 2
 450
 900
 850
 North
 South
 North
 West
 South
 1000
 800
 900
 850
 1350
 900
 SUM
 1700
 Total Price=
 SUMX(Sales,Sales[Quantity]*Sales[Price])
 Total Price=
 2*500+1*800+3*450+1*900+850
 5750
 Total Price=
 100+800+1350+900+1700
 Total Price=5750
 The other 'X' functions in DAX, such as AVGX, MINX, MAXX, and others, work similarly 
to SUMX by allowing for row-by-row evaluation of an expression across a table or 
table expression, and then performing the respective aggregation operation based 
on the results of that evaluation. 
07
 FILTER FUNCTIONS: 
codebasics.io
 Filtering functions are a crucial part of DAX, providing the capability to 
manipulate data context, which is fundamental for creating dynamic and 
context-sensitive calculations. 
5
 CALCULATE: 
Modifies the filter context for a given expression.
 Syntax:
 Example: 
‘Sales’ Table:
 CALCULATE(Expression, [Filter1, Filter2,…]) 
Calculate the total quantity sold for the 'North' region. 
Transaction ID
 1
 Product ID
 Quantity
 Price
 A 2 500 North
 2
 3
 4
 5
 Explanation:
 Transaction ID
 1
 B 1 800 South
 A 3 450 North
 Product ID
 A
 3
 Quantity
 2
 3
 SUM
 Region
 C 1 900 West
 B 2 850 South
 Quantity
 2
 A
 3
 5
 Price
 500
 400
 Region
 North
 North
 North QTY= 
CALCULATE(SUM(Sales[Quantity]),
 Sales[Region]="North")
 North QTY= 2+3
 North QTY= 5
08
 6
 FILTER: 
codebasics.io
 Returns a table that includes only the rows that meet a certain condition. 
Syntax:
 Example: 
FILTER(Expression,Filter)
 Filters transactions over North region.
 ‘Sales’ Table:
 Transaction ID
 1
 2
 3
 4
 5
 Product ID
 A
 B
 A
 C
 B
 Quantity
 2
 1
 3
 1
 North QTY= 
FILTER(Sales,Sales[Region]=”North”)
 Explanation:
 Transaction ID
 Price
 500
 800
 450
 900
 2
 Product ID
 1
 3
 A
 Quantity
 850
 Price
 Region
 North
 South
 North
 West
 South
 Region
 2
 A
 3
 500
 400
 North
 North
09
 7
 Syntax:
 Example: 
‘Sales’ Table:
 Transaction ID
 Explanation:
 Total QTY= 
CALCULATE(SUM(Sales[Quantity]), ALL(Region)
 Total QTY=2+1+3+1+2
 Total QTY=9
 Without Filters:
 codebasics.io
 ALL: 
Returns all rows in a table or all values in a column ignoring any filters that might 
have been applied. 
ALL(TableName or ColumnName, [Column1,…]) 
Calculate the total quantity ignoring the Region filter.
 Product ID
 1
 Quantity
 Price
 A 2 500 North
 2
 3
 4
 5
 B 1 800 South
 A 3 450 North
 Region
 C 1 900 West
 B 2 850 South
 Qty Sold=SUM(Sales[Quantity])
 Qty Sold=SUM(2+1+3+1+2)
 Qty Sold=9
 With
 Filters:
10
 8
 Syntax:
 Example: 
‘Sales’ Table:
 Transaction ID
 Explanation:
 Total QTY= 
CALCULATE(SUM(Sales[Quantity]), ALLEXCEPT(Region)
 Total QTY=2+1+3+1+2
 Total QTY=9
 With Other Filters:
 codebasics.io
 ALLEXCEPT:
 Removes all context filters in the table except filters that have been applied to the 
specified columns. 
ALLEXCEPT(TableName, Column1,[Column2,…]) 
Calculate the total quantity ignoring all filters except the Region filter.
 Product ID
 1
 Quantity
 Price
 A 2 500 North
 2
 3
 4
 5
 B 1 800 South
 A 3 450 North
 C 1 900 West
 Region
 B 2 850 South
 With Region Filter:
11
 codebasics.io
 TABLE MANIPULATION FUNCTIONS: 
These functions return a table or manipulate existing tables.
 9
 DISTINCT: 
Returns a table containing only distinct rows.
 Syntax: DISTINCT(TableName)
 Returns a column of unique values. 
Syntax:
 Example: 
‘Sales’ Table:
 DISTINCT(ColumnName) 
List unique product IDs sold. 
Transaction ID
 1
 Product ID
 A
 Quantity
 2
 Price
 500
 Region
 North
 2 B 1 800 South
 3 A 3 450 North
 4 C 1 900 West
 5
 Explanation:
 B
 2
 Products=DISTINCT(Sales[ProductID]) 
Product ID
 A
 B
 850
 South
 C
12
 MATH AND TRIG FUNCTIONS:
 codebasics.io
 These are functions in DAX that allow for the execution of mathematical and 
trigonometric operations on data. 
10
 ABS:
 Returns the absolute value of a number. 
Syntax: ABS(Number) 
Example: 
11
 ABS(10-15) 
5 
DIVIDE:
 Performs division and returns an alternate result or BLANK on division by 0. 
Syntax: DIVIDE(Numerator, Denominator, [AlternateResult]) 
Example: 
= DIVIDE(8,2,0) 
= 4 
Example: 
DIVIDE(3,0,0) 
= 0 
13
 LOGICAL FUNCTIONS:
 codebasics.io
 Logical functions act upon an expression to return information about the values 
or sets in the expression. 
12
 IF:
 Checks a condition, and returns one value if True, and another value if False. 
Syntax: IF(LogicTest, ResultIfTrue, [ResultIfFalse])
 Example: 
‘Sales’ Table:
 Categorize transactions as 'High' or 'Low' based on price. 
Transaction ID
 1
 2
 3
 4
 5
 Explanation:
 Price
 500
 800
 Product ID
 A
 B
 A
 C
 B
 Applying
 condition
 450
 900
 Quantity
 2
 1
 1
 Price
 500
 800
 Region
 North
 South
 3 450 North
 900
 2
 850
 Category = IF(Sales[Price] >= 800, "High", "Low")
 Category
 Low
 High
 Low
 High
 850
 High
 West
 South
14
 13
 SWITCH: 
codebasics.io
 Evaluates an expression against a list of values and returns the result 
corresponding to the first matching value. 
Syntax: SWITCH(Expression, Value1, Result1, Value2, Result2, …,
 [DefaultResult]) 
Example: 
‘Sales’ Table:
 Categorize transactions as 'High Price' or ‘Medium Price’ or 'Low Price' 
based on price.
 Transaction ID
 1
 2
 3
 4
 5
 Explanation:
 )
 Price
 500
 800
 450
 Product ID
 A
 B
 A
 C
 B
 Quantity
 2
 1
 1
 2
 Price
 500
 800
 Region
 North
 South
 3 450 North
 900
 850
 West
 South
 Price Category = SWITCH(TRUE(),
    Sales[Price] >= 800, "High Price",
    Sales[Price] >= 500 && Sales[Price] < 800, "Medium Price",
    Sales[Price] < 500, "Low Price",
    "Undefined" // Default case if no other conditions are met
 Applying
 condition
 900
 850
 Price Category
 Medium Price
 High Price
 Low Price
 High Price
 High Price
15
 RELATIONSHIP FUNCTIONS:
 codebasics.io
 Relationship functions facilitate data flow between tables when there is an 
established relationship between them. 
15
 RELATED: 
Returns a related value from another table.
 Syntax: RELATED(ColumnName) 
Example: 
‘Sales’ Table:
 Retrieve related product details for sales transactions. 
Transaction ID
 1
 2
 3
 4
 5
 ‘Products’ Table:
 Product ID
 A
 Product ID
 A
 B
 A
 Quantity
 2
 1
 3
 C
 B
 1
 2
 Price
 500
 800
 450
 Product Name
 Widget
 B
 C
 Explanation:
 Transaction ID
 1
 Gadget
 Other
 900
 850
 Quantity
 Electronics
 Home
 Electronics
 Region
 North
 South
 North
 West
 South
 Product Details = RELATED(Products[ProductName])
 Product ID
 A
 Quantity
 2
 Price
 500
 Region
 North
 2 B 1 800 South
 3 A 3 450 North
 Category Price Category Product Category
 Low
 Medium Price
 High
 Low
 4 C 1 900 West
 5 B 2 850 South
 High
 High Price
 Low Price
 High Price
 High Price
 Widget
 Gadget
 Widget
 Other
 Gadget
 High
16
 15
 RELATEDTABLE: 
codebasics.io
 Retrieves a table of rows related to the current row context based on an existing 
relationship. 
Syntax: RELATEDTABLE(TableName) 
Example: 
Retrieve related average price for each category. 
‘Products’ Table:
 Product ID
 A
 B
 Product Name
 Widget
 Quantity
 Electronics
 Gadget
 C
 ‘Sales’ Table:
 Transaction ID
 1
 Explanation:
 Product ID
 A
 Other
 Product ID
 A
 Home
 Electronics
 Quantity
 Price
 2
 500
 Region
 North
 2 B 1 800 South
 3 A 3 450 North
 4 C 1 900 West
 5 B 2 850 South
 AVG Price=
 CALCULATE(AVERAGE(Sales[Price]),RELATEDTABLE(sales_data))
 Product ID
 Widget
 B
 C
 Gadget
 Category
 Electronics
 AVG Price
 Home
 Other
 Electronics
 475
 825
 900
Enab l i ng Career s
 Found this interesting?
 Dive deeper!
 Check this Free Power BI Project
 Join our YT community of 1M learners
 codebasics. io

