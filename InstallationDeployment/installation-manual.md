---
title: Manual Installation
meta_title: Manual Installation
meta_description: description.
slug: 
tags:manual,installation
publish:True
---


From Q1 2013 on, the manual installation package of RadControls for Windows 8 / HTML also provides an [extension SDK](http://msdn.microsoft.com/en-us/library/jj161096.aspx). This article explains how to perform a manual installation of RadControls for Windows 8 / HTML and be able to reference them in your
				project from the __Reference Manager__.
			

# Section1Manual Installation

The steps that you need to perform are:

* 

Download RadControls_for_Windows_8_HTML_201X_X_XXX_Dev.zip to your machine and unzip it. If you do not know where to
							find this file, do the following:
						

* 

Go to your [Telerik account](http://www.telerik.com/account/).
								

* 

Click on the __Products & Subscriptions__ link.
								![upgrading 1](../Media/InstallationDeployment\upgrading_1.png)

* 

On the next page click the __Download Installer and other resources__ button.
								![upgrading 2](../Media/InstallationDeployment\upgrading_2.png)

* 

Locate __RadControls for Windows 8__ in the displayed list of products and click the __
										Browse all
										product files
									__ link.
								![upgrading 3](../Media/InstallationDeployment\upgrading_3.png)

* 

From the displayed list, pick __HTML Manual installation__ which will download
									the .zip archive containing the installation files.
								![installation-manual 1](../Media/InstallationDeployment\installation-manual_1.png)

* 

You will find a folder named __ExtensionSDK__. Open it and copy its contents.

* 

Go to *C:\Program Files (x86)\Microsoft SDKs\Windows\v8.0\ExtensionSDKs\* and see if
							there is a __Telerik.UI__ folder in there. If there isn't, create it.
						

* 

Inside Telerik.UI create a folder named after the version of the controls that you want to see in the References
							window.
						

* 

Paste the __ExtensionSDK__ folder content into the newly created folder and restart Visual Studio if it is running.

Now you should see __RadControls for Windows 8 HTML__ in the References window. 

# Manual Update

Updating RadControls from a manual installation is done by creating a new folder in 
					*C:\Program Files (x86)\Microsoft SDKs\Windows\v8.0\ExtensionSDKs\* and updating the reference
					in your project. If the old version is no longer needed, you can delete its folder.
				

# Related Topics
