---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---
![Chart](../Media/Controls\Chart\Chart.png)

RadChart for Windows Runtime JavaScript applications is a versatile charting component specifically designed for creating Windows Store JavaScript applications.
				It offers unmatched performance regarding loading time, drawing capabilities and real-time updates.
				Its intuitive object model and public API allow complex charts to be easily setup either in HTML or through JavaScript.
				The control is completely data aware and may work in bound or unbound mode, depending on the requirements. Through tight
				integration with the DataSource component, RadChart can visualize data both from a local array or straight from an external data
				feed. Below is an example of the RadChart used in a real life scenario.
			![chart-overview](../Media/Controls\Chart\chart-overview.png)

# Architecture

A charting component in general is used to visualize (or plot) some data in a human-readable way through different
					representations like lines, areas, bars pies, etc. Each series has a collection of data points and knows how to visualize them.
					Different series types may process certain types of data points – for example categorical series may contain categorical data
					points. Data points may be added directly to a series or a data binding mechanism may be used to create the appropriate data
					points from a data source.
				

# RadChart

RadChart implements the architecture described above and offers the following types of charts (represented by their series
					types):
				

# Categorical Charts

Categorical charts such as [Bar](bb03ac0d-401c-45fe-872e-7e4501570e84),
							[Column](b2c907b7-ef80-4a43-a2f4-02fc42b3211f),
							[Line](53149c9c-fffe-4443-9a03-1c49fddaacd5) and
							[Area](b4da469c-6173-49ac-8ee8-65b63a252615) use one category axis and one value axis.
							The axis orientation (horizontal or vertical) is inferred from the series type.
						![chart-overview-01](../Media/Controls\Chart\chart-overview-01.png)

# XY Charts

XY charts such as [Scatter](8b72db8e-3e99-48ac-ac47-49433e5e3fc2) (see image below),
							[Scatter Line](a67f8b22-95e8-4e9d-ae3d-c104c43655a2) and
							[Bubble](9712a4e6-abf0-464b-bf37-02060d46a5b2) use one or more X and Y axes and show the crossing point of two values, each
							laying on a different value axis. These axes are configured through the
							__xAxis__ and the __yAxis__ properties. Bubble charts visualize one more value -
							volume, represented by the bubble size.
						![chart-overview-02](../Media/Controls\Chart\chart-overview-02.png)

# Radial Charts

Radial charts, such as [Pie](922320e0-7122-431a-a29d-a5b3a61af847) and
							[Donut](04e80fa7-a792-422c-aa2d-e84d24ff5a10), use a radial scale. Each data point in the series is represented as an arc
							segment, the value of which represents the ratio of the data point's value to the total value of all data points in the series.
						![chart-overview-03](../Media/Controls\Chart\chart-overview-03.png)

# Stock Charts

Stock charts, such as [Candlestick](11ba012b-cff5-46da-92d4-b37b382d7efd) and
							[Ohlc](d6f2af06-d7e0-4008-8c71-cc0d7e652753) charts, can be technically considered a subset of
							categorical charts that has a specific usage. They use one category axis, where categories always represent a period of
							time, and one value axis. A single data point visualizes four values-open, close, high and low representing changes in
							a value during a given period.
						![chart-overview-04](../Media/Controls\Chart\chart-overview-04.png)

# Related Topics
