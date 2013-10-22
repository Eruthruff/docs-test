---
title: Plot Bands
meta_title: Plot Bands
meta_description: description.
slug: 
tags:plot,bands
publish:True
---


RadSparkline axes can be configured to display bands with different colors for predefined value ranges. They can be used to outline a specific
				range of values. In sparkline scenarios they are especially useful with the bullet type, where you can use them to achieve a bullet graph
				look.
			

# Section1Configuring Plot Bands

To add plot bands to your chart, you should assign the __axis.plotBands__ property an array of objects having the following
					format:
				

	
					{
					from: x, //where x is a number representing a start value on the axis
						to: y, //where y is number representing an end value on the axis
						color: "value", // where "value" is any valid CSS color
						opacity: z //where z is a number, between 0 and 1, representing the bands opacity
					}
				



For example:


 __html__
    


				<span id="bullet" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'bullet',
					data: [955, 980],
					valueAxis: {
						plotBands: [
							{from: 0, to: 950, color: '#787878', opacity: 0.15},
							{from: 950, to: 980, color: '#787878', opacity: 0.45}
						]
					},
					theme: 'light'
				}"></span>



This will produce the following result:![sparkline-types-bullet](../Media/Controls\Sparkline\sparkline-types-bullet.png)

# Related Topics
