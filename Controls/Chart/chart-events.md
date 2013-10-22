---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events fired by RadChart, their usage and most notable event arguments.

# 

Event Name

Description

Arguments

__axislabelclick__

Fires when an axis label is clicked.
							

__e.axis__: The axis that the label belongs to.
							

__e.dataItem__: Tthe original data item used to generate the label. Applicable only for data bound
								category axis.
							

__e.index__: The label sequential index or category index.
							

__e.text__: The label text.
							

__e.target__: The RadChart instance.
							

__e.value__: The label value or category name.
							

__databound__

Fires immediately after the control is databound.
							

__e.target__: The RadChart instance.
							

__drag__

Fired as long as the user is dragging the chart using the mouse or swipe gestures.
							

__e.axisRanges__: A hastable containing the initial range
								(min and max values) of named axes. The axis name is used as a key.
							

__e.originalEvent__: The original user event that triggered the drag action.
							

__e.target__: The RadChart instance.
							

__dragend__

Fires when the user stops dragging the chart.
							

__e.axisRanges__: A hastable containing the initial range
								(min and max values) of named axes. The axis name is used as a key.
							

__e.originalEvent__: The original user event that triggered the drag end action.
							

__e.target__: The RadChart instance.
							

__dragstart__

Fires when the user starts dragging the chart.
							

__e.axisRanges__: A hastable containing the initial range
								(min and max values) of named axes. The axis name is used as a key.
							

__e.originalEvent__: The original user event that triggered the drag action.
							

__e.preventDefault__: If invoked the drag operation will be aborted.
							

__e.target__: The RadChart instance.
							

__legenditemclick__

Fires when an item in the chart legend is clicked or tapped.
							

__e.series__: The chart series object represented by the legend item.
							

__e.seriesIndex__: The index of the chart series.
							

__e.target__: The RadChart instance.
							

__e.text__: The legend item text.
							

__legenditemhover__

Fires when an item in the chart legend is hovered.
							

__e.series__: The chart series object represented by the legend item.
							

__e.seriesIndex__: The index of the chart series.
							

__e.target__: The RadChart instance.
							

__e.text__: The legend item text.
							

__plotareaclick__

Fires when the plot area is clicked.
							

__e.category__: the data point category. Available only for categorical charts (bar, line, area and
								similar).
							

__e.target__: The RadChart instance.
							

__e.value__: the data point value. Available only for categorical charts (bar, line, area and similar).
							

__select__

Fires when the user modifies the visible selection of RadChart.
							

The range units are: *Generic axis* - Category index (0-based);
								*Date axis* - Date instance.
							

__e.from __: The lower boundary of the selected range.
							

__e.target__: the RadChart instance.
							

__e.to__: The upper boundary of the selected range.
								*The last selected category is at index [to - 1] unless the axis is justified. In this case it is at index [to].*

__selectend__

Fires when the user completes modifying the selection.
							

The range units are: *Generic axis* - Category index (0-based);
								*Date axis* - Date instance.
							

__e.from __: The lower boundary of the selected range.
							

__e.target__: the RadChart instance.
							

__e.to__: The upper boundary of the selected range.
								*The last selected category is at index [to - 1] unless the axis is justified. In this case it is at index [to].*

__selectstart__

Fires when the user starts modifying the axis selection.
							

The range units are: *Generic axis* - Category index (0-based);
								*Date axis* - Date instance.
							

__e.from __: The lower boundary of the selected range.
							

__e.target__: the RadChart instance.
							

__e.to__: The upper boundary of the selected range.
								*The last selected category is at index [to - 1] unless the axis is justified. In this case it is at index [to].*

__seriesclick__

Fires when any of the chart series is clicked.
							

__e.category__: The data point category.
							

__e.dataItem__: The original data item (when binding to dataSource).
							

__e.series__: The clicked series. You can get the name and type of the series through the respective
								properties (e.series.name, e.series.type).
							

__e.target__: The RadChart instance.
							

__e.value__: The data point value.
							

__serieshover__

Fires when any of the chart series is hovered.

							

__e.category__: The data point category.
							

__e.dataItem__: The original data item (when binding to dataSource).
							

__e.series__: The clicked series. You can get the name and type of the series through the respective
								properties (e.series.name, e.series.type).
							

__e.target__: The RadChart instance.
							

__e.value__: The data point value.
							

__zoom__

Fired as long as the user is zooming the chart using the mousewheel.
							

__e.axisRanges__: A hastable containing the initial range (min and max values) of named axes. The axis name is used as a key.
							

__e.delta__: A number that indicates the zoom amount and direction. A negative value indicates "zoom in", while a positive "zoom out".
							

__e.originalEvent__: The original user event that triggered the zoom action.
							

__e.target__: the RadChart instance.
							

__zoomend__

Fires when the user stops zooming the chart.
							

__e.axisRanges__: A hastable containing the initial range (min and max values) of named axes. The axis name is used as a key.
							

__e.originalEvent__: The original user event that triggered the zoom end action.
							

__e.target__: The RadChart instance.
							

__zoomstart__

Fires when the user uses the mouse wheel to zoom the chart.
							

__e.axisRanges__: A hastable containing the initial range (min and max values) of named axes. The axis name is used as a 
								key.
							

__e.originalEvent__: If invoked the zoom operation will be aborted.
							

__e.preventDefault__: The original user event that triggered the zoom action.
							

__e.target__: The RadChart instance.
							

The following example shows how to use the __seriesclick__ event to display information about the clicked series.
				


 __html__
    


				<div id="myChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
								data: [
								{ year: '2000', sales: 200, profit: 100 },
								{ year: '2001', sales: 450, profit: 370 },
								{ year: '2003', sales: 125, profit: 87 }]
							},
							series: [
								{ type: 'line', field: 'sales', name: 'Sales' },
								{ type: 'line', field: 'profit', name: 'Profit' }
							],
							categoryAxis: {
								field: 'year'
							},
							onseriesclick: Sample.Helpers.seriesClick
						}">
				</div>
				<p id="seriesInfo" style="color: #336699"></p>
				<p id="selection" style="color: #33ccff"></p>




 __js__
    


	    WinJS.Namespace.define("Sample.Helpers", {
	    	seriesClick: WinJS.Utilities.markSupportedForProcessing(function (e) {
	    		var dataItem = e.dataItem;
	    		document.getElementById("seriesInfo").innerHTML = "On <span style='color: white'>" + e.series.name
				+ "</span> series, clicked a data point with value of <span style='color: white'>" + e.value + "</span>.";
	    	})
	    });



# Related Topics
