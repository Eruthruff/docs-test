---
title: Vertical Line Series
meta_title: Vertical Line Series
meta_description: description.
slug: 
tags:vertical,line,series
publish:True
---


Vertical Line series visualize data as a continuous line on a Cartesian coordinate system. Categories are laid out
				on the Y-axis, while values go on the X-axis.
			![chart-vertical-line-series](../Media/Controls\Chart\chart-vertical-line-series.png)

# 
				Defining a Vertical Line Series Declaratively
			

To define a Vertical Line series in HTML, add an object with __type__ property set to "verticalLine"
				to the __series__ array.
				


 __html__
    


				<div id="declarativeVerticalLineSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ type: 'verticalLine', name: 'World', data: [16.7, 20, 15.7, 26.6, 23.5] }
					]
				}">
				</div>



# 
				Defining a Vertical Line Series Programmatically
			

To programmatically add a Vertical Line series to the chart, create a new __Telerik.UI.Chart.VerticalLineSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var verticalLineSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("verticalLineSeriesChart"));
					var verticalLineSeries = new Telerik.UI.Chart.VerticalLineSeries();
					verticalLineSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					verticalLineSeriesChartCtrl.series.push(verticalLineSeries);
					verticalLineSeriesChartCtrl.refresh();



# Configuring a Vertical Line Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					that you can use to customize the look and behavior of the Vertical Line series. As they are identical to the regular (horizontal) Line series, you
					can check their description [here](53149c9c-fffe-4443-9a03-1c49fddaacd5).
				

# Related Topics

 * [Vertical Line Series]({{slug:vertical-line-series}})
