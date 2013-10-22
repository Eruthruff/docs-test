---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


Structurally and functionally, RadDatePicker and RadTimePicker are nearly identical, so they can be configured and used in the same way with two minor 
				exceptions. Both controls work with Date object values. The RadDatePicker uses the date components of the object (year, month and date) while the 
				RadTimePicker uses the time components (hour and minute; the period is determined from the data available in a Windows.Globalization.Calendar object). 
				The other difference is in the format property, which has different values in the two controls corresponding to whether you are modifying date or time values.
			

This help article describes the configuration options of the RadDatePicker and RadTimePicker controls.
			

# rendering-modeControl Display Modes

You can control the way RadDatePicker and RadTimePicker controls are displayed and function in the page using the __displayMode__
				property. It accepts two values, listed in the __Telerik.UI.RadDatePicker.DisplayMode__ and 
				__Telerik.UI.RadTimePicker.DisplayMode__ enumerations:
				

* 

__standard__: This is the default mode of the control. Both the picker and selector parts of the control are available. 
							The selector is opened when the picker button is clicked/tapped. Selection changes when the 'OK' button in the selector is pressed.
						

* 

__inline__: In this mode the picker part of the control is not available. The selector renders inline in the document and 
							is always open. Once the selected value of any of the lists changes, the *control.value* property is immediately 
							updated.
						

# control-configurationControl Configuration Options

The following properties are responsible for global behaviors of the control. In the next sections you will get acquainted with the options
					for configuring certain parts of its structure.
				

* 

__autoSizeWidth__: Use it to tell the control whether it should automatically calculate its picker width, so that it equals
							the width of the selector part.
						


 __html__
    


				<div id="picker1" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					autoSizeWidth: true
				}">
				</div>



* 

__culture__: Sets the culture locally for the control. The property takes a valid [BCP-47](http://tools.ietf.org/html/bcp47) language tag as a value. For more information regarding Telerik culture support you
              can visit this article: [Culture Support](d3c7ea15-4986-48fe-9cc7-db2f1c03a57f).
            


 __html__
    


				<div id="pickerFR" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					culture: 'fr-FR'
				}">
				</div>

![datepicker-culture](../Media/Controls\DatePicker\datepicker-culture.png)

* 

__displayValueFormat__: Determines how the edited value is displayed on the screen after it has been selected. If not set,
							the format from the current system clock configuration is used. The assigned value should conform to the common RadControls formats, listed in
							this help article: [](0c3b0ea5-3850-4c90-86b3-5d20f2a18c1e). 
						


 __html__
    


				<div id="picker2" data-win-control="Telerik.UI.RadTimePicker" data-win-options="{
					displayValueFormat: 'dddd, MMMM dd, yyyy'
				}">
				</div>

![Display value format](../Media/Controls\DatePicker\datepicker-display-value-format.png)

* 

__enabled__: Use this property to disable and re-enable the control. It accepts a boolean value indicating whether the user
							should be able to interact with the control.
						


 __html__
    


				<div id="picker3" data-win-control="Telerik.UI.RadTimePicker" data-win-options="{
					enabled: false
				}">
				</div>



* 

__isReadOnly__: Setting this property value to __true__ will prevent the user from changing the value of 
							the picker. The visual appearance of the picker is not changed, it is only the interaction with it that is prevented.
						


 __html__
    


				<h3>isReadOnly: true</h3>
				<div id="picker4" data-win-control="Telerik.UI.RadTimePicker" data-win-options="{
					isReadOnly: true
				}">
				</div>



* 

__minValue__: Use this property to set a minimum value for the picker. Note that the property accepts a Date object (or a
							string that can be parsed as a date) as a value but will use only the date part for RadDatePicker and only the time part for RadTimePicker.
						


 __html__
    


				<div id="picker5" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					minValue: '10/10/2012'
				}">
				</div>



* 

__maxValue__: Specifies the maximum allowed value for the picker. Same as with __minValue__, 
							__maxValue__ accepts a whole Date object (or a string that can be parsed as a date) but only the relevant part will be 
							used.
						


 __html__
    


				<div id="picker6" data-win-control="Telerik.UI.RadTimePicker" data-win-options="{
					minValue: '10/10/2012 1:00 PM',
					maxValue: '11/15/2012 6:59 PM'
				}">
				</div>



* 

__tabIndex__: Used to specify the position of the control in the tab order. Accepts an integer value; the default one is 0.
						

# header-settingsHeader Settings

To display content above the picker control, use the __header__ property. You can assign it a string or data object. In
					case the value is an object, you also need to set a __headerTemplate__ to specify which properties of the object will be
					rendered.
				


 __html__
    


				<div id="picker8" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					header: 'Pick a date for your trip:'
				}">
				</div>

![Header text](../Media/Controls\DatePicker\datepicker-header-text.png)


 __html__
    


				<div id="picker9" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					header: {Destination: 'Prague'},
					headerTemplate: 'Pick a date for your trip to #=Destination#:'
				}">
				</div>

![Header template](../Media/Controls\DatePicker\datepicker-header-template.png)

# empty-text-templateDisplaying Empty Text/Template

Similar to the header, you can specify a string or data object as a value of the __emptyContent__ property. It will be displayed
					in the picker when there is no date selected yet. Again, if the assigned value is an object, you need to define a template to describe which properties of the
					object will be displayed.
				


 __html__
    


				<div id="picker10" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					emptyContent: 'Trip date...'
				}">
				</div>

![Empty content text](../Media/Controls\DatePicker\datepicker-empty-content.png)


 __html__
    


				<div id="picker11" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					emptyContent: {Destination: 'Prague'},
					emptyContentTemplate: 'Trip to #=Destination# date...'
				}">
				</div>

![Empty Content Template](../Media/Controls\DatePicker\datepicker-empty-content-template.png)

# selector-settingsSelector Settings

# selector-headerCustomizing the Selector Header

The selector header is one more part of the control that can be customized. The combination of the __selectorHeader__ and
							__selectorHeaderTemplate__ properties allow you to either specify a string, a combination of an object and a template, or only a
							template that will populate the area at the top of the selector.
						


 __html__
    


				<div id="picker12" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					selectorHeader: 'Pick a Date'
				}">
				</div>

![Selector header](../Media/Controls\DatePicker\datepicker-selector-header.png)


 __html__
    


				<div id="picker13" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					selectorHeader:{Destination: 'Prague'},
					selectorHeaderTemplate: 'Pick a date for trip to: #=Destination#',
					autoSizeWidth: true
				}">
				</div>

![Selector header template](../Media/Controls\DatePicker\datepicker-selector-header-template.png)

# formatting-selectorFormatting the Selector

To specify which editable parts of the selector should be visible to the user, you can use the __selectorFormat__ property.
							Its value defines how the different selector components will be ordered. By setting this property, you can also define which editable parts of
							the selector will be visible. For example, *'y/m'* will display the __Year__ and
							__Month__ components in a DatePicker. Valid values are a string permutation of the following:
						

RadDatePicker

* 

__y__ - year
								

* 

__m__ - month
								

* 

__d__ - day
								

RadTimePicker

* 

__h__ - hour
								

* 

__m__ - minute
								

* 

__t__ - period [AM/PM]
								>
								Whether or not the period list (containing the values 'AM' and 'PM') appears
								depends also on the system settings. If the system short time pattern is in 24-hour mode,
								the period list will not appear even if the 't' component is passed
								to the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">selectorFormat</legacyBold> property.
							


 __html__
    


				<div id="picker14" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					selectorFormat: 'm/y'
				}">
				</div>

![Selector format](../Media/Controls\DatePicker\datepicker-selector-format.png)


 __html__
    


				<div id="picker15" data-win-control="Telerik.UI.RadTimePicker" data-win-options="{
					selectorFormat: 'm'
				}">
				</div>

![RadTimePicker selector format](../Media/Controls\DatePicker\datepicker-timepicker-selector-format.png)

# default-valueChanging the Default Value

The __selectorDefaultValue__ property represents the default value displayed in the selector part. The default value
							is shown when the value property is not set (null/undefined). If no default value is specified, the current date/time on the system is displayed
							when the selector opens.
						

# selector-show-hideShowing and Hiding the Selector

If you want to display the selector at all times and not only when the user clicks it, set the __isSelectorOpen__ property
							to __true__. Its value is false by default. You can also programmatically toggle the value of the control if under different
							than the default conditions, you want the selector to show and hide (for example, once the user fills in another form control).
						


 __html__
    


				<div id="picker16" data-win-control="Telerik.UI.RadDatePicker">
				</div>
				<button style="display: block" id="showSelectorBtn">Show the selector</button>




 __js__
    


					document.getElementById("showSelectorBtn").onclick = function () {
						var picker = document.getElementById("picker16").winControl;
						picker.isSelectorOpen = true;
					};



# selector-itemsCustomizing the Appearance and Content of Selector Items

# item-countModifying Item Count

Use the __itemCount__ property to set the number of items visible within the selector part of the control. This property is used to
							determine the height of the selector part when opened. The calculated height will not exceed the height of the view port. 
						


 __html__
    


				<div id="picker17" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					itemCount: 1
				}">
				</div>

![Item count](../Media/Controls\DatePicker\datepicker-item-count.png)

# item-width-heightControlling Item Width and Height

Using the __itemLength__ property, you can specify a numeric value that will set the width and height of the items
							displayed in the selector part of the control. The same value is used for both dimensions of the items.
						


 __html__
    


				<div id="picker18" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					itemLength: 65
				}">
				</div>

![Item length](../Media/Controls\DatePicker\datepicker-item-length.png)

# item-spacingChanging Spacing Between Items

If you want to increase or decrease spacing between the items that appear in the selector part of the control, change the
							__itemSpacing__ property value. Note that this property also determines the spacing between the different parts
							of the selector, e.g. lists, buttons, header.
						


 __html__
    


				<div id="picker19" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					itemSpacing: 15
				}">
				</div>

![Item spacing](../Media/Controls\DatePicker\datepicker-item-spacing.png)

# item-templateTemplating the Selector Items

You can provide a template for the actual selector items as well. With this property the default template can be overriden. Internally, all
							items are bound to a data object having a __value__ field that corresponds to the number that represents the current year, 
							month, hour, etc. There is a second __label__ field available for RadDatePicker which holds the name of the month, day, 
							and whether the year is leap. In order to utilize either or both of the data object properties, the template should have mappings to them, e.g., 
							#= value #'#= label #'.
						


 __html__
    


				<div id="picker20" data-win-control="Telerik.UI.RadDatePicker" data-win-options="{
					itemTemplate: '&lt;h2&gt;#=value#&lt;/h2&gt; &lt;h6&gt;#=label#&lt;/h6&gt;'
				}">
				</div>

![Item template](../Media/Controls\DatePicker\datepicker-item-template.png)

# Related Topics
