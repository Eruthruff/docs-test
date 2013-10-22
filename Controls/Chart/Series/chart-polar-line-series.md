---
title: Polar Line
meta_title: Polar Line
meta_description: description.
slug: 
tags:polar,line
publish:True
---


Polar Line series visualize data as a line by connecting data points in a polar coordinate system. Each data point is defined by an angle and a
        distance from the center point. The vertex of the angle is the chart's center point and by default the starting ray is the horizontal line
        starting from the vertex going right. The data point will be visualized on the second (resulting) ray of the angle at a distance from the
        center point equal to the second polar coordinate. On the image below you can see the polar coordinate system coordinates and how they are used.
      ![chart-polar-line-series](../Media/Controls\Chart\chart-polar-line-series.png)

# declarative-definitionDefining a Polar Line Series Declaratively

Polar Line series can be defined in the mark-up or in __RadChart__'s constructor declaratively by adding an
          object with a __type__ property set to *'polarLine'* to the
          __Telerik.UI.RadChart.series__ array.
        

The simplest way to add data to a Polar Line series, is to assign the __data__ property an array with the data.
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



# programmatic-definitionDefining a Polar Line Series Programmatically

To create and add a Polar Line series programmatically, you need to create a new __Telerik.UI.Chart.PolarLineSeries__
          object and add it to the __Telerik.UI.RadChart.series__ array. Call the __refresh()__
          method for the changes to take effect.
        


 __js__
    


				    var polarLineSeriesChart = document.getElementById("polarLineSeriesChart").winControl;
				    var polarLineSeries = new Telerik.UI.Chart.PolarLineSeries();
				    polarLineSeries.data = [
						[105, 43.7],
						[163, 36.5],
						[231, 48.1],
	                    [296, 22]
				    ];
				    polarLineSeriesChart.series.push(polarLineSeries);
				    polarLineSeriesChart.refresh();



# configurationConfiguring Polar Line Series

Apart from the common configuration settings listed in this article:
          [RadChart Series Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4),
          there a few more specific configuration settings that you can use to customize the look and behavior of the Polar Line series.
        

# fieldsSetting the Polar Line Series Fields

You can also use an array of JavaScript objects as data for the Polar Line series. You need to specify data 
              fields that the series will use to get values. There are two available field settings for the Polar Line series representing 
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



# lineLine Settings

There are three specific properties that allow the customization of the line. These are __dashType__ 
              (*'dash'*, *'dashDot'*, *'dot'*, 
              *'longDash'*, *'longDashDot'*, *'longDashDotDot'*, 
              and *'solid'*), __width__, and __opacity__. You can also 
              use the __color__ property to change the color of the line. Below is an example of configuring the line 
              settings for the Polar Line series.
            


 __html__
    


				<div id="polarLineLineSettings" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarLine',
	                    data: [
							[ 0, 36.2],
	                        [ 60, 18.4],
							[ 120, 33.1],
							[ 180, 37.7],
							[ 240, 31.5],
							[ 240, 0],
	                        [ 300, 0],
	                        [ 360, 36.2]
						],
	                    dashType: 'dash',
	                    opacity: 0.5,
	                    width: 3,
	                    color: '#FF361C'
					}],
	                theme: 'light'       
				}">
				</div>



Here is an image of the chart produced by the above code snippet.
            ![chart-polar-line-line-settings](../Media/Controls\Chart\chart-polar-line-line-settings.png)

# markersCustomizing Markers

By default the data point markers are not displayed. To visualize them, set the __visible__ option 
              value of the __markers__ property to *true*. This will display the data 
              point markers with their default settings. The __markers__ property exposes the following options 
              to customize the appearance of the markers: __background__, __border__ settings, 
              __size__, __type__ (*'circle'*, 
              *'square'*, and *'triangle'*), and __visible__. 
              Here is an example of how to display and customize the data points markers.
            


 __html__
    


				<div id="polarLineMarkers" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarLine',
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
	                            color: '#564110'
	                        },
	                        size: 15,
	                        type: 'triangle',
	                        visible: true
	                    }
					}],
	                theme: 'light'       
				}">
				</div>



Below is an image of the resulting chart with the customized data point markers.
            ![chart-polar-line-markers](../Media/Controls\Chart\chart-polar-line-markers.png)

# missing-valuesHandling Missing Values

Use the __missingValues__ property to specify how a missing value at some angle in the data will be handled. 
              Below is a brief description of the possible property values.
            

* 

*'interpolate'*: This is the default property value. When this property value is set, the 
                  missing points will be interpolated from neighboring data points.
                

* 

*'gap'*: When this property value is set, the line will break between the missing value's 
                  neighboring data points and will continue afterwards.
                

* 

*'zero'*: This property value specifies that the missing values should be assigned a value 
                  of zero.
                

In the code snippet below there is a value in the data that is *null* and the __missingValues__ 
              property value is set to *'gap'*.
            


 __html__
    


				<div id="polarLineMissingValues" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarLine',
	                    data: [
							[ 0, 21.2],
							[ 78, 34.5],
							[ 96, 32.7],
							[ 168, 41.1],
							[ 221, null],
	                        [ 254, 52.8],
	                        [ 360, 21.2]
						],
	                    missingValues: 'gap'
					}],
	                theme: 'light'       
				}">
				</div>



Here is an image of the resulting Polar Line chart.
            ![chart-polar-line-missing-values](../Media/Controls\Chart\chart-polar-line-missing-values.png)

# Related Topics
