---
title: Types
meta_title: Types
meta_description: description.
slug: 
tags:types
publish:True
---


RadSparkline offers the following sparkline types:

* 

Line

* 

Bar

* 

Column

* 

Area

* 

Pie

* 

Bullet

This help article introduces them and their specifics.

# lineLine

The line-type sparkline visualizes data as a continuous line on a Cartesian coordinate system where values are laid out on an implicit Y-axis.

TThe following code sample shows a sample This is a sample definition and the resulting line-type sparkline definition and its result:


 __html__
    


				<span id="line" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'line',
					data: [952, 940, 937, 980, 966, 965, 928, 916, 910, 980, 950],
					height: 50,
					width: 100,
					theme: 'light'
				}"></span>

![sparkline-types-line](../Media/Controls\Sparkline\sparkline-types-line.png)

# barBar

The bar-type sparkline visualizes data in horizontal bars on a Cartesian coordinate system where values are laid out on an implicit X-axis. In a sparkline,
					you would usually use a single bar to visualize one value. For multiple values, you can use line, column or area type.
				

The following code sample shows a sample bar-type sparkline definition and its result:


 __html__
    


				<span id="bar" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'bar',
					data: [952],
					theme: 'light'
				}"></span>

![sparkline-types-bar](../Media/Controls\Sparkline\sparkline-types-bar.png)

# columnColumn

The column-type sparkline visualizes data in columns in a Cartesian coordinate system where values are laid out on an implicit Y-axis.

The following code sample shows a sample column-type sparkline definition and its result:


 __html__
    


				<span id="column" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'column',
					data: [952, 940, 937, 980, 966, 965, 928, 916, 910, 980, 950],
					height: 50,
					width: 100,
					theme: 'light'
				}"></span>

![sparkline-types-column](../Media/Controls\Sparkline\sparkline-types-column.png)

# areaArea

The area-type sparkline visualizes data as a portion of the Cartesian coordinate system where values are laid out on an implicit Y-axis.

The following code sample shows a sample area-type sparkline definition and its result:


 __html__
    


				<span id="area" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'area',
					data: [952, 940, 937, 980, 966, 965, 928, 916, 910, 980, 950],
					height: 50,
					width: 100,
					theme: 'light'
				}"></span>

![sparkline-types-area](../Media/Controls\Sparkline\sparkline-types-area.png)

# piePie

The pie-type sparkline visualizes data as arc segments on a radial coordinate system. The sum of all data points in a pie series is considered a full
					pie (a 360-degree arc). Each single data point is represented as a portion of the full pie.
				

The following code sample shows a sample pie-type sparkline definition and its result:


 __html__
    


				<span id="pie" data-win-control="Telerik.UI.RadSparkline" data-win-options="{
					type: 'pie',
					data: [952, 940, 937, 980, 966],
					height: 100,
					width: 100,
					theme: 'light'
				}"></span>

![sparkline-types-pie](../Media/Controls\Sparkline\sparkline-types-pie.png)

# bulletBullet

The bullet-type sparkline displays a single measure (in the form of a bar), that is compared to a single point (target). You can combine it with plot bands
					to better visualize the scale and achieve a bullet graph look.
				

The following code sample shows a sample bullet-type sparkline definition and its result:


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

![sparkline-types-bullet](../Media/Controls\Sparkline\sparkline-types-bullet.png)

# Related Topics
