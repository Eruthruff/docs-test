---
title: Localization
meta_title: Localization
meta_description: description.
slug: 
tags:localization
publish:True
---


RadGrid supports automatic localization of its strings, using resource files. The setup is simple and this article
				describes the steps needed to provide localization for this control.
			

# Section1Localizing RadGrid

Following is the set of steps that you can follow:

* 

At the root level of you application, create a __strings__ folder. It will host the localization resources.
						

* 

Create a separate folder for each language that you want to support and name it after the corresponding locale, e.g. fr-FR.
						

* 

Go to *C:\Program Files (x86)\Telerik\RadControls for Windows 8 HTML QX 201X\strings\en* and copy
							the __radgrid.resjson__ file. Paste it in each language's folder.
						

The correct folder structure should look like this:![grid-localization](../Media/Controls\Grid\grid-localization.png)>
								In some scenarios (usually data operation features) RadGrid displays other RadControls. If they are localizable, you need to copy their
								files and translate them as well. You can find a list of all localizable RadControls here:
								<link xlink:href="fc0cf5bc-16f0-4855-921f-9cb0d4497844" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" />

* 

Translate the provided messages to the corresponding language and save the file.

Now, the control will use the current culture of the application, which would be either the user default culture (if supported), the
					default culture provided in __package.appxmanifest__ or the one that you have provided by overwriting the primary
					language of the application. For more information on the application's way of handling cultures, check the MSDN resource, linked at the
					end of this article.
				

# Related Topics

 * [Localization]({{slug:localization}})[How to manage language and region](http://msdn.microsoft.com/en-us/library/windows/apps/hh967758.aspx)
