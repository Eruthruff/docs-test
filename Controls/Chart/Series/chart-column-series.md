---
title: Column Series
meta_title: Column Series
meta_description: description.
slug: 
tags:column,series
publish:True
---


Column series visualize data in vertical columns in a Cartesian coordinate system. Categories are
				laid out on the X-axis, while values go on the Y-axis.
			![chart-column-series](../Media/Controls\Chart\chart-column-series.png)

# 
				Defining a Column Series Declaratively
			

To define a Column series in HTML, add an object with __type__ property set to "column"
				to the __series__ array.
				


 __html__
    


				<div id="declarativeColumnSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [
						{ type: 'column', name: 'World', data: [16.7, 20, 15.7, 26.6, 23.5] }
					]
				}">
				</div>



# 
				Defining a Column Series Programmatically
			

To programmatically add a Column series to the chart, create a new __Telerik.UI.Chart.ColumnSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var columnSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("columnSeriesChart"));
					var columnSeries = new Telerik.UI.Chart.ColumnSeries();
					columnSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					columnSeriesChartCtrl.series.push(columnSeries);
					columnSeriesChartCtrl.refresh();



# Configuring Column Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					that you can use to customize the look and behavior of the Column series. As they are identical to the Bar series' settings, you
					can check their description [here](bb03ac0d-401c-45fe-872e-7e4501570e84).
				

# Related Topics

 * [Bar Series]({{slug:bar-series}})
