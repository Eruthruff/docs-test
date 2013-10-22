---
title: Value Axis
meta_title: Value Axis
meta_description: description.
slug: 
tags:value,axis
publish:True
---


In categorical charts, data points are plotted on the value axis. RadChart currently supports only numeric value axes.

# value-axisConfiguring Value Axis

Value axis settings are configured  through the __valueAxis__ property. The configuration options are listed
					in the [Common Configuration](5469340a-fd03-4793-9b78-aafcda0bf923) article. Properties of the Axis class
					which target axes having Date values will not take any effect on a value axis.
				

Sample definitions of a value axis are shown in the code sample below. They ensure that the axis start value is 0 and the end value is 100:


 __html__
    


				<div id="declarativeValueAxisChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
								data: [15.7, 16.7, 20, 23.5, 26.6]
							}],
							valueAxis: {
								min: 0,
								max: 100
							},
							categoryAxis: {
								categories: [2005, 2006, 2007, 2008, 2009]
							},
							height: 200,
							width: 300
							}">
				</div>




 __js__
    


					var valueAxisChartCtrl = new Telerik.UI.RadChart(document.getElementById("valueAxisChart"));
					valueAxisChartCtrl.valueAxis.min = 0;
					valueAxisChartCtrl.valueAxis.max = 100;
					valueAxisChartCtrl.width = 300;
					valueAxisChartCtrl.height = 200;
	
					var columnSeries = new Telerik.UI.Chart.ColumnSeries();
					columnSeries.data = [15.7, 16.7, 20, 23.5, 26.6];
					valueAxisChartCtrl.series.push(columnSeries);
	
					valueAxisChartCtrl.categoryAxis.categories = [2005, 2006, 2007, 2008, 2009];
					valueAxisChartCtrl.refresh();



# Related Topics
