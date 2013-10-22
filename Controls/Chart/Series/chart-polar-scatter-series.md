---
title: Polar Scatter
meta_title: Polar Scatter
meta_description: description.
slug: 
tags:polar,scatter
publish:True
---


Polar Scatter series visualize data points in a polar coordinate system. Each data point is defined by an angle (direction) and a
        distance from the center point. The vertex of the angle is the chart's center point and by default the starting ray is the horizontal line
        starting from the vertex going right. The data point will be visualized on the second (resulting) ray of the angle at a distance from the 
        center point equal to the second polar coordinate. On the image below you can see the polar coordinate system coordinates and how they are used.
      ![chart-polar-scatter-series](../Media/Controls\Chart\chart-polar-scatter-series.png)

# declarative-definitionDefining a Polar Scatter Series Declaratively

To define a Polar Scatter series declaratively in the mark-up or in __RadChart__'s constructor, add an
          object with a __type__ property set to *'polarScatter'* to the
          __Telerik.UI.RadChart.series__ array.
        

The simplest way to add data to a Polar Scatter series, is to assign the __data__ property an array with the data.
          Each data point is also represented by an array with two members. The first member is the angle in degrees (0 to 360). The second member
          is the distance from the chart's center point.
        


 __html__
    


				<div id="polarLineSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarLine',
	                    data: [
							[ 45, 36.2],
							[ 86, 33.1],
							[ 145, 17.7],
							[ 236, 21.5],
							[ 273, 42.1],
	                        [ 303, 36]
						]
					}],
	                theme: 'light'       
				}">
				</div>



# programmatic-definitionDefining a Polar Scatter Series Programmatically

To create and add a Polar Scatter series programmatically, you need to create a new __Telerik.UI.Chart.PolarScatterSeries__
          object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call the __refresh()__
          method for the changes to take effect.
        


 __js__
    


	                var polarScatterSeriesChart = document.getElementById("polarScatterSeriesChart").winControl;
				    var polarScatterSeries = new Telerik.UI.Chart.PolarScatterSeries();
				    polarScatterSeries.data = [
						[105, 43.7],
						[163, 36.5],
						[231, 48.1],
	                    [296, 22]
				    ];
				    polarScatterSeriesChart.series.push(polarScatterSeries);
				    polarScatterSeriesChart.refresh();



# configurationConfiguring Polar Scatter Series

Apart from the common configuration settings listed in this article:
          [RadChart Series Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4),
          there a few more specific configuration settings that you can use to customize the look and behavior of the Polar Scatter series.
        

# fieldsSetting the Polar Scatter Series Fields

You can also use an array of JavaScript objects as data for the Polar Scatter series. You need to specify data
              fields that the series will use to get values. There are two available field settings for the Polar Scatter series representing
              the two polar coordinates. Here is a description of their usage:
            

* 

__xField__: The data field that holds the data points' angle coordinate.
                

* 

__yField__: The data field that holds the data points' distance coordinate.
                

Here is an example of how to use the above properties with a __dataSource__, but their use is identical if
              you assign an array of JavaScript objects to the series __data__ property.
            


 __html__
    


				<div id="polarLineFields" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarLine',
	                    xField: 'angle',
	                    yField: 'value'
					}],
	                dataSource: {
	                    data: [
	                        { angle: 0, value: 15.3},
						    { angle: 60, value: 25.1},
						    { angle: 120, value: 16.7},
						    { angle: 180, value: 13.1},
						    { angle: 240, value: 31.1},
	                        { angle: 300, value: 19.2},
	                        { angle: 360, value: 15.3}
	                    ]
	                },
	                theme: 'light'       
				}">
				</div>



# markersCustomizing Markers

To modify the appearance of the data point makers, use the __markers__ property. It exposes the following settings: 
              __background__, __border__ settings, __size__, __type__ 
              (*'circle'*, *'square'*, and *'triangle'*), and __visible__. 
              Here is an example of a Polar Scatter series with customized data point markers and below is an image of the resulting chart.
            


 __html__
    


				<div id="polarScatterMarkers" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarScatter',
	                    data: [
							[ 0, 16.2],
							[ 60, 23.1],
							[ 120, 27.7],
							[ 180, 21.5],
							[ 240, 12.1],
	                        [ 300, 24.8],
	                        [ 360, 16.2],
						],
	                    markers: {
	                        background: '#FFF',
	                        border: {
	                            width: 3,
	                            color: '#CE0613'
	                        },
	                        size: 25,
	                        type: 'triangle'
	                    }
					}],
	                theme: 'light'       
				}">
				</div>

![chart-polar-scatter-markers](../Media/Controls\Chart\chart-polar-scatter-markers.png)

# Related Topics
