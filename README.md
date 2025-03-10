            REPORTS USING FILTER FUNCTIONS IN DAX



Dashboard Link :https://app.powerbi.com/groups/me/reports/958ce70a-52a2-4cfa-bd10-14def2c01f7a/8b18b8a997bc61941fc6?experience=power-bi



Procedure:

1.Importing the Dataset:
	Launch Power BI Desktop.
	Click on "Get Data" in the Home tab of the ribbon.
	Select the appropriate data source option "Excel” and follow the prompts to import yoursample dataset into Power BI.
	Select sample-super store data,xsl
	Select orders table from the check-boxws.

2.	Insert Rectangle Shape:




	Click on “Format tab” on right side and perform changes on visual.
	Shape > Style > #E66C37
	Shape > Text >Text = “Page1” , Font Size = 46, Horizontal Alignment = “Center”.
 


3.	Create Table:
	Create table and place it in the report
	In the fields column drag and drop category

4.	Create Table for calculating profits:
	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
Total Profit = SUM(Orders[profit])
	Visualizations >Columns>Total profit


5.	Applying ALL-Filter:

Syntax: ALL(<table>|<column>].<column>[,…]]]])
Description: returns all the rows in a table or all the values in the column, ignoring any filters that have been applied. This function is useful for clearing filters and creating calculations or all the rows in a table
	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
All profit filter = CALCULATE([Total Profit],ALL(orders))
 


6.	Applying ALLAccept:

Syntax: ALLACCEPT(<table>|<column>].<column>[,…]]]])
Description: returns all the rows in a table or all the values in the column, ignoring any filters that have been applied except the given coulmn. This function is useful for clearing filters and creating calculations or all the rows in a table except given column.
	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
All profit Except Cat = CALCULATE([Total Profit],ALLEXCEPT(Orders,Orders[Category]))
	Visualizations >Columns>All profit Except cat




7.	calculating % of profit for each category:
	Home > Enter data > Create table by giving values to the columns

	Click on new measure>and enter the below dax formula:
%profit Cat = DIVIDE([Total Profit],[All profit filter])
	Visualizations >Columns>%profit cat
	Change the mode to %



8.	Applying filter to a particular Column:
	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
technology profit = CALCULATE([total profit],Orders[category]="Technology"]
	Visualizations >Columns>technology profit
 


9.	Applying Keep-Filter:
Syntax: KEEPFILTERS(<Expression>)
Description: Modifies how filters are applied for evaluating.

	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
(KP)Technology profit = calculate([Total Profit],keepfilters(orders[category]="Technology"))
	Visualizations >Columns>(KP)Technology Profit

10.	Applying REMOVE-Filter:

Syntax: RemoveFilter(.<column>[,…]]]])
Description: same as all filter but not returns all the rows in a table or all the values in the column, ignoring any filters that have been applied. Majorly used for reducing complexity and increasing performance. This function is useful for clearing filters and creating calculations or all the rows in a table
	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
All Profit RF filter = calculate([total profit],REMOVEFILTERS(Orders[category]))
	Visualizations >Columns>All profit RF filter
 

11.	Creating a slicer for comparision:
	Home>visulazation>build visual>select slicer
	Chose religion in the fields
	From setting change the slicer settings>
	Choose style as tile



comparison:
if region=central


if region=south:
 

if region=East:


if region=West:

12.	Create Table:
	Home > Enter data > Create table by giving values to the columns
	Click on new measure>and enter the below dax formula:
	Profit rank = RANKX(ALL(Orders[region]),[total profit],,desc
	Visualizations >Columns>religion>profit>profit rank

 
13. Final Output


![Image](https://github.com/user-attachments/assets/5669a6de-a9f8-4787-ac9a-994ab30b22ca)
