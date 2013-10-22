---
title: Vertical Bullet
meta_title: Vertical Bullet
meta_description: description.
slug: 
tags:vertical,bullet
publish:True
---


The Vertical Bullet chart can be used to visualize one or more data points, consisting of two values - a current value, represented by a column, and a target
				value, represented by a line at the same X position as the column. They can be used to represent comparison between an expected and actual value in different
				scenarios - company profit, people's performance, weather measures, etc.
			![chart-vertical-bullet-series](../Media/Controls\Chart\chart-vertical-bullet-series.png)

# 
				Defining a Vertical Bullet Series Declaratively
			

To define a vertical bullet series in HTML, add an object with __type__ property set to "verticalBullet"
				to the __series__ array.
				


 __html__
    


				<div id="declarativeVerticalBulletSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'verticalBullet',
						data: [[17, 35],
							   [20, 37],
							   [36, 24],
							   [30, 38],
							   [23, 35],
							   [45, 87],
							   [67, 74],
							   [12, 38]]
					}],
					theme: 'light',
					width: 400
				}">
				</div>



# 
				Defining Vertical Bullet Series Programmatically
			

To programmatically add a Vertical Bullet series to the chart, create a new __Telerik.UI.Chart.VerticalBulletSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect.
				


 __js__
    


					var verticalBulletSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("verticalBulletSeriesChart"));
					var verticalBulletSeries = new Telerik.UI.Chart.VerticalBulletSeries();
					verticalBulletSeries.data = [[17, 35], [20, 37], [36, 45], [30, 38], [23, 35], [45, 87], [67, 74], [12, 38]];
					verticalBulletSeriesChartCtrl.series.push(verticalBulletSeries);
					verticalBulletSeriesChartCtrl.refresh();



# Configuring Vertical Bullet Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific ones that you can use to customize the look and behavior of the Vertical Bullet series.  As they are identical to the Bullet series, you
					can check their description [here](d4c0df77-be37-4294-ac60-59148e45ba06).
				

# Related Topics

 * [Bullet]({{slug:bullet}})

 * [Common Configuration]({{slug:common-configuration}})
