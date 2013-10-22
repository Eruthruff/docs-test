---
title: Hiding the Trial Message
meta_title: Hiding the Trial Message
meta_description: description.
slug: 
tags:hiding,the,trial,message
publish:True
---


Once you purchase RadControls for Windows 8, you will want to remove the trial message that shows upon running your Windows Store App, which uses a
				control from the suite. This help article elaborates on the steps you can follow to replace the trial version of the controls with a developer one.
			

# Section1How to Hide the Trial Message After Obtaining a Developer License

To hide the trial message, you must upgrade your RadControls to a developer version of the installation. To do so, follow the steps below:

* 

Uninstall the trial version of the suite. To do so, go to __Control Panel__, locate and uninstall
							__Telerik RadControls for Windows 8 HTML QX 20XX__.
						

* 

Choose one of the options for installing RadControls for Windows 8 (the non-trial version) -
							[automatically](92854f93-3cf6-4198-b502-34a3787524f2) or
							[manually](f217a83d-a467-43a3-af6f-006d95e910d6) and perform a new installation of a licensed
							version of the product.
						

* 

If your choice of installation provides an SDK, you should update your project references.
							Open your project and expand its *References* node. Remove any old references to __
								RadControls for
								Windows 8 HTML
							__ and add a new one to the version of the suite that you have just installed and rebuild your app.
						

If all has gone well, you should not see the trial message anymore.

# Related Topics
