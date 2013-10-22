---
title: Create a Bullet Graph Using RadChart
meta_title: Create a Bullet Graph Using RadChart
meta_description: description.
slug: 
tags:create,a,bullet,graph,using,radchart
publish:True
---


The bullet graph is a variation of the bar graph and is used as a replacement for dashboard gauges and meters. It is simple 
      and provides more information than its alternatives. The bullet graph features a single measure bar, provides a comparative measure (a target), 
      and displays it in the context of qualitative ranges of performance, such as poor, satisfactory, and good.

# Section1

With its rich customization options __RadChart__ is capable of producing bullet graphs and customizing them to 
          your needs. The following article will provide a basic example of how to create a bullet graph using __RadChart__.
        

In this particular case the __RadChart__ control is initialized programmatically, but you can also initialize it in the mark-up.
        


 __html__
    


	
				<div id="bulletgraph"></div>
	



Basically, a bullet graph is a bullet series chart with a single data entry in its series and colored qualitative ranges.
          Here is a list of property options you need to set up in order to create a bullet graph:
        

* 

*Set up dimensions.* You can set the __width__ and __height__ according 
              to your needs. In the current example, they are set to *400* and *90* respectively. Note 
              that these are the width and height of the whole control including the title and the axis.
            

* 

*Set up chart title.* You can set and customize a title for the bullet graph through __RadChart's title__ 
            property. You can alter __text__, __align__, __font__, __padding__, 
            __margin__ and more. A full list of the exposed properties can be found at: 
            T:Telerik.UI.Chart._TitleConfiguration.
            

* 

*Set up the series.* Here is a list with the properties you can set to achieve the bullet graph look.
            

* 

In order to produce a bullet graph, you need to use __RadChart's__ bullet series. You need only one data entry as the 
                bullet graph has a single measure bar. The bullet series data entry has two values - one for the measure and one for the target. In the 
                current scenario the series data is bound to local variables, defined in the application, but you can also use __dataSource__ to 
                get remote data or JSON objects.
              

* 

Set the __color__ of the measure bar through the series' __color__ property.
              

* 

You can use the series' __gap__ property to set the measure bar's thickness. The __gap__ property value 
                sets the proportion between the plot area height and the bar thickness (i.e. "gap: 3" means the bar thickness is one third of the plot area height).
              

* 

Customize the target's properties. You can set __color__ and __line__ properties such as 
                __width__ or __visible__.
              

* 

*Hide the Category Axis.* Since there is only one data entry in the series, the category axis is redundant. You can 
              hide it through setting its __visible__ property to *false*.
            

* 

*Set the Value Axis.* Here is a list with the properties you can alter to achieve the bullet graph look:
            

* 

Set __min__ and __max__ values for the axis. In this case they are set to 0 and 300 respectively.
                

* 

Hide the __majorGridLines__ through setting their __visible__  property to *false*. 
                  These are the lines that cross the chart plot area and help for better understanding of the series values, especially when there are multiple data entries. 
                  Since the bullet graph has qualitative color areas, which serve the same purpose, the grid lines are redundant. The __minorGridLines__ 
                  are hidden by default, so you do not need to hide them explicitly.
                

* 

You can alter the __majorUnit__ and __minorUnit__ properties of the bullet series. These are the units 
                  that you will have between major ticks and minor ticks. In the current example they are set to 50 and 10 respectively.
                

* 

Additionaly you can change the properties of the major and minor ticks through __RadChart's majorTicks__ and 
                  __minorTicks__ properties. In the current example their sizes are set to be equal. That means the only difference between 
                  the major and minor ticks is that the major ticks have values.
                

* 

Set the qualitative color areas of the bullet graph. You can achieve this through __RadChart's plotBands__ property. It is basically an 
                  array of objects with four instructions for the color areas: __from__, __to__, 
                  __color__ and __opacity__ (opacity is optional). For the purposes of the example three color areas have been 
                  set - from 0 to 200, from 200 to 250 and from 250 to 300 - all with different shades of gray.
                

Here is a sample code for creating a bullet graph with __RadChart__.
        


 __js__
    


				    var bulletGraph = new Telerik.UI.RadChart(document.getElementById('bulletgraph'), {
				        height: 90,
				        width: 400,
				        title: {
				            text: "Revenue 2012 YTD (US $ in thousands)",
				            align: "left",
				            font: "14px Segoe UI",
				            padding: {
	                            left: 0
				            },
				            margin: {
	                            left: 4
				            }
				        },
				        series: [{
				            type: "bullet",
				            color: "#CCFA00",
				            data: [[bulletGraphValue, bulletGraphTarget]],
				            gap: 4,
				            target: {
				                color: "#FF810C",
				                line: {
				                    width: 3,
				                }
				            }
				        }],
				        categoryAxis: {
				            visible: false
				        },
				        valueAxis: {
				            min: 0,
				            max: 300,
				            majorGridLines: {
				                visible: false
				            },
				            majorUnit: 50,
				            majorTicks: {
				                size: 4
				            },
				            minorUnit: 10,
				            minorTicks: {
				                visible: true,
				                size: 4
				            },
				            plotBands: [
	                        { from: 0, to: 200, color: "#111111"},
	                        { from: 200, to: 250, color: "#6B6B6B"},
	                        { from: 250, to: 300, color: "#A0A0A0"},
				            ]
				        },
				        theme: "light"
				    });



Here is an image of the bullet graph produced with the code above.
        ![chart-bullet-graph](../Media/Controls\Chart\chart-bullet-graph.png)

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Chart/CreateBulletGraph*.
        

# Related Topics

 * [Bullet]({{slug:bullet}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Category Axis]({{slug:category-axis}})

 * [Value Axis]({{slug:value-axis}})
