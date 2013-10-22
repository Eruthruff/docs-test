---
title: Candlestick
meta_title: Candlestick
meta_description: description.
slug: 
tags:candlestick
publish:True
---


The Candlestick series are used primarily to describe price movements of a security, derivative, or currency over time. They are a combination
				of a Line series and a Bar series, in that each bar represents the range of price movement over a given time interval. They are most often used in
				technical analysis of equity and currency price patterns. Candlestick series is another way of displaying market price data, with the opening and
				closing prices defining a rectangle within the range for each time unit. Both series show exactly the same data, i.e., the opening, high, low,
				and closing prices during a particular time frame. Some traders find the
				candlestick series easier to read.
			![Candlestick series](../Media/Controls\Chart\chart-candlestick-series.png)

# Defining a Candlestick Series Declaratively

To define Candlestick series in HTML, add an object with __type__ property set to "candlestick" to the
					__series__ array:
				


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{
							type: 'candlestick',
							openField: 'Open',
							highField: 'High',
							lowField: 'Low',
							closeField: 'Close',
							data: DefaultData.dataSource
						}
					]
				}">
				</div>



Here, *DefaultData.dataSource* is an array of objects similar to the one shown below:
				


 __js__
    


		dataSource: [
	    {
	    	Date: "2000/01/03",
	    	Open: 41.62,
	    	High: 41.69,
	    	Low: 39.81,
	    	Close: 40.12,
	    	Volume: 2632000,
	    	DownColor: "#014E82"
	    },
		//...



# Defining a Candlestick Series Programmatically

To programmatically a Candlestick series to the chart, create a new __Telerik.UI.Chart.CandleStickSeries__ object and
					add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__ to have the
					changes take effect:
				


 __js__
    


					var chart2Ctrl = new Telerik.UI.RadChart(document.getElementById("chart2"), {
						dataSource: {
							data: DefaultData.dataSource
						}
					});
	
					var candlestickSeries = new Telerik.UI.Chart.CandleStickSeries();
					candlestickSeries.openField = "Open";
					candlestickSeries.highField = "High";
					candlestickSeries.lowField = "Low";
					candlestickSeries.closeField = "Close";
					chart2Ctrl.series.push(candlestickSeries);
					chart2Ctrl.refresh();



# Configuring a Candlestick Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Candlestick series. 
				

# Setting the Fields

There are four fields defining the candlesticks position and shape:

* 

__openField__: the data field containing the open value.
								

* 

__highField__: the data field containing the high value.
								

* 

__lowField__: the data field containing the low value.
								

* 

__closeField__: the data field containing the close value.
								

Additionally, to visualize the values even better, you can provide a data source containing specific colors. To color each candlestick use the
							__colorField__ property; and for the scenarios where the open value is smaller than the close value you
							should assign the name of the field containing a valid CSS color to the __downColorField__ property.
						


 __html__
    


				<div id="chart3" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{
							type: 'candlestick',
							openField: 'Open',
							highField: 'High',
							lowField: 'Low',
							closeField: 'Close',
							downColorField: 'DownColor',
							data: DefaultData.dataSource
						}
					]
				}">
				</div>

![Setting fields](../Media/Controls\Chart\chart-candlestick-series-fields.png)

# Using Custom Colors

Apart from getting the color for the series from the chart's datasource, you can also specify static colors through the
							__downColor__ property (as well as the __color__ property derived from the base
							__Series__ class.
						


 __html__
    


				<div id="chart4" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{
							type: 'candlestick',
							openField: 'Open',
							highField: 'High',
							lowField: 'Low',
							closeField: 'Close',
							color: 'green',
							downColor: 'yellow',
							data: DefaultData.dataSource
						}
					]
				}">
				</div>



The following image shows the results of using each of these properties in a Candlestick series.![Customizing colors](../Media/Controls\Chart\chart-candlestick-series-colors.png)

# Using Aggregates

Through the __aggregate__ property you can set an aggregate function for date series. This function is used when a
							category (a year, month, etc.) contains two or more points. The function return values are displayed instead of the individual points. For
							a Candlestick series, you can set a function to each of the variables: __open__, __high__, 
							__low__, __close__.
						

The accepted aggregate functions are:

* 

__"max"__: The highest value for the date period.
								

* 

__"min"__: The lowest value for the date period.
								

* 

__"sum"__: The sum of all values for the date period.
								

* 

__"count"__: The number of values for the date period.
								

* 

__"avg"__: The average of all values for the date period.
								

* 

__function (values, series)__: Custom-defined aggregate function.
								


 __html__
    


				<div id="chart5" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{
							type: 'candlestick',
							openField: 'Open',
							highField: 'High',
							lowField: 'Low',
							closeField: 'Close',
							aggregate: {
								open: 'min',
								high: 'max',
								low: 'min',
								close: 'min'	
							}
						}
					],
					dataSource: {
						data: DefaultData.dataSourceForAggregation
					},
					categoryAxis: {
						field: 'Date',
						baseUnit: 'months',
						type: 'date'
					}
				}">
				</div>



Here, *DefaultData.dataSourceForAggregation* is an array of objects similar to the one shown below:
						


 __js__
    


		dataSourceForAggregation: [
		{
			Date: "2000/01/03",
			Open: 41.62,
			High: 41.69,
			Low: 39.81,
			Close: 40.12,
			Volume: 2632000,
			DownColor: "#014E82"
		},
		//...



This is the result from the above definition:![Applying aggregate](../Media/Controls\Chart\chart-candlestick-series-aggregate.png)

# Assigning a Value Axis

When you have multiple value axes, you can assign the Candlestick series to one of them, using the axis option. The property defaults to
							the primary axis.
						


 __html__
    


				<div id="chart6" data-win-control="Telerik.UI.RadChart" data-win-options="{
					dataSource: {
						data: DefaultData.dataSource
					},
					series: [
						{
							 type: 'candlestick',
							 name: 'Company 1',
							 openField: 'Open',
							 highField: 'High',
							 lowField: 'Low',
							 closeField: 'Close',
							 axis: 'axis1',
							 gap: 1,
							 spacing: 1
						}
					],
					valueAxis: [{
						name: 'axis1'
					}, {
						name: 'axis2'
					}]
				}">
				</div>

![Assigning value axis](../Media/Controls\Chart\chart-candlestick-series-value-axis.png)

# Line Settings

The __line__ property gets the line settings for the Candlestick series. It exposes three options for customizing the
							border line of the rectangle rendered by the series: __color__, __opacity__,
							__width__.
						

Example:


 __html__
    


				<div id="chart7" data-win-control="Telerik.UI.RadChart" data-win-options="{
					dataSource: {
						data: DefaultData.dataSource
					},
					series: [
						{
							type: 'candlestick',
							openField: 'Open',
							highField: 'High',
							lowField: 'Low',
							closeField: 'Close',
							line: {
								color:'#336699',
								width:10,
								opacity: 0.3
							}
						}
					]
				}">
				</div>



And the result:![Line settings](../Media/Controls\Chart\chart-candlestick-series-line-settings.png)

# Controlling the Distance Between Categories

Based on your requirement, you can increase or decrease the space between category clusters. This is done by setting the __gap__
              property to an appropriate numeric value. This value represents the proportion between the space between category clusters and the candlestick width 
              (i.e. "gap: 4" means that the candlestick width will be one fourth of the space between category clusters):
            


 __html__
    


				<div id="chart8" data-win-control="Telerik.UI.RadChart" data-win-options="{
					dataSource: {
						data: DefaultData.dataSource
					},
					series: [
						{
							type: 'candlestick',
							openField: 'Open',
							highField: 'High',
							lowField: 'Low',
							closeField: 'Close',
							gap: 4
						}
					]
				}">
				</div>

![Setting gap](../Media/Controls\Chart\chart-candlestick-series-gap.png)

# Controlling the distance between the candlesticks

You can also increase or decrease the space between candlesticks belonging to one and the same category by setting
							the __spacing__ property to an appropriate numeric value. This value represents the proportion between the space between
              candlesticks in a single category and the candlestick width (i.e. "spacing: 0.2" means that the candlestick width will be five times the space 
              between category clusters).
            


 __html__
    


				<div id="chart9" data-win-control="Telerik.UI.RadChart" data-win-options="{
					dataSource: {
						data: DefaultData.dataSource
					},
					series: [
						{
							 type: 'candlestick',
							 openField: 'Open',
							 highField: 'High',
							 lowField: 'Low',
							 closeField: 'Close',
							 axis: 'ax1',
							 spacing: 2,
							 gap: 3
						},
						{
							 type: 'candlestick',
							 openField: 'Open',
							 highField: 'High',
							 lowField: 'Low',
							 closeField: 'Close',
							 axis: 'ax2',
							 spacing: 2,
							 gap: 2
						}
					],
					valueAxis: [
						{
							name: 'ax1'
						}, 
						{
							name: 'ax2'
						}
					]
				}">
				</div>

![Setting series spacing](../Media/Controls\Chart\chart-candlestick-series-spacing.png)

# Related Topics

 * [Ohlc]({{slug:ohlc}})
