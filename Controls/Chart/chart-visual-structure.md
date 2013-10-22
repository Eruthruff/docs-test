---
title: Visual Structure
meta_title: Visual Structure
meta_description: description.
slug: 
tags:visual,structure
publish:True
---


This article explains the visual elements of the RadChart control.

# Common Structure

The image below shows the common visual elements in all chart types.

# Visual Structure![Common visual structure](../Media/Controls\Chart\chart-common-structure.png)

# Description of Chart elements

Name

Description

Title

The title of the chart. By default, no title will appear until you set one explicitly.
									

Plot Area

This is where the chart series are drawn. The plot area can be blank or can display a grid of lines that make data values
										easier to read on a chart with axes.
									

[Series](15e0c300-a141-495d-9355-3d2d35951bd4)

Series are the actual visual representation of data. Each figure drawn by the series (a bar, a bubble, a point in a line, etc.)
										represents a single data value, or the crossing point when having a XY-type chart.
									

[Tooltip](2d4f6986-e8b9-46c6-bcc9-8d9e97f65530)

The tooltip is a text element that hovers (when tooltips are enabled) over a data point. It is used to display additional 
										information about the point.
									

[Legend](03a5bd22-3ae3-4b2c-afe9-18ccbb4809cf)

The chart legend appears next to the plot area (could be positioned at top, right, bottom and left) and displays the name
										of the field visualized by each series in the chart, along with a colored figure, representing the color used to draw the
										corresponding series.
									

# Specific Elements of Categorical Charts

The elements specific to a categorical chart (column, bar, line, area) are shown below.

# Visual Structure of a Categorical Chart![Categorical chart elements](../Media/Controls\Chart\chart-categorical-structure.png)

# Description of elements

Name

Description

[Value Axis](5469340a-fd03-4793-9b78-aafcda0bf923)

In a Cartesian chart, data points are plotted on the value axis. You can have multiple value axes-one for each series in the
										chart.
									

[Category Axis](5469340a-fd03-4793-9b78-aafcda0bf923)

Displays the category of each data point in the series. For example, the points in time to which the data point corresponds.
									

# Specific Elements of XY-charts

Following you can see the specific elements of the XY-charts (scatter, scatter line, bubble).

# Visual Structure of XY-charts![XY chart structure](../Media/Controls\Chart\chart-xy-structure.png)

# Description of Elements in XY-charts

Name

Description

[X-axis](5469340a-fd03-4793-9b78-aafcda0bf923)

Scatter, scatter line and bubble series represent data points defined by two values. The first value is positioned on the X-axis.
										This is identical to positioning points in a Cartesian coordinate system with X and Y axes.
									

[Y-axis](5469340a-fd03-4793-9b78-aafcda0bf923)

The second axis used for positioning data points in an XY-based series.
									

# Specific Elements of Donut and Pie Charts

Donut and pie charts are radial and do not use axes. The only specific element they render that is not seen in charts displaying other series
					are connectors.
				

# Visual Structure of Donut and Pie Charts![Radial type chart visual structure](../Media/Controls\Chart\chart-radial-structure.png)

# Description of Donut and Pie Chart Connectors

Name

Description

Connectors

Connectors are the lines connecting the donut or pie sectors with their corresponding label.
									

# Related Topics
