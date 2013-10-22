---
title: Localization
meta_title: Localization
meta_description: description.
slug: 
tags:localization
publish:True
---


# Localization

Localizing __RadControls for Windows 8 HTML__ is no different than localizing an app.
				([Here is some more info](http://msdn.microsoft.com/en-us/library/windows/apps/hh943060.aspx) about localizing a Windows Store app using JavaScript and HTML.)
			

If you need to localize a RadControl, you will also need to know the names of the supported strings and
				their purpose. You can find the preset __.resjson__ files in your RadControls
				installation directory, e.g.
				__
						'C:\Program Files (x86)\Telerik\RadControls for Windows 8 HTML Q3 2012\strings\en'
					__
				and copy them to the directories of all locales, for which you would like to prepare your app, e.g., de-De, fr-CA, etc.
			![app localization strings](../Media/Localization\app_localization_strings.PNG)>
					The RadControls strings are isolated in a separate resource map for each control,
					e.g. <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">strings\en\raddatepicker.resjson</legacyBold> for common use and easier maintenance.
				

Then you can translate each string in the file as you would normally
				do for the rest of the string resources in your app.
			![resjson file content](../Media/Localization\resjson_file_content.PNG)

The following controls have built-in strings and support localization:
			

* 

__
									DatePicker and TimePicker
								__

* 

__
									Grid
								__

* 

__
									NumericBox
								__

* 

__
									Slider
								__

# Related Topics

 * [Overview]({{slug:overview}})
