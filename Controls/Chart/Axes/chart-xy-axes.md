---
title: X and Y Axes
meta_title: X and Y Axes
meta_description: description.
slug: 
tags:x,and,y,axes
publish:True
---


Charts series such as Scatter, Scatter Line and Bubble use two value axes - the X and Y axes. The __xAxis__
			and __yAxis__ properties in RadChart are used to configure the two value axes when an XY type of series is defined.
		

# xy-axesConfiguring X and Y Axes

X and Y axes settings are configured  through the __xAxis__ and __yAxis__ properties. 
				  The configuration options are listed in the [Common Configuration](5469340a-fd03-4793-9b78-aafcda0bf923)
				  article. As opposed to the value axis in a categorical chart, the X and Y axes have built-in support for displaying dates.
			  


 __html__
    


				<div id="declarativeXYAxesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								type: 'scatter',
								name: 'Pentium D 915',
								data: [[120, 102]]
							}],
							xAxis: {
								max: 1000
							},
							yAxis: {
								min: 80
							},
							height: 180,
							width: 400
							}">
				</div>




 __js__
    


					var xyAxesChartCtrl = new Telerik.UI.RadChart(document.getElementById("xyAxesChart"));
					xyAxesChartCtrl.xAxis.max = 1000;
					xyAxesChartCtrl.yAxis.min = 80;
					xyAxesChartCtrl.height = 200;
					xyAxesChartCtrl.width = 400;
	
					var scatterSeries = new Telerik.UI.Chart.ScatterSeries();
					scatterSeries.name = "Pentium D 915";
					scatterSeries.data = [[120, 102]];
					xyAxesChartCtrl.series.push(scatterSeries);
	
					xyAxesChartCtrl.refresh();



# Displaying Dates

The built-in dates support includes:
					  

* 

Automatic selection of granularity/base unit (minutes, hours, days, etc.)
							  

* 

Label formatting matched to the granularity
							  

The axis will switch to date mode if the series values are of type Date. The automatic mode selection can be overriden by specifying type: "Date".
					  

The following axis properties accept dates:
					  

* 

min

* 

max

* 

axisCrossingValue

The following axis properties are expressed in base units:
					  

* 

minorUnit

* 

majorUnit


 __js__
    


					var xyDateSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("xyDateSeriesChart"), {
						series: [
						 {
						 	type: 'scatter',
						 	data: [
									{ Year: new Date(2001, 1, 1), Expense: 8000 },
									{ Year: new Date(2002, 1, 1), Expense: 9000 },
									{ Year: new Date(2003, 1, 1), Expense: 12000 },
									{ Year: new Date(2004, 1, 1), Expense: 18000 },
									{ Year: new Date(2005, 1, 1), Expense: 16000 }
						 	],
						 	xField: 'Year',
						 	yField: 'Expense',
						 	name: 'Production'
						 }],
						xAxis: {
							min: new Date(2001, 12, 12)
						},
						width: 500,
						height: 250
					});

![chart-axes-xy-dates](../Media/Controls\Chart\chart-axes-xy-dates.png)

The base unit can also be specified manually. Valid options are:
					  

* 

seconds

* 

minutes

* 

hours

* 

days

* 

weeks

* 

months

* 

years

If you set __baseUnit__ property to *"weeks"*, you can use the __weekStartDay__
						  property to define the day which should be considered to be the first in the week. The value should be a number from 0 to 6 where 0 corresponds to Sunday,
						  1—to Monday and so on.
					  

The format of the displayed date values on the categorical axis can be specified through the
						  __labels.format__ property of the axis.
					  

# Related Topics
