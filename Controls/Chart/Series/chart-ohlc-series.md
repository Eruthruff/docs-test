---
title: Ohlc
meta_title: Ohlc
meta_description: description.
slug: 
tags:ohlc
publish:True
---


An Ohlc chart is a special financial series that is typically used to illustrate movements in the price of a financial instrument over time. Each vertical line drawn 
				by the series shows the price range (the highest and lowest prices) over one unit of time, e.g., one day or one hour. Tick marks project from each side of the line 
				indicating the opening price (e.g., for a daily Bar series this would be the starting price for that day) on the left, and the closing price for that time period on 
				the right. The bars may be shown in different hues depending on whether prices rose or fell in that period. It uses stick-like shapes to visualize its data points.
			![Ohlc series](../Media/Controls\Chart\chart-ohlc-series.png)

# Defining an Ohlc Series Declaratively

To define an Ohlc series in HTML, add an object __type__ property set to "ohlc" to the series array.
			


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [
								{
									type: 'ohlc',
									openField: 'Open',
									highField: 'High',
									lowField: 'Low',
									closeField: 'Close'
								}
							],
							dataSource: {
								data: DefaultData.dataSource
							}
						}">
				</div>



Here, *DefaultData.dataSource* is an array containing objects similar to the one shown below.
				


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



# Defining an Ohlc Series Programmatically

To programmatically add an Ohlc series to the chart, create a new __Telerik.UI.Chart.OhlcSeries__ object and
					add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__ to have the
					changes take effect.
				


 __js__
    


					var chart2Ctrl = new Telerik.UI.RadChart(document.getElementById("chart2"), {
						dataSource: {
							data: DefaultData.dataSource
						}
					});
	
					var ohlcSeries = new Telerik.UI.Chart.OhlcSeries();
					ohlcSeries.openField = "Open";
					ohlcSeries.highField = "High";
					ohlcSeries.lowField = "Low";
					ohlcSeries.closeField = "Close";
					chart2Ctrl.series.push(ohlcSeries);
					chart2Ctrl.refresh();



# Configuring an Ohlc Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					that you can use to customize the look and behavior of the ohlc series. As they are identical to the Candlestick series' settings, you
					can check their description [here](11ba012b-cff5-46da-92d4-b37b382d7efd).
				

# Related Topics

 * [Candlestick]({{slug:candlestick}})
