---
title: Localization
meta_title: Localization
meta_description: description.
slug: 
tags:localization
publish:True
---


RadDatePicker and RadTimePicker support automatic localization of their strings, using resource files. The setup is simple and this article
				describes the steps needed to provide localization for these two controls.
			

# Section1Localizing RadDatePicker and RadTimePicker

Following is the set of steps that you can follow:

* 

At the root level of you application, create a __strings__ folder. It will host the localization resources.
						

* 

Create a separate folder for each language that you want to support and name it after the corresponding locale, e.g. fr-FR.
						

* 

Go to *C:\Program Files (x86)\Telerik\RadControls for Windows 8 HTML QX 201X\strings\en* and copy
							the __raddatepicker.resjson__ and/or the __radtimepicker.resjson__ files. Paste them in
							each language's folder.
						

The correct folder structure should look like this:![datepicker-localization](../Media/Controls\DatePicker\datepicker-localization.png)

* 

Translate the provided messages to the corresponding language and save the files.

Now, the controls will use the current culture of the application, which would be either the user default culture (if supported), the
					default culture provided in __package.appxmanifest__ or the one that you have provided by overwriting the primary
					language of the application. For more information on the application's way of handling cultures, check the MSDN resource, linked at the
					end of this article.
				

# Related Topics

 * [Localization]({{slug:localization}})[How to manage language and region](http://msdn.microsoft.com/en-us/library/windows/apps/hh967758.aspx)
