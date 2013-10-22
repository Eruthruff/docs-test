---
title: Localization
meta_title: Localization
meta_description: description.
slug: 
tags:localization
publish:True
---


RadSlider supports automatic localization of its strings, using resource files. The setup is simple and this article
				describes the steps needed to provide localization for this control.
			

# Section1Localizing RadSlider

Follow these steps to localize RadSlider/RadRangeSlider:

* 

At the root level of you application, create a __strings__ folder. It will host the localization resources.
						

* 

Create a separate folder for each language that you want to support and name it after the corresponding locale, e.g. __fr-FR__.
						

* 

Go to *C:\Program Files (x86)\Telerik\RadControls for Windows 8 HTML QX 201X\strings\en* and copy
							the __radslider.resjson__ file. Paste it in each language's folder.
						

The correct folder structure should look like this:![slider-localization](../Media/Controls\Slider\slider-localization.png)

* 

Translate the provided messages to the corresponding language and save the file.

The control will use the current culture of the application, which would be either the user default culture (if supported), the
					default culture provided in __package.appxmanifest__, or the one that you have provided by overwriting the primary
					language of the application. For more information on the application's way of handling cultures, click to read the MSDN resource, "How to manage 
					language and region", linked at the
					end of this article.
				

# Related Topics

 * [Localization]({{slug:localization}})[How to manage language and region](http://msdn.microsoft.com/en-us/library/windows/apps/hh967758.aspx)
