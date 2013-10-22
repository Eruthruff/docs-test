---
title: Vertical Area Series
meta_title: Vertical Area Series
meta_description: description.
slug: 
tags:vertical,area,series
publish:True
---


Vertical Area series visualize data as a portion of the Cartesian coordinate system. Categories are laid out
				on the Y-axis, while values go on the X-axis.
			![chart-vertical-area-series](../Media/Controls\Chart\chart-vertical-area-series.png)

# 
				Defining a Verttical Area Series Declaratively
			

To define a Vertical Area series in HTML, add an object with __type__ property set to "verticalArea"
				to the __series__ array.
				


 __html__
    


				<div id="declarativeVerticalAreaChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
							type: 'verticalArea', 
							name: 'World', 
							data: [16.7, 20, 15.7, 26.6, 23.5] 
						}
					]
				}">
				</div>



# 
				Defining a Vertical Area Series Programmatically
			

To programmatically add a Vertical Area series to the chart, create a new __Telerik.UI.Chart.VerticalAreaSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var verticalAreaSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("verticalAreaSeriesChart"));
					var areaSeries = new Telerik.UI.Chart.VerticalAreaSeries();
					areaSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					verticalAreaSeriesChartCtrl.series.push(areaSeries);
					verticalAreaSeriesChartCtrl.refresh();



# Configuring a Vertical Area Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					that you can use to customize the look and behavior of the Vertical Area series. As they are identical to the regular (horizontal) Area series, you
					can check their description [here](b4da469c-6173-49ac-8ee8-65b63a252615).
				

# Related Topics

 * [Area Series]({{slug:area-series}})
