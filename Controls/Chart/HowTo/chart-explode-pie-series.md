---
title: Explode a Pie Chart on Series Click
meta_title: Explode a Pie Chart on Series Click
meta_description: description.
slug: 
tags:explode,a,pie,chart,on,series,click
publish:True
---


The explode state of the sectors in Pie and Donut series is controlled by the explode field that they are bound to. By default, the explode field is not connected to
				user interaction with the chart. One way to implement behavior that explodes the clicked sector, is to modify the respective values in the chart data
				source in the __seriesclick__ event.
			>
					Note that this approach is mostly valid for a chart bound to local data or a static object populated (once or at a certain
					time interval) from remote data. This is due to the need to modify one of the fields values on the fly to provide the desired result.
				>
					You can use the exact same approach, shown below, with Donut series.
				

# Implementation

* 

The code snippet below declares a simple pie chart, bound to a static data source, which defines sectors to explode, based on the value of the
							*Highlight* field.
						


 __html__
    


						<div id="pieChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
							series: [{
							type: 'pie',
	
							field: 'Value',
							explodeField: 'Highlighted',
							labels: {
							  visible: true,
							  template: '#=dataItem.Employee # (#=dataItem.Value# %)'
							}
						}],
						dataSource: {
								data: [
								{ Value: 26.6, Employee: 'Maria Anders', Change: 2, Highlighted: false },
								{ Value: 23, Employee: 'Ana Trujillo', Change: -3, Highlighted: false },
								{ Value: 16.7, Employee: 'Antonio Moreno', Change: -4, Highlighted: false },
								{ Value: 20, Employee: 'Thomas Hardy', Change: 3, Highlighted: false },
								{ Value: 15.7, Employee: 'Christina Berglund', Change: 2, Highlighted: false}
							]
						},
						onseriesclick: eventHandlers.seriesClick,
						transitions: false,
						title: {
							text: 'Sales per employee',
							font: '18pt times'
						},
						width: 700
						}">
						</div>
						<div id="info" style="display: none; margin: 50px;">
							Sales for 2011 by 
							<span id="employee" style="color: #2755c2"></span>: 
							<span id="value" style="color: #3a7113"></span>
							(<span id="change"></span>)
						</div>



* 

In JavaScript, handle the __onseriesclick__ event to access the dataItem of the current sector, as well as the data source of the whole
							chart. First, set all explode values to *false* and then switch only the one for the current sector to
							*true*.
						

* 

Finally, you can access additional data from the current data item and display it through formatted text to the user.


 __js__
    


	WinJS.Namespace.define("eventHandlers", {
		seriesClick: WinJS.Utilities.markSupportedForProcessing(function (e) {
			var dataItem = e.dataItem;
			var dataItems = e.target.dataSource.data;
			//setting the explode value of all sectors to false
			for (var i = 0; i < dataItems.length; i++) {
				dataItems[i].Highlighted = false;
			}
			//exploding the currently selected sector
			dataItem.Highlighted = true;
			e.target.refresh();
			//populating the information area below the chart
			document.getElementById("info").style.display = "";
			document.getElementById("employee").innerText = dataItem.Employee;
			document.getElementById("value").innerText = dataItem.Value + "%";
			var changeSpan = document.getElementById("change");
			if (dataItem.Change > 0) {
				changeSpan.style.color = "green";
				changeSpan.innerText = "+" + dataItem.Change + "%";
			}
			else {
				changeSpan.style.color = "red";
				changeSpan.innerText = dataItem.Change + "%";
			}
	
		})
	});



The result is shown in the image below:![Explode pie series on click](../Media/Controls\Chart\chart-explode-pie-on-click.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/ExplodingPieChartOnSeriesClick*.
        

# Related Topics

 * [Events]({{slug:events}})
