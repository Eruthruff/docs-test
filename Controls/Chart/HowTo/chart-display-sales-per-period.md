---
title: Display Sales Info Using Bar and Column Series
meta_title: Display Sales Info Using Bar and Column Series
meta_description: description.
slug: 
tags:display,sales,info,using,bar,and,column,series
publish:True
---


Column and Bar charts are convenient mechanisms for displaying sales data to the user. The main difference between the two is the orientation –
				Column charts have a vertical alignment whereas Bar charts display the data horizontally. The Telerik RadChart for Windows 8 HTML is an extremely
				flexible control, allowing you to create different types of charts based on the configuration settings, either set in markup or through JavaScript.
			

In this article, you will learn how to display sales data for certain periods of time using Column and Bar series.
			

# Section1Example 1: Using Already Aggregated Data

When your data is already calculated, you can directly use them as categories and the corresponding values as series values. Here is what you
					can do:
				

* 

For the series object, set the values, name, and type:

* 

Sales Values – *16.7, 20, 15.7, 26.6, 23.5*

* 

Name – *Performance Summary*

* 

Type – *column (or bar)*

* 

For the control itself, set the categories, legend location, and title:

* 

Categories – *2005, 2006, 2007, 2008, 2009*

* 

Legend – *Performance Summary*

* 

Title – *Sales by Year*


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart"
					data-win-options="{
					series: [
					{
						data: [16.7, 20, 15.7, 26.6, 23.5],
						name: 'Performance Summary',
						type: 'column'
					}],
					categoryAxis: {
						categories: [2005, 2006, 2007, 2008, 2009],
					},
					legend: { position: 'top' },
								title: { text: 'Sales by Year' }
				}">
				</div>



The result will look like this:

__Column Chart__![Simple sales column chart](../Media/Controls\Chart\chart-sales-simple-column.png)

__Bar Chart__![Simple sales bar chart](../Media/Controls\Chart\chart-sales-simple-bar.png)

# Example 2: Using the Aggregate Feature of the Series

Even if the data you have is not summarized, RadChart can display aggregated values per year (or other period of time, controlled by the
					[baseUnit](5469340a-fd03-4793-9b78-aafcda0bf923) property of the category axis). The following example, displays aggregated sales
					for 2008 and 2009. 
				


 __js__
    


		salesData: [
			{ Date: "2009/11/30", Value: 8.7 },
			{ Date: "2009/8/30", Value: 5.5 },
			{ Date: "2009/5/30", Value: 4.5 },
			{ Date: "2009/2/30", Value: 4.8 },
			{ Date: "2008/11/30", Value: 10 },
			{ Date: "2008/8/30", Value: 6.3 },
			{ Date: "2008/5/30", Value: 5 },
			{ Date: "2008/2/30", Value: 5.3 }
		]



The steps to follow are:

* 

For the series object, set the values, name, type and aggregate:

* 

Field – *'Value'*

* 

Name – *Performance Summary*

* 

Type – *column (or bar)*

* 

Aggregate - *min*; you could use another aggregate function, if needed (e.g. 'min', 'avg' etc.)
								

* 

For the control itself, set the categories (with a specified base unit and type), legend location, and title:

* 

Categories – taken from the *Date* field, using *years* as base unit.
								

* 

Legend – *Performance Summary*

* 

Title – *Sales by Year*


 __html__
    


				<div id="chart2" data-win-control="Telerik.UI.RadChart"
					data-win-options="{
					dataSource: {
						data: DefaultData.salesData,
						sort: { field: 'Date', dir: 'asc' }
					},
					series: [{
						field: 'Value',
						name: 'Performance Summary',
						type: 'column',
						aggregate: 'sum'
					}],
					categoryAxis: {
						field: 'Date',
						baseUnit: 'years',
						type: 'date'
					},
					legend: { position: 'top' },
					title: { text: 'Sales by Year' }
				}">
				</div>



The result will look like this:

__Column Chart__![Aggregates sales column chart](../Media/Controls\Chart\chart-sales-aggregate-column.png)

__Bar Chart__![Aggregated sales bar chart](../Media/Controls\Chart\chart-sales-aggregate-bar.png)

# Related Topics

 * [Category Axis]({{slug:category-axis}})

 * [Chart Legend]({{slug:chart-legend}})

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})
