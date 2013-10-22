---
title: Display Rental Info Using Scatter Series
meta_title: Display Rental Info Using Scatter Series
meta_description: description.
slug: 
tags:display,rental,info,using,scatter,series
publish:True
---


The Telerik RadChart for Windows 8 HTML contains Scatter and ScatterLine series, both convenient mechanisms for displaying two variables for a set of data. This
				help article demonstrates how to use these series to display a combination of rental information data - the number of properties for rent along with how long, on average,
				they stay on market (in days).
			

# 

* 

Add a Telerik.UI.RadChart control to your page.  For more information, refer to the
							[Getting Started Page](0d50f4b2-6f80-4fb7-ad09-00bd6b28b1da).
						

* 

For the series object, set the value fields, type and markers (optional):

* 

The series data is an array of JSON objects with "Count”, and "DaysOnMarket" fields. These fields should be assigned to the xField and yField
									properties.
								

* 

Type - scatter or scatterLine.

* 

Markers – to customize the markers, set their border, size, and type options. You can find out more markers here:
									[Scatter Series](8b72db8e-3e99-48ac-ac47-49433e5e3fc2).
								

For further customization options of the series, check out the [Scatter Series](8b72db8e-3e99-48ac-ac47-49433e5e3fc2),
					[Scatter Line Series](a67f8b22-95e8-4e9d-ae3d-c104c43655a2) and
					[Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4) articles.
				

Our chart declaration now looks like this:


 __html__
    


				<div data-win-control="Telerik.UI.RadChart" data-win-options="{
					series:[
					{	
						name: 'Days on Market / Count',
						markers:{
							border:{
								color:'green', 
								width: 2
							}, 
							size: 7, 
							type:'circle'
						}, 
						type:'scatterLine', 
						xField:'DaysOnMarket', 
						yField:'Count',
					}],
					dataSource: {
						data:[
							{Count: 10, DaysOnMarket: 10}, 
							{Count: 20, DaysOnMarket: 15}, 
							{Count: 30, DaysOnMarket: 20}, 
							{Count: 40, DaysOnMarket: 32}, 
							{Count: 50, DaysOnMarket: 43}, 
							{Count: 60, DaysOnMarket: 55}, 
							{Count: 70, DaysOnMarket: 60}, 
							{Count: 80, DaysOnMarket: 70}
						]			
					}
				}">
				</div>
	



The result is shown below:![Rental info sample](../Media/Controls\Chart\chart-rental-info.png)

# Related Topics

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})
