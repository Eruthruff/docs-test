---
title: Plot Bands
meta_title: Plot Bands
meta_description: description.
slug: 
tags:plot,bands
publish:True
---


Each axis can be configured to display bands with different colors for predefined value ranges. They can be used to outline a specific
				range of values.
			

# plot-bands
				Configuring Plot Bands
			

Plot bands can be added to both category and value-type axes.To add plot bands to your chart, you should assign the axis.plotBands property an array of objects having the following
					format:
				

	
          {
            from: x //where x is a number representing a start value on the axis
            to: y //where y is number representing an end value on the axis
            color: "value" // where "value" is any valid CSS color
            opacity: z // where z is from 0 to 1. This property is optional.
          }
        



With value axes, the start-end value interval is defined by values on the axis.
				


 __html__
    


				<div id="valuePlotBandsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							legend: {
								position: 'bottom'
							},
							series: [{
								name: 'Temperature',
								data: [20, 25, 32],
								axis: 'temperature',
								color: '#1E98E4'
							}, {
								name: 'Humidity',
								data: [45, 50, 80],
								axis: 'humidity',
								color: '#f99'
							}
							],
							categoryAxis: {
								categories: ['Aug', 'Sep', 'Oct'],
								axisCrossingValue: [0, 3]
							},
							valueAxis: [{
									title: {
										text: 'Temperature, Celsius'
									},
									name: 'temperature',
									plotBands: [{
										from: 30,
										to: 40,
										color: 'rgba(41,156,20, 0.8)',
	                                    opacity: 0.6
									}]
								}, {
									title: {
										text: 'Relative Humidity'
									},
									name:'humidity'
							}],
								width: 600,
								height: 350
						}">
				</div>

![chart-axis-values-plot-bands](../Media/Controls\Chart\chart-axis-values-plot-bands.png)

In category axes, the start-end value interval is represented by category indexes (zero-based). For example:


 __html__
    


				<div id="categoryPlotBandsChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							legend: {
								position: 'bottom'
							},
							series: [{
								name: 'Temperature',
								data: [20, 25, 32],
								axis: 'temperature',
								color: '#1E98E4'
							}, {
								name: 'Humidity',
								data: [45, 50, 80],
								axis: 'humidity',
								color: '#f99'
							}
							],
							categoryAxis: {
								categories: ['Aug', 'Sep', 'Oct'],
								axisCrossingValue: [0, 3],
								plotBands: [{
									from: 1,
									to: 1,
									color: 'rgba(41,156,20, 0.8)',
	                                opacity: 0.6
								}]
	
							},
							valueAxis: [{
									title: {
										text: 'Temperature, Celsius'
									},
									name: 'temperature'
								}, {
									title: {
										text: 'Relative Humidity'
									},
									name:'humidity'
							}],
								width: 600,
								height: 350
						}">
				</div>

![chart-axis-categories-plot-bands](../Media/Controls\Chart\chart-axis-categories-plot-bands.png)

# Related Topics
