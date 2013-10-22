---
title: Change the Series Type Dynamically
meta_title: Change the Series Type Dynamically
meta_description: description.
slug: 
tags:change,the,series,type,dynamically
publish:True
---


In some scenarios you might want to allow the user to choose between different representations of your data, by letting them pick the chart series type. Here
				you will find an explanation on what should be done to change the type of series used in the control dynamically.
			

# Changing the Chart Series Type Dynamically

Since the chart series are represented by different classes, you need to replace the current series with a new instance of the chosen type of series and then
					refresh the chart. You can see a code sample along with comments below.
				

The code below includes radio buttons for switching the series type between column and bar and a simple chart declaration:


 __html__
    


				<div id="radioButtonGroup">
					<input type="radio" name="chartType" value="bar" id="bar" /><label for="bar">Bar</label>
					<input type="radio" name="chartType" value="column" id="column" checked="checked" /><label for="column">Column</label>
				</div>
				<div id="chart1" data-win-control="Telerik.UI.RadChart" data-win-options="{
							dataSource: {
								data: [
									{value: 10},
									{value: 20},
									{value: 30},
									{value: 40},
									{value: 50}
								]},
							series: [
								{
									field: 'value'
								}]
						}">
				</div>



Following is the JavaScript logic to handle the radio button click. When a click occurs, this code will:

* 

Access the chart control.

* 

Clear the series collection.

* 

Add a new series, corresponding to the currently selected radio button.


 __js__
    


					var radioButtonGroup = document.getElementById("radioButtonGroup");
					var inputs = radioButtonGroup.getElementsByTagName("input");
					var radioButtons = Array.prototype.slice.call(inputs);
					//attach the click event on each of the radio buttons
					radioButtons.forEach(function (item) {
						item.addEventListener("click", function () {
							var chart = document.getElementById("chart1").winControl;
							//clear the chart series
							chart.series = [];
							var newSeries;
							//based on the selected button, instantiate new series
							switch (this.value) {
								case "bar":
									newSeries = new Telerik.UI.Chart.BarSeries();
									break;
								case "column":
									newSeries = new Telerik.UI.Chart.ColumnSeries();
									break;
								default: newSeries = null;
							}
							if (newSeries) {
								//assign a field to the series and add them to the chart
								newSeries.field = "value";
								chart.series.push(newSeries);
								chart.refresh();
							}
						});
					});



Running the code will allow the user to switch between the following a Bar series and Column series:![Change series dynamically](../Media/Controls\Chart\chart-change-series_1.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/ChangingSeriesTypeDynamically*.
        

# Related Topics
