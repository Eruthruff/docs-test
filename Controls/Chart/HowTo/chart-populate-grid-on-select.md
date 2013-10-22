---
title: Populate a Grid on Series Click
meta_title: Populate a Grid on Series Click
meta_description: description.
slug: 
tags:populate,a,grid,on,series,click
publish:True
---


Charts are sometimes used to visualize aggregated data values. When you need to provide more details about each data item from the aggregation, 
        a good way to present it, is using a tabular data structure. Using __RadChart's__ and __RadGrid's__ features you can easily
        achieve such result. The following article will introduce a simple scenario where a chart displays count of olympic medals per athlete and on click
        of a series data point (column) a grid displays information regarding all medals the athlete has won.
      

# 

The data used in the following basic example is represented by two *json* objects in the following formats:
        

	
          { "athleteId": "551", "athleteName": "Nikolay Andrianov", "medalsCount": 16 }
        



	
          { "athleteId": "551", "athleteName":"Nikolay Andrianov", "year":"1972", "sport":"Gymnastics Floor Exercises", "medal":"gold" }
        



The first one is for the chart control and has exactly one entry for each athlete, containing his total medals count. The second one is for the grid control 
          and can have multiple entries for the same athlete, because some athletes have more than one olympic medal in their career.
        

The next steps depict the process of creating a column chart, which upon click of a column displays a __RadGrid__ with additional information 
          about the selected category. 
        


 __html__
    


	
				<div id="chart"></div>
	            <div id="gridcontainer">
	                <h2 id="gridtitle"></h2>
	                <div id="grid"></div>
	            </div>
	



* 

*Define a __RadGrid__.* Because the given data is a list with 
              the results of all the athletes, you can initialize the control with the __autoBind__ property set to 
              *false*. Thereby, you avoid the initial visualization of the possibly large amount of data. 
              You can also hide the grid with CSS styles and show it in the __onseriesclick__ event handler.
            


 __js__
    


				    grid = new Telerik.UI.RadGrid(document.getElementById('grid'), {
				        dataSource: {
				            transport: {
				                read: {
				                    url: "/js/athletesResults.json",
				                    dataType: "json"
				                }
				            }
				        },
				        columns: [
	                        { field: 'sport', width: 500 },
	                        { field: 'year' },
	                        { field: 'medal' }
				        ],
	                    autoBind: false
				    });



* 

*Define a __RadChart__ with the medals count set as the series' field and the athlete name set as the category axis' field*. 
              In order to trigger the grid filtering, you need to attach a handler to the __onseriesclick__ event.
            


 __js__
    


				    chart = new Telerik.UI.RadChart(document.getElementById('chart'), {
				        dataSource: {
				            transport: {
				                read: {
				                    url: "/js/athletesMedals.json",
				                    dataType: "json"
				                }
				            }
				        },
				        height: 400,
				        series: [
	                        {
	                            type: 'column',
	                            name: 'Medals Count',
	                            field: 'medalsCount',
	                            colorField: 'color'
	                        }
				        ],
				        categoryAxis: {
				            field: 'athleteName',
				            labels: {
				                rotation: 45,
				                margin: {
				                    left: 25
				                }
				            }
				        },
	                    transitions: false,
				        onseriesclick: ChartSeriesClickHandler
				    });



Here is what should be done in the handler:
            

* 

Get the athlete name and the count of his medals through the event's __dataItem__ argument.

* 

Change the selected item's color and return the normal color to the previous selected item. This is done by adding a new property to the JavaScript 
                  objects, named "color", and setting it's value to the desired color. This property is used by the __RadChart's__ series, where 
                  the __colorField__ option was previously set to *color* to match the newly added property.
                

* 

Assign the modified data to __RadChart's dataSource__ and refresh the __RadChart__ to display 
                  the selected column with the new color. Note that in order to skip the redrawing of the chart's columns, the __transitions__ property 
                  of the __RadChart__ has to be set to *false*.
                

* 

Create a __filter__ for the data source. It is an array of filter commands as objects. Each filter command has three properties - 
                  __field__, __operator__ and __value__. In the current scenario the grid needs to be filtered 
                  by the athlete name, where the name should equal the chart event's __category__ argument.
                

* 

Assign the created filter to the __RadGrid's dataSource.filter__ property.
                

* 

Because the __RadGrid__ was initialized with the __autoBind__ property set to *false*, 
                  you need to manually bind the __RadGrid's dataSource__. This can be achieved through calling the __read()__ method 
                  of the __dataSource__. Note that you do not need to explicitly call __RadGrid's refresh()__ method to update the grid. 
                  The reason for this is the __RadGrid__ refreshes itself automatically when its __dataSource__ is rebound.
                


 __js__
    


		function ChartSeriesClickHandler(e) {
		    var item = e.dataItem;
		    var chartDS = chart.dataSource.data;
	
		    // setting the red color of the selected item and removing the red color from the previous selected item
		    for (var i = 0; i < chartDS.length; i++) {
		        if (chartDS[i].athleteId == item.athleteId) {
		            chartDS[i].color = "red";
		        } else if (chartDS[i].color != "#1e98e4") {
		            chartDS[i].color = "#1e98e4";
		        }
		    }
	
		    chart.dataSource.data = chartDS;
		    chart.refresh();
	
		    // modifying the h2 title element's innerText
		    gridTitle.innerText = item.athleteName + " - " + item.medalsCount + " medals";
	
		    // setting up the filter for the RadGrid
		    var filter = [];
		    filter.push({ field: "athleteName", operator: "eq", value: item.athleteName });
		    grid.dataSource.filter = filter;
	
		    grid.dataSource.read();
		    gridContainer.style.visibility = "visible";
		}



Now, if you click on a data point (column) in the __RadChart__ (e.g. Alexey Petrov), the __RadGrid__ below will be populated 
           and displayed. The result looks like this:
        ![chart-populate-grid](../Media/Controls\Chart\chart-populate-grid.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/PopulateGridOnBarSelect*.
        

# Related Topics

 * [Column Series]({{slug:column-series}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Category Axis]({{slug:category-axis}})

 * [Events]({{slug:events}})

 * [Using DataSource with UI Controls]({{slug:using-datasource-with-ui-controls}})

 * [Filtering]({{slug:filtering}})

 * [Binding RadGrid to Remote Data]({{slug:binding-radgrid-to-remote-data}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})
