---
title: Notes
meta_title: Notes
meta_description: description.
slug: 
tags:notes
publish:True
---


Similar to [axes notes](efda1238-d919-4b85-acf3-45bb7d9ca27b), from Q2 2013, RadChart features series notes. They allow you to display notes for the
				data points rendered by the series. The notes can be customized using the numerous properties exposed by the RadChart control.
			

# Section1Configuring Notes

A note can be displayed for each data point in a series. Note text is taken from the chart datasource. To enable notes, you need to set the
					__noteTextField__ property of the series to field from the assigned datasource that contains the notes. If for a given data point, there is
					no value in the corresponding data record, a note is not displayed. The properties exposed for customizing series notes, through the
					__series.notes__ and __seriesDefaults.notes__ properties, are listed below.
				

* 

__position__: Specifies the position of the series note. Accepted values are: *"top"*,
							*"bottom"*, *"left"*, and __"right"__.
						

* 

__icon__: Settings icon which appears around the note label. These settings include:
						

* 

__background__: Background color for the note. Any valid CSS color is accepted.
								

* 

__border__: Border settings for the note. Settings include __color__, __width__
									and __dashType__. __dashType__ accepts the following values:
									*"solid"*, *"dot"*, *"dash"*,
									*"longDash"*, *"dashDot"*, *"longDashDot"*,
									*"longDashDotDot"*.
								

* 

__size__: A numeric value specifying the size of the icon.
								

* 

__type__: Specifies the shape of the icon rendered for the current note. Accepted values are: *"circle"*,
									*"square"*, and *"triangle"*.
								

* 

__visible__: A Boolean value that determines the visibility of the note icon. If set to *false*,
									only the note label and the line connecting the label to the series will be visible.
								

* 

__line__: The series note line settings. They include __color__, __length__, and
							__width__.
						

* 

__label__: The note label settings. They include:
						

* 

__background__: The label background color. any valid CSS color is accepted.
								

* 

__border__: The label border settings. They include __color__, __width__
									and __dashType__. __dashType__ accepts the following values:
									*"solid"*, *"dot"*, *"dash"*,
									*"longDash"*, *"dashDot"*, *"longDashDot"*,
									*"longDashDotDot"*.
								

* 

__color__: The label text color. Any valid CSS color is accepted.
								

* 

__font__: Allows you to specify the font for the label. Since this will be used as a CSS style, to be able to apply it,
									you need to specify both font size and type, e.g. "12pt Segoe UI".
								

* 

__template__: The template which renders the labels. The field that can be used in the template is
									__value__ which is the current data point value.
								

* 

__visible__: A Boolean property that controls the label visibility.
								

* 

__visible__: A Boolean property that controls the visibility of the entire note.
						>
						All properties listed above can be defined:
					

* 

For all notes belonging to the current series—inside the __series.notes__ object.
							

* 

For all notes belonging to all chart series—inside the __seriesDefaults.notes__ object.
							

The example below shows a RadChart with notes field defined and some custom setting applied.


 __html__
    


		<div id="chartWithNotes" data-win-control="Telerik.UI.RadChart" data-win-options="{
			dataSource: {
				data: 
					[
						{ Year: '2008', Value: 8.7 },
						{ Year: '2009', Value: 5.5, Note: 'Financial crisis' },
						{ Year: '2010', Value: 4.5 },
						{ Year: '2011', Value: 4.8 },
						{ Year: '2012', Value: 10, Note: 'Best sales to date' },
						{ Year: '2013', Value: 9.3 }
					]
			},
		    series: [{
				type: 'line',
		        name: 'Product Sales',
				field: 'Value',
				noteTextField: 'Note',
				notes: {
					icon: {
						type: 'square',
						border: {
							color: 'pink'
						},
						background: 'pink'
					},
					line: {
						color: 'pink',
						length: 30
					},
					label: {
						color: 'gray'
					},
					position: 'top'
				}
		    }
		    ],
			categoryAxis: {
				field: 'Year'
			},
			width: 600,
		    height: 350,
			theme: 'light'
		}">
		</div>



The result from the above code snippet is shown in the following image.![chart-series-notes](../Media/Controls\Chart\chart-series-notes.png)

# Related Topics

 * [Notes]({{slug:notes}})
