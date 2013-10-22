---
title: Axes
meta_title: Axes
meta_description: description.
slug: 
tags:axes
publish:True
---


RadSparkLine displays categorical (discrete) charts and has an implicit category and value axis. The awareness for their existence is important even though they
				are not typically visible. The axis orientation is inferred from the series type.
			

This help article describes the specifics you would need to know about the category and value axes in RadSparkline.

# Section1Category Axis

The category axis is used to represent the category to which a data point value belongs. While category names are not visible by default, they will be displayed in tooltips.
					RadSparkline's __categoryAxis__ property is used to configure the category axis settings.
				

To provide category names, use the __categoryAxis.categories__ property, as shown below:
				


 __html__
    


				<span id="line" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'line',
					data: [952, 940, 937, 980],
					categoryAxis: {
						categories: [2010, 2011, 2012, 2013]
					},
					height: 50,
					width: 100,
					theme: 'light'
				}"></span>

![sparkline-axes-categories](../Media/Controls\Sparkline\sparkline-axes-categories.png)

If RadSparkline is bound to a Telerik.Data.DataSource and you want to use one of the data fields as source of category names, use the
					__categoryAxis.field__ property.
				

# Displaying Dates

The category axis provides built-in support for displaying dates. This includes:
						

* 

Automatic selection of granularity/base unit (minutes, hours, days, etc.)

* 

Label formatting matched to the granularity

* 

Grouping of categories into base units and series aggregates

Specifying categories of type Date will switch the axis to date mode.
						

The base unit can also be specified manually. Valid options are:
						

* 

minutes

* 

hours

* 

days

* 

months

* 

years

Below, you can see an example of RadSparkline using a Date field to populate its category axis:


 __xml__
    


				<span id="column" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					dataSource: {
						data: SampleData.salesPerDate
					},
					series: [
						{
							type: 'column',
							field: 'Value',
							aggregate: 'sum'
						}
					],
					categoryAxis: {
						field: 'Date',
						type: 'date',
						baseUnit: 'years',
						crosshair: {
							visible: false
						}
					},
					tooltip: {
						sharedTemplate: '&lt;strong&gt; #=category.getFullYear()# &lt;/strong&gt;: #=points[0].value#'
					},
					height: 50,
					width: 50,
					theme: 'light'
				}"></span>



The example data has the following structure:


 __js__
    


	var salesData = [
	
		{ Date: new Date(2008, 11, 30), Value: 10 },
		{ Date: new Date(2008, 8, 30), Value: 6.3 },
		{ Date: new Date(2008, 5, 30), Value: 5 },
		{ Date: new Date(2008, 2, 30), Value: 5.3 },
		{ Date: new Date(2009, 11, 30), Value: 8.7 },
		{ Date: new Date(2009, 8, 30), Value: 5.5 },
		{ Date: new Date(2009, 5, 30), Value: 4.5 },
		{ Date: new Date(2009, 2, 30), Value: 4.8 }
	]



This is how the result looks:![sparkline-axes-dates](../Media/Controls\Sparkline\sparkline-axes-dates.png)

# Aggregates

In the above example we defined an __aggregate__ property for the series. If more than one category
							falls within a base unit, then its values are aggregated to display a single point. To display an aggregated value that fits your requirements, you
							can change the aggregates function by setting this __aggregate__ property for the series.
						

Available options are:

* 

min

* 

max

* 

count

* 

sum

* 

avg

* 

function (values, series) - custom aggregate

# Value Axis

In a categorical chart like RadSparkline, data points are plotted on the value axis. RadSparkline currently supports only numeric value axes.
						

When you want to explicitly define the values at which the axis will start
							and end, use the __min__ and __max__ properties. Their default values are 0 and 1 respectively.
							Once the sparkline is aware of its data, the max value is dynamically changed to be larger than all values belonging to the current axis.
						

Setting different min and max values for the axis produces different scale for the drawn series. For example, the following declaration
							produces the sparkline below it:
						


 __xml__
    


				<span id="vlueAxisSettingsSparkline" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'area',
					data: [955, 998, 970, 980],
					valueAxis: {
						min: 950,
						max: 1000
					},
					width: 100,
					height: 100,
					theme: 'light'
				}"></span>

![sparkline-axes-value 1](../Media/Controls\Sparkline\sparkline-axes-value_1.png)

Now, if you change the __min__ property value to 700, the same sparkline will look like this:
						![sparkline-axes-value 2](../Media/Controls\Sparkline\sparkline-axes-value_2.png)

# Related Topics
