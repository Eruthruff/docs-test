---
title: Scatter Series
meta_title: Scatter Series
meta_description: description.
slug: 
tags:scatter,series
publish:True
---


Scatter series are suitable for visualizing two-dimensional data on a Cartesian coordinate system. The two axes, X and Y,
				both represent data values. Each data point in the series is represented by a pair of values - the X value and the Y value.
			![Scatter series](../Media/Controls\Chart\chart-scatter-series.png)

# 
				Defining a Scatter Series Declaratively
			

To define a Scatter series in HTML, add an object with __type__ property set to "scatter"
				to the __series__ array.
				


 __html__
    


				<div id="declarativeScatterSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'scatter', 
						data: [[10, 10], [15, 20], [20, 25], [32, 40], [43, 50], [55, 60], [60, 70], [70, 80]] 
						}
				]}">
				</div>



# 
				Defining a Scatter Series Programmatically
			

To programmatically add a scatter series to the chart, create a new __Telerik.UI.Chart.ScatterSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var scatterSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("scatterSeriesChart"));
					var scatterSeries = new Telerik.UI.Chart.ScatterSeries();
					scatterSeries.data = [[10, 10], [15, 20], [20, 25], [32, 40], [43, 50], [55, 60], [60, 70], [70, 80]];
					scatterSeriesChartCtrl.series.push(scatterSeries);
					scatterSeriesChartCtrl.refresh();



# Configuring a Scatter Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Scatter series.
				

# Setting X- and Y-fields

Positioning the data points in a Scatter series is done using X and Y values. When your chart is bound to non-trivial data, you could use the
							__xField__ and __yField__ properties to specify from which fields in the datasource, the coordinates 
							should be taken.
						


 __html__
    


				<div id="xyFieldsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
					  type: 'scatter',
					  xField: 'Quantity',
					  yField: 'Value'
					}],
					dataSource: {
						data: [
							{Quantity: 10, Value: 10},
							{Quantity: 12, Value: 5},
							{Quantity: 9, Value: 19},
							{Quantity: 15, Value: 13},
							{Quantity: 25, Value: 10},
							{Quantity: 32, Value: 18}
						] 				
					}
				}">
				</div>

![Setting fields](../Media/Controls\Chart\chart-scatter-fields.png)

# Using Multiple Axes

When you want to display multiple Scatter series in one chart, you could you the __xAxis__ and __yAxis__ properties
							to assign different axes for the series.
						


 __html__
    


				<div id="multipleAxesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
						  series: [{
							  type: 'scatter', 
							  data: [
									  {Year: 2001, Value: 10000},
									  {Year: 2003, Value: 11000},
									  {Year: 2005, Value: 19000},
									  {Year: 2007, Value: 16000},
									  {Year: 2009, Value: 20000},
									  {Year: 2011, Value: 18000}
							  ] ,
							  xField: 'Year',
							  yField: 'Value',
							  yAxis: 'Sales',
							  name: 'Sales'
						  },
							  {
							  type: 'scatter', 
							  data: [
									  {Year: 2001, Expense: 8000},
									  {Year: 2003, Expense: 5000},
									  {Year: 2005, Expense: 8000},
									  {Year: 2007, Expense: 13000},
									  {Year: 2009, Expense: 14000},
									  {Year: 2011, Expense: 12000}
							  ] ,			 			   
							  xField: 'Year',
							  yField: 'Expense',
							  yAxis: 'Production',
							  name: 'Production'
						  }],
							  yAxis: [{
								  name: 'Sales'
							  },
							  {
								  name: 'Production'
							  }
							  ]
							  }">
				</div>



This will produce two Scatter series, colored differently, using the primary X-axis and a separate Y-axis each.![Using multiple axes](../Media/Controls\Chart\chart-scatter-series-multiple-axes.png)

# Customizing Markers

You can set a few options that change what a data point looks like in a Scatter series by setting the __markers__ options. They include:
							__background__, __border__ settings, __size__, __type__ (circle, square or triangle) and
							__visible__.
						


 __html__
    


				<div id="customMarkersChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
					  type: 'scatter', 
					  xField: 'Year',
					  yField: 'Value',
					  markers: {
						  border: {
							  color: 'green',
							  width: 2
						  },
						  type: 'triangle',
						  size:12
					  }
					}],
					dataSource: {
					  data: [
							  {Year: 2001, Value: 5000},
							  {Year: 2002, Value: 7500},
							  {Year: 2002, Value: 9000},
							  {Year: 2004, Value: 8000},
							  {Year: 2005, Value: 12000},
							  {Year: 2006, Value: 18000},
							  {Year: 2007, Value: 16000},
							  {Year: 2008, Value: 19000},
							  {Year: 2009, Value: 16000},
							  {Year: 2010, Value: 20000},
							  {Year: 2011, Value: 18000}
					  ] ,
					}
				}">
				</div>

![chart-scatter-series-markers](../Media/Controls\Chart\chart-scatter-series-markers.png)

# Related Topics

 * [Scatter Line Series]({{slug:scatter-line-series}})

 * [Bubble Series]({{slug:bubble-series}})
