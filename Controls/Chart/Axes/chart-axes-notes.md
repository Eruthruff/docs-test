---
title: Notes
meta_title: Notes
meta_description: description.
slug: 
tags:notes
publish:True
---


From Q3 2013, RadChart adds up the possibility to add notes to your category or value axes. The notes feature is highly customizable using the multiple
				configuration options available.
			

# Section1Configuring Notes

Notes can be displayed for any axis. To list the notes that you want to display for an axis, use the __axis.notes.data__ property. The

				

* 

__value__: The axis value for which the note should be displayed. If you want to display notes for the category axis, specify the
							index of the category (0-based) at which the note should appear.
						

* 

__position__: Specifies the position of the axis note. Accepted values are: *"top"*,
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

__visible__: A Boolean value that determines the visibility of the icon. If set to *false*,
									only the note label and the line connecting the label to the axis will be visible.
								

* 

__line__: The axis note line settings. They include __color__, __length__, and
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
									__value__ which is the current axis value.
								

* 

__visible__: A Boolean property that controls the label visibility.
								

* 

__visible__: A Boolean property that controls the visibility of the entire note.
						>
						All properties listed above, except for <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">value</legacyBold> and <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">label.text</legacyBold>, can be defined:
					

* 

Separately for each note—inside each object in the __axis.notes.data__ array.
							

* 

For all notes belonging to the current axis—inside the __axis.notes__ object.
							

* 

For all notes belonging to all chart axes—inside the __axisDefaults.notes__ object.
							

The following example shows a RadChart with two value axes. Each axis has notes defined. Properties that are common for all notes are defined using the
					__axisDefaults.notes__ property. The properties specific to each axis notes' are assigned to the __axis.notes__ property.
				


 __html__
    


		<div id="chartWithNotes" data-win-control="Telerik.UI.RadChart" data-win-options="{
			legend: {
				position: 'bottom'
			},
		    series: [{
		        name: 'Temperature',
		        data: [20, 27 , 32],
		        axis: 'temperature',
		        color: '#1E98E4'
		    }, {
		        name: 'Humidity',
		        data: [65, 78, 60],
		        axis: 'humidity',
		        color: '#f99'
		    }
		    ],
			seriesDefaults: {
				type: 'area'
			},
		    categoryAxis: {
		        categories: ['May', 'Jun', 'Jul'],
		        axisCrossingValue: [0, 3]
			},
			axisDefaults: {
				notes: {
					line: {
						color: 'lightgray',
						length: 30
					},
					icon: {
						visible: false
					},
					label: {
						font: '12pt Segoe UI',
						color: 'orange'
					}
				}
			},
		    valueAxis: [{
		        name: 'temperature',
				notes: {
					data: [
						{
							value: 5, 
							label: {
								text: 'Cold'
							}
						},{
							value: 18, 
							label: {
								text: 'Warm'
							}
						},{
							value: 30, 
							label: {
								text: 'Hot'
							}
						}
					],
					position: 'left'
				}
				}, 
				{
		        name:'humidity',
				notes: {
					data: [
						{
							value: 45, 
							label: {
								text: 'Dry'
							}
						},{
							value: 70, 
							label: {
								text: 'Humid'
							}
						}
					],
					position: 'right'
				}
		    }],
		    width: 600,
		    height: 350,
			theme: 'light'
		}">
		</div>



The result from the above code snippet is shown in the following image.![chart-axes-notes](../Media/Controls\Chart\chart-axes-notes.png)

# Related Topics

 * [Notes]({{slug:notes}})
