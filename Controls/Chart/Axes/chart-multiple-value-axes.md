---
title: Use Multiple Value Axes
meta_title: Use Multiple Value Axes
meta_description: description.
slug: 
tags:use,multiple,value,axes
publish:True
---


A chart might have more than one value axis. These additional axes must have unique names. To assign a series to certain axis, set its
				axis/xAxis/yAxis property to the name of the axis you want it to use. 
			

# multiple-value-axesMultiple Value Axes

In the following code snippet there are two series and two value axes ("temperature" and "humidity") defined. Each series has its 
					__axis__ property set to the name of the corresponding value axis.
			


 __js__
    


					var multipleValueAxesChartCtrl = new Telerik.UI.RadChart(document.getElementById("multipleValueAxesChart"), {
						legend: {
							position: "bottom"
						},
						series: [{
							name: "Temperature",
							data: [20, 25, 32],
							axis: "temperature",
							color: "#1E98E4"
						}, {
							name: "Humidity",
							data: [45, 50, 80],
							axis: "humidity",
							color: "#f99"
						}
						],
						categoryAxis: {
							categories: ["Aug", "Sep", "Oct"]
						},
						valueAxis: [{
							name: "temperature",
							labels: {
								format: "{0}C"
							}
						}, {
							name: "humidity",
							labels: {
								format: "{0}%"
							}
						}],
						width: 400,
						height: 300
					});

![chart-multiple-axes](../Media/Controls\Chart\chart-multiple-axes.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/MultipleAxes*.
        

# Related Topics

 * [Category Axis]({{slug:category-axis}})

 * [Value Axis]({{slug:value-axis}})
