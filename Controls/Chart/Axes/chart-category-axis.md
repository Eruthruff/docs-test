---
title: Category Axis
meta_title: Category Axis
meta_description: description.
slug: 
tags:category,axis
publish:True
---


In Cartesian charts, the category axis is used to represent the category to which the data point value belongs.
				RadChart's __categoryAxis__ property is used to configure the category axis settings.
			

# category-axisConfiguring Category Axis

The __categories__ property of the category axis is used to define the set of categories that will appear
					on the category axis:
				


 __html__
    


				<div id="declarativeCategoryAxisChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								data: [15.7, 16.7, 20, 23.5, 26.6]
							}],
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							},
							height: 200,
							width: 300
							}">
				</div>




 __js__
    


					var categoryAxisChartCtrl = new Telerik.UI.RadChart(document.getElementById("categoryAxisChart"), { height: 200, width: 300 });
					var columnSeries = new Telerik.UI.Chart.ColumnSeries();
					columnSeries.data = [15.7, 16.7, 20, 23.5, 26.6];
					categoryAxisChartCtrl.series.push(columnSeries);
	
					categoryAxisChartCtrl.categoryAxis.categories = [2005, 2006, 2007, 2008, 2009];
					categoryAxisChartCtrl.refresh();



The category name can also be bound to a field of the data item when a dataSource is used.
				


 __js__
    


		internetUsers: [{
			"country": "United States",
			"year": "2005",
			"value": 67.96
		}, {
			"country": "United States",
			"year": "2006",
			"value": 68.93




 __html__
    


				<div id="boundChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
								data: ChartAxis.Data.internetUsers
							},
							series: [{
								field: 'value',
								name: 'United States'
							}],
							categoryAxis: {
								field: 'year'
							},
							height: 200,
							width: 300
							}">
				</div>



# Displaying Dates

The category axis provides built-in support for displaying dates. This includes:
						

* 

Automatic selection of granularity/base unit (minutes, hours, days, etc.)

* 

Label formatting matched to the granularity

* 

Grouping of categories into base units and series aggregates

Specifying categories of type Date will switch the axis to date mode.
						


 __js__
    


					var displayingDatesChartCtrl = new Telerik.UI.RadChart(document.getElementById("displayingDatesChart"), {
						series: [{
							data: [15.7, 16.7, 20, 23.5, 26.6]
						}],
						categoryAxis: {
							baseUnit: "years",
	
							categories: [
								new Date("2011/12/30"),
								new Date("2011/12/31"),
								new Date("2012/01/01"),
								new Date("2012/01/02"),
								new Date("2012/01/03")
							]
						},
						height: 180,
						width: 300
					});

![chart-bar-series-dates](../Media/Controls\Chart\chart-bar-series-dates.png)

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
							__categoryAxis.labels.dateFormats__ property. The __categoryAxis.labels.format__ property takes priority, if specified.
						

# Controlling Categories Position

In Line and Area series, you can decide whether data points and category labels will be visualized on major ticks or
							between them. This is done using the __justified__ property. Its default value is __true__, meaning that
							categories and series are positioned on major ticks. This removes the empty space in the plot area before and after the
							series. As it would not have meaning in such scenarios, this option is ignored for Bar, Column, Ohlc or Candlestick series.
						


 __html__
    


				<div id="justifiedSample" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{
						type: 'line',
						name: 'Profit',
						data: [2200, 2500, 1800, 2400, 2300],
					}],
					categoryAxis: {
						justified: true,
						categories: ['Cat1', 'Cat2', 'Cat3', 'Cat4', 'Cat5']
					}
				}">
				</div>



The image below shows the difference between setting __justified__ to true and false in a line chart.
						![chart-common-justified](../Media/Controls\Chart\chart-common-justified.png)

# Related Topics
