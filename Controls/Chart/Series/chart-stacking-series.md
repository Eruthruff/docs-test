---
title: Stacking Series
meta_title: Stacking Series
meta_description: description.
slug: 
tags:stacking,series
publish:True
---


RadChart for Windows 8 HTML implements stacking of its *area*, *bar*,
				*column* and *line* series. This allows you to place multiple series in one chart, separating
				them vertically,  for better visualization. Stacking is controlled by the __stack__ property which, based on the series type, can
				accept Boolean and/or string values. If you read on, you will get acquainted with the specifics of stacking series in RadChart.
			

# Section1Description of Stacking Series

Stacking puts the first declared series as normal - starting from point 0 on the value axis and then starts drawing each subsequent series of the same type on 
					top of the previously drawn ones. The start value of the latter series is the end value of the former ones. At the end, the value reached by the last
					drawn column, line, etc., is the total sum of all series stacked one over another.
				


 __html__
    


				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [
								{
									data: [1, 16, 28],
								},
								{
									data: [6, 12, 35]
								}
							],
							seriesDefaults: {
								stack: true
							},
							width: 500
						}">
				</div>

![Stacking series](../Media/Controls\Chart\chart-stacking-series.png)

# Stacking Bar and Column Series

You can assign either a Boolean value or a non-empty string to the __stack__ property of Bar and Column series. Assigning 
					*true* means that series will be stacked each over the other. It is enough to set __stack = true__ for the 
					first declared series of a given type, all series of this type will be stacked. Another option to achieve the same result is to set 
					__stack=true__ in the __seriesDefault__ property, which applies its settings to all series.
				


 __html__
    


				<div id="chart2" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [
								{
									data: [1, 16, 28],
									type: 'bar',
									stack: true
								},
								{
									data: [6, 12, 35],
									type: 'bar'
								}
							],
							width: 500
						}">
				</div>

![Stacking bar series](../Media/Controls\Chart\chart-stacking-bar-series.png)

If you want to group stacked series, give the __stack__ property of each series a string value – it should be the same for the series that 
					you want to group together. If you leave a series without the __stack__ property set or with a group name that is unique to this series only, 
					it will not be stacked.
				


 __html__
    


				<div id="chart3" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [
								{
									data: [1, 16, 28],
									stack: 'stack1'
								},
								{
									data: [6, 12, 35],
									stack: 'stack2'
								},
								{
									data: [3, 12, 38],
									stack: 'stack1'
								},
								{
									data: [14, 12, 22],
									stack: 'stack2'
								}
							],
							width: 500
						}">
				</div>

![Grouping stacked series](../Media/Controls\Chart\chart-grouping-stacked-series.png)

# Stacking Area and Line Series

The __stack__ property of Area and Line series accepts only Boolean values, due to the nature of the series itself (you cannot have groups 
					of stacked Line series). Setting it to true for the first declared series, or through the __seriesDefaults__ property, will 
					cause all series of the same type to get stacked.
				


 __html__
    


				<div id="chart4" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [
								{
									data: [1, 16, 28],
									type: 'area',
									stack: true
								},
								{
									data: [6, 12, 35],
									type: 'area'
								}
							],
							width: 500
						}">
				</div>

![Stacking area series](../Media/Controls\Chart\chart-stacking-area-series.png)

# Related Topics
