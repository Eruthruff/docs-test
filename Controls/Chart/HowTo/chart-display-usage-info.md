---
title: Display Usage Info Using Radial Series
meta_title: Display Usage Info Using Radial Series
meta_description: description.
slug: 
tags:display,usage,info,using,radial,series
publish:True
---


The Telerik RadChart for Windows 8 HTML contains Pie and Donut series, both convenient mechanisms for displaying comparative values to the user.
				The main difference between the two is that Donut charts represent data as segments on a wheel (with a “donut hole” in the center) where Pie charts represent data as
				pieces of a pie.
			

This help article shows how to use these series types to display a comparison between the usage of browsers by users who visited a popular site by October 2012.

# 

* 

Add a Telerik.UI.RadChart control to your page.  For more information on this, refer to the
							[Getting Started Page](0d50f4b2-6f80-4fb7-ad09-00bd6b28b1da).
						

* 

For the series object, set the values, labels, and type:

* 

The series data is an array of JSON objects with "Name”, and "Value" fields (required) and an optional "explode" property which pulls the
									sector out of the Pie chart.
								

* 

Labels – JSON object defining visibility and providing a format string for the numeric value, so a percentage sign is shown at the end.

* 

Type - pie or donut.

For further customization options of the series, check out the [Pie Series](922320e0-7122-431a-a29d-a5b3a61af847),
					[Donut Series](04e80fa7-a792-422c-aa2d-e84d24ff5a10) and
					[Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4) articles.
				

Our chart declaration now looks like this:


 __html__
    


				<div id="pie" data-win-control="Telerik.UI.RadChart" data-win-options="{
				dataSource: {
					data: [
						{name: 'Internet Explorer', value: 23.18, explode: true},
						{name: 'Firefox', value: 26.17},
						{name: 'Chrome', value: 37.20},
						{name: 'Safari' , value: 6.79},
						{name: 'Opera', value: 3.72},
						{name: 'Others', value: 2.94}
					]
				},
				series: [{
					type: 'pie',
					field: 'value',
					categoryField: 'name',
					labels: {
						visible: true,
						format: '{0} %'
					}
				}],
				width: 600
				}">
				</div>



And the result is shown below:![Usage info sample](../Media/Controls\Chart\chart-usage-info.png)

# Related Topics
