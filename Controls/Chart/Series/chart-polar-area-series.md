---
title: Polar Area
meta_title: Polar Area
meta_description: description.
slug: 
tags:polar,area
publish:True
---


Polar series visualize data in a polar coordinate system. In the Polar Area series the area enclosed by the data points is colored and represents the polar area. 
        Each data point is defined by an angle and a distance from the center point. The vertex of the angle is the chart's center
        point and by default the starting ray is the horizontal line starting from the vertex going right. The data point will be visualized on the second
        (resulting) ray of the angle at a distance from the center point equal to the second polar coordinate. On the image below you can see the polar
        coordinate system coordinates and how they are used.
      ![chart-polar-area-series](../Media/Controls\Chart\chart-polar-area-series.png)

# declarative-definitionDefining a Polar Area Series Declaratively

Polar Area series can be defined in the mark-up or in __RadChart__'s constructor declaratively by adding an 
          object with a __type__ property set to *'polarArea'* to the 
          __Telerik.UI.RadChart.series__ array.
        

The simplest way to add data to a Polar Area series, is to assign the __data__ property an array with the data.
          Each data point is also represented by an array with two members. The first member is the angle in degrees (0 to 360). The second member
          is the distance from the chart's center point.
        


 __html__
    


				<div id="declarativePolarAreaSeriesChart" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarArea', 
						data: [
							[ 47, 20.0],
							[ 125, 15.7],
							[ 178, 26.6],
							[ 231, 25.3]
						]
					}],
	                theme: 'light'       
				}">
				</div>



# programmatic-definitionDefining a Polar Area Series Programmatically

To create and add a Polar Area series programmatically, you need to create a new __Telerik.UI.Chart.PolarAreaSeries__ 
          object and add it to the __Telerik.UI.RadChart.series__ array. Finally, call the __refresh()__ 
          method for the changes to take effect.
      


 __js__
    


				    var polarAreaSeriesChart = document.getElementById("declarativePolarAreaSeriesChart").winControl;
				    var polarAreaSeries = new Telerik.UI.Chart.PolarAreaSeries();
				    polarAreaSeries.data = [
						[117, 12.7],
						[195, 24.6],
						[234, 22.3],
	                    [297, 26.9]
				    ];
				    polarAreaSeriesChart.series.push(polarAreaSeries);
				    polarAreaSeriesChart.refresh();



# configurationConfiguring Polar Area Series

Apart from the common configuration settings listed in this article: 
          [RadChart Series Common Configuration](15e0c300-a141-495d-9355-3d2d35951bd4), 
          there a few more specific configuration settings that you can use to customize the look and behavior of the Polar Area series.
        

# fieldsSetting the Polar Area Series Fields

You can also use an array of JavaScript objects as data for the Polar Area series. You need to specify data 
              fields that the series will use to get values. There are two available field settings for the Polar Area series representing 
              the two polar coordinates. Here is a description of their usage:
            

* 

__xField__: The data field that holds the data points' angle coordinate.
                

* 

__yField__: The data field that holds the data points' distance coordinate.
                

Here is an example of how to use the above properties with a __dataSource__, but their use is identical if
              you assign an array of JavaScript objects to the series __data__ property.
            


 __html__
    


				<div id="polarAreaWithFields" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarArea',
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

The __line__ property holds the settings to customize the area border line. There are three settings exposed: 
              __color__, __opacity__, and __width__. Below is an example of line 
              customization.
            


 __html__
    


				<div id="polarAreaBorder" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarArea',
	                    data: [
							[ 0, 26.7],
							[ 60, 18.3],
							[ 120, 35.1],
							[ 180, 26.4],
							[ 240, 29.3],
	                        [ 300, 17.9],
	                        [ 360, 26.7]
						],
	                    line: {
	                        color: '#336699',
	                        opacity: 0.5,
	                        width: 5
	                    }
					}],
	                theme: 'light'       
				}">
				</div>



Here is the resulting chart with Polar Area series.
            ![chart-polar-area-line](../Media/Controls\Chart\chart-polar-area-line.png)

# markersCustomizing Markers

By default the data points in a Polar Area series are not displayed. To show them and customize the way they are visualized, use 
              the settings exposed by the __markers__ property. They include __background__, 
              __border__ settings, __size__, __type__ 
              (*'circle'*, *'square'*, and *'triangle'*), 
              and __visible__. Here is an example of how to display and customize the data points markers.
            


 __html__
    


				<div id="polarAreaMarkers" data-win-control="Telerik.UI.RadChart" data-win-options="{
					series: [{ 
						type: 'polarArea',
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
	                            color: '#000'
	                        },
	                        size: 6,
	                        type: 'square',
	                        visible: true
	                    }
					}],
	                theme: 'light'       
				}">
				</div>



Below is an image of the chart with Polar Area series and data point markers.
            ![chart-polar-area-markers](../Media/Controls\Chart\chart-polar-area-markers.png)

# Related Topics
