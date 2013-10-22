---
title: Area Series
meta_title: Area Series
meta_description: description.
slug: 
tags:area,series
publish:True
---


Area series visualize data as a portion of the Cartesian coordinate system. Categories are laid out
				on the X-axis, while values go on the Y-axis.
			![chart-area-series](../Media/Controls\Chart\chart-area-series.png)

# 
				Defining an Area Series Declaratively
			

To define an area series in the HTML, add an object with __type__ property set to "area"
					to the __series__ array.
				


 __html__
    


				<div id="declarativeAreaSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
							type: 'area', 
							name: 'World', 
							data: [16.7, 20, 15.7, 26.6, 23.5] 
						}
					]
				}">
				</div>



# 
				Defining an Area Series Programmatically
			

To programmatically add an area series to a chart, create a new __Telerik.UI.Chart.AreaSeries__
					object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call __refresh()__
					to have the changes take effect:
				


 __js__
    


					var areaSeriesChartCtrl = new Telerik.UI.RadChart(document.getElementById("areaSeriesChart"));
					var areaSeries = new Telerik.UI.Chart.AreaSeries();
					areaSeries.data = [16.7, 20, 15.7, 26.6, 23.5];
					areaSeriesChartCtrl.series.push(areaSeries);
					areaSeriesChartCtrl.refresh();



# Configuring Area Series

Apart from the common configuration settings listed in [this article](15e0c300-a141-495d-9355-3d2d35951bd4), there a few more
					specific configuration settings that you can use to customize the look and behavior of the Area series.
				

# Line Settings

The __line__ property gets the line setting for the area series. It exposes three options for customizing the border line of the
							rendered area: __color__, __opacity__, __width__.
						

Example:


 __html__
    


				<div id="lineSettingsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series:[{
						name: 'Example Series',
						type: 'area',
						data: [16.7, 20, 15.7, 26.6, 23.5],
						line: {
							color:'#336699',
							width:10,
							opacity: 0.3
						}
							}]
				}">
				</div>



The image here shows the result.![Line settings](../Media/Controls\Chart\chart-area-series-line.png)

# Customizing Markers

You can set a few options that change what a data point looks like in an Area series by setting the __markers__ property.
							The options you can set include __background__, __border__ settings, __size__, 
							__type__ (circle, square or triangle) and __visible__.
						


 __html__
    


				<div id="markersSettingsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series:[{
						name: 'Example Series',
						type: 'area',
						data: [16.7, 20, 15.7, 26.6, 23.5],
						markers: {
							type: 'triangle',
							background: '#fff',
							size:10,
							border:{
								width:1
							}
						}
					}]
				}">
				</div>

![Markers settings](../Media/Controls\Chart\chart-area-series-markers.png)

# Handling Missing Values

There are three different options to handle missing values in your chart when using Area series. They are presented by the 
							__missingValues__ property, which accepts the following values:

* 

__gap__: The line stops before missing point and continues after it (default value).
								

* 

__interpolate__: The value is interpolated from neighboring points
								

* 

__zero__: The value is assumed to be zero.
								

In the example below,the missing value is assumed to be zero:


 __html__
    


				<div id="missingValuesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series:[{
						name: 'Example Series',
						type: 'area',
						missingValues: 'zero',
						field: 'value'
					}],
					dataSource: {
						data:[{
								value: 40,
								category: 'Apples'
							}, 
							{
								category: 'Pears',
							},
							{
								value: 20,
								category: 'Peaches'
							},
							{
								value: 60,
								category: 'Oranges'
						}]
					}
				}">
				</div>



This chart shows the missingValues property set to zero:![Handling missing values](../Media/Controls\Chart\chart-area-series-missing-values.png)

# Related Topics

 * [Vertical Area Series]({{slug:vertical-area-series}})
