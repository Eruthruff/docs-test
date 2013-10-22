---
title: Bubble Series
meta_title: Bubble Series
meta_description: description.
slug: 
tags:bubble,series
publish:True
---


Bubble series visualize data points represented by three values - X-value, Y-value and size. Data is visualized as
				a circle (or bubble) on a Cartesian coordinate system, where the X and Y values of each data point represent the
				location of the circle on the two axes, while size determines the area of the circle. Bubble series are useful
				for visualizing data points that differ significantly in size values, thus plotting a relative comparison of the data.
			![Bubble Series](../Media/Controls\Chart\chart-bubble-series.png)

# 
				Defining a Bubble Series Declaratively
			

To define a Bubble series in HTML, add an object with __type__ property set to "bubble"
					to the __series__ array:
				


 __html__
    


				<div id="declarativeBubbleSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'bubble',
						data: [[17, 35, 12],
							   [20, 37, 36],
							   [36, 24, 14],
							   [30, 18, 22]]
					}],
					theme: 'light'
				}">
				</div>



# 
				Defining Bubble Series Programmatically
			

To programmatically add a Bubble series to the chart, create a new __Telerik.UI.Chart.BubbleSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var bubbleSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("bubbleSeriesChart"), {theme: 'light'});
					var bubbleSeries = new Telerik.UI.Chart.BubbleSeries();
					bubbleSeries.data = [[17, 35, 12], [20, 37, 36], [36, 24, 14], [30, 18, 22]];
					bubbleSeriesChartCtrl.series.push(bubbleSeries);
					bubbleSeriesChartCtrl.refresh();



# Configuring Bubble Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Bubble series. They follow below.
				

# Setting the Bubble Fields

There are five available field settings for the Bubble series. Here is a brief description of their usage:

* 

__xField__: The data field containing the bubble x value.
								

* 

__yField__: The data field containing the bubble y value.
								

* 

__sizeField__: The data field containing the bubble size value.
								

* 

__colorField__: The data field containing the bubble color. The field should contain valid CSS colors.
								

* 

__categoryField__: The data field containing the bubble category name. This field will be used to populate the bubble series
									tooltips.
								

A simple example of the usage of these fields follows below. Of course, it is not required to have them always set; this would mostly depend on the
							type of data you pass to the chart series.
						


 __html__
    


				<div data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bubble',
					  xField: 'Year',
					  yField: 'UnitsInStock',
					  sizeField: 'UnitPrice',
					  categoryField: 'Name',
					  colorField: 'Color'
					}],
					dataSource: {
						data: [ 
							{Year: 1980, UnitsInStock: 500, UnitPrice: 50, Color: '#ff6644', Name: 'Sales in 1980'},
							{Year: 1990, UnitsInStock: 523, UnitPrice: 310, Color: '#33ccff', Name: 'Sales in 1990'},
							{Year: 2000, UnitsInStock: 604, UnitPrice: 700, Color: '#336699', Name: 'Sales in 2000'},
							{Year: 2010, UnitsInStock: 650, UnitPrice: 1000, Color: '#11cc99', Name: 'Sales in 2010'} 
						],
					},
					tooltip: {
					  visible: true
					},
					theme: 'light'
					}">
				</div>



The resulting chart will look like this:![Setting fields](../Media/Controls\Chart\chart-bubble-series-fields.png)

# Using Multiple Axes

You can specify an x-axis and y-axis for each Bubble series that you define. This is done by setting the __xAxis__ and __yAxis__
							properties. If you do not explicitly specify them, the primary axis will be used. This way you
							can visualize related data in a single chart, as shown in the example below:
						


 __html__
    


				<div id="multipleAxesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bubble',
					  data: [ {Year: 2002, UnitsSold: 2100, UnitPrice: 50000 , Name: 'Number of units sold in 2002'},
							  {Year: 2005, UnitsSold: 4350, UnitPrice: 61000 , Name: 'Number of units sold in 2005'},
							  {Year: 2008, UnitsSold: 6040, UnitPrice: 70000, Name: 'Number of units sold in 2008'},
							  {Year: 2012, UnitsSold: 6500, UnitPrice: 100000, Name: 'Number of units sold in 2012'} 
					  ],
					  yField: 'Year',
					  xField: 'UnitsSold',
					  sizeField: 'UnitPrice',
					  categoryField: 'Name',
					  xAxis: 'sales',
					  name: 'Sales',
					  tooltip: {
						  template: '#=category#: #=dataItem.UnitsSold# &lt;br/&gt; Unit price: #=dataItem.UnitPrice# '
					  }
					},
					{
					type: 'bubble',
					data: [{Year: 2002, Offices: 1, Employees: 3, Name: 'Number of employees in 2002'},
						  {Year: 2005, Offices: 1, Employees: 15, Name: 'Number of employees in 2005'},
						  {Year: 2008, Offices: 3, Employees: 41, Name: 'Number of employees in 2008'},
						  {Year: 2012, Offices: 5, Employees: 102, Name: 'Number of employees in 2012'}],
					  yField: 'Year',
					  xField: 'Employees',
					  sizeField: 'Offices',
					  categoryField: 'Name',
					  xAxis: 'employees',
					  name: 'Employees',
					  tooltip: {
						  template:'#=category#: #=dataItem.Employees# &lt;br/&gt; Number of offices: #=dataItem.Offices#'
					  }
					}],
					xAxis: [{
					  name: 'sales'
					}, {
					  name: 'employees'
					}],
					tooltip: {
					  visible: true
					},
					theme: 'light'
					}">
				</div>

![xAxis setting](../Media/Controls\Chart\chart-bubble-series-axes.png)

# Specifying Min and Max Size for the Bubbles

To limit the size of the series, you can set numeric values of the __minSize__ and __maxSize__ properties. These
							values represent the diameter of the bubble in pixels (excluding the border). So, if you do not want the rendered bubbles to be wider than 30 pixels and narrower
							than 10, you could define the series like this:
						


 __html__
    


				<div id="minMaxSizeChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bubble',
					  yField: 'Year',
					  xField: 'UnitsSold',
					  sizeField: 'UnitPrice',
					  categoryField: 'Name',
					  maxSize: 30,
					  minSize: 10
					}],
					dataSource: {
						data: [ {Year: 2002, UnitsSold: 1000, UnitPrice: 5000},
							  {Year: 2003, UnitsSold: 2300, UnitPrice: 20000},
							  {Year: 2005, UnitsSold: 4350, UnitPrice: 67000},
							  {Year: 2008, UnitsSold: 6040, UnitPrice: 85000},
							  {Year: 2012, UnitsSold: 6500, UnitPrice: 100000} 
					    ]
					},
					theme: 'light'
					}">
				</div>



This will get you the following result:![Setting min and max value](../Media/Controls\Chart\chart-bubble-series-min-max.png)

# Handling Negative Values

Because the __size__ value is represented as a circle area, it is best to plot positive values. Negative values are not displayed by default.
							If you choose to display them, their area will be calculated as if their value was positive. You can control the visibility and color used through the
							__negativeValues__ options, or more specifically, their __color__ and __visible__ properties:
						


 __html__
    


				<div id="negativeValuesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bubble',
					  yField: 'UnitsSold',
					  xField: 'Year',
					  sizeField: 'Profit',
					  negativeValues: {
						  visible: true,
						  color:'red'
					  }
					}],
					dataSource: {
						data: [ {Year: 2002, UnitsSold: 1000, UnitPrice: 5000 , Profit: 7000},
							  {Year: 2005, UnitsSold: 4350, UnitPrice: 67000 , Profit: -1000},
							  {Year: 2008, UnitsSold: 6040, UnitPrice: 85000, Profit: -200},
							  {Year: 2009, UnitsSold: 4350, UnitPrice: 67000 , Profit: 800},
							  {Year: 2011, UnitsSold: 6040, UnitPrice: 85000, Profit: 3500}
						]
					},
					theme: 'light'
					}">
				</div>



This will produce a chart with negative values displayed and colored red.![Handling negative values](../Media/Controls\Chart\chart-bubble-series-negative-values.png)

# Adding Border to the Bubbles

From Q2 2013 on, you can also add a border to the bubbles. Use the __border__ property for this purpose. The property exposes
							three options - __color__, __dashType__ (possible values: *"solid"*,
							*"dot"*, *"dash"*, *"longDash"*,
							*"dashDot"*, *"longDashDot"*, and *"longDashDotDot"*), and
							__width__. Make sure you set width that is greater than 0 to be able to show the border.
						


 __html__
    


				<div id="borderSettingsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
					  type: 'bubble',
					  yField: 'UnitsSold',
					  xField: 'Year',
					  sizeField: 'Profit',
					  border: {
						color: '#336699',
						width: 2
					  }
					}],
					dataSource: {
						data: [ {Year: 2002, UnitsSold: 1000, UnitPrice: 5000 , Profit: 7000},
								{Year: 2003, UnitsSold: 1500, UnitPrice: 10000 , Profit: 9000},
								{Year: 2005, UnitsSold: 4350, UnitPrice: 67000 , Profit: 1000},
								{Year: 2008, UnitsSold: 6040, UnitPrice: 85000, Profit: 3500}
						]
					},
					theme: 'light'
					}">
				</div>



This will produce a chart with a darker blue border.![chart-bubble-series-border](../Media/Controls\Chart\chart-bubble-series-border.png)

# Related Topics

 * [Scatter Series]({{slug:scatter-series}})

 * [Scatter Line Series]({{slug:scatter-line-series}})
