---
title: Display the Total Sum of Series in a Stack
meta_title: Display the Total Sum of Series in a Stack
meta_description: description.
slug: 
tags:display,the,total,sum,of,series,in,a,stack
publish:True
---


You can easily display the value of each series using its label property. However, when stacking series, in order to be able to display a total of all
				stacked values, you would need to manually sum the values of the stacked series. Below you can see a sample of how this can be achieved in a couple of steps.
			

# 

* 

The __dataSource__ property of RadChart is of type __Telerik.Data.DataSource__ and it allows you
							to process data once it is fetched, using the __parse__ event of the __schema__ child object.
							So, the first step is to define your implementation of the parse function to sum the values from the passed datasource and assign the result to
							a new property of the data item.
						


 __js__
    


	WinJS.Namespace.define("StackingSeries.Functions", {
		processData: WinJS.Utilities.markSupportedForProcessing(function (dataItems) {
			var item;
			for (var i = 0; i < dataItems.length; i++) {
				item = dataItems[i];
				item.total = item.value1 + item.value2;
			}
			return dataItems;
		})
	});



* 

In the series declaration, make the labels visible and using a template, display the value of the newly added property of the
							*dataItem* object.
						


 __html__
    


				<div id="chart5" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
								data: [
									{value1: 15, value2: 17},
									{value1: 11, value2: 19},
									{value1: 32, value2: 24}
								],
								schema: {
									parse: StackingSeries.Functions.processData
								}
							},
							series: [
								{ 
									field: 'value1', 
								},
								{
									field: 'value2',
									labels: {
										visible: true,
										template: 'Total: #=dataItem.total#'
									}
								}
							],
							seriesDefaults: {
								type: 'column',
								stack: true
							}
						}">
				</div>



The resulting chart looks like this:![chart-stacking-series-totals](../Media/Controls\Chart\chart-stacking-series-totals.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/DisplayingTotalSumOfSeriesInAStack*.
        

# Related Topics

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})
