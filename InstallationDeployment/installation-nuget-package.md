---
title: Using a NuGet Package
meta_title: Using a NuGet Package
meta_description: description.
slug: 
tags:using,a,nuget,package
publish:True
---


From Q1 2013 on, you can also download a nupkg file, which when used with the
				[Package Manager](http://visualstudiogallery.msdn.microsoft.com/27077b70-9dad-4c64-adcf-c7cf6bc9970c) in Visual
				Studio will provide you with the files needed to build your JS project, without installing an extension SDK. In this scenario,
				references are added only in HTML - to the .js and .css files of RadControls for Windows 8 / HTML.
			

This article describes how you can add RadControls for Windows 8 / HTML to your project as a NuGet package.

# Section1Installing RadControls from a NuGet Package

The steps that you need to perform are:

* 

Download RadControls_for_Windows_8_HTML_2013_1_219_NuGet_Dev.zip from Your Account and unzip it. If you do not know where to
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

From the displayed list, pick __HTML NuGet installation__ which will download
									the .zip archive containing the NuGet package.
								![installation-nuget 6](../Media/InstallationDeployment\installation-nuget_6.png)

* 

Copy the .nupkg file to a location of your choice.

* 

In Visual Studio open *Tools -> Options* and then locate
							__Package Manager__ in the tree on the left and expand it.
						

* 

Click on __Package Sources__ and you will see the following window:
						![installation-nuget 1](../Media/InstallationDeployment\installation-nuget_1.png)

* 

Click the plus (__+__) button which will add a new package. Type a name for the package such as __
								RadControls for Windows 8 HTML
							__. For the Source locate the .nupkg file that you just unzipped and click __OK__.
						![installation-nuget 2](../Media/InstallationDeployment\installation-nuget_2.png)

* 

Right-click on your project and choose Manage NuGet packages. On the left, expand the Online node and locate the
							package that has the Name you typed in the previous window (in our example - __RadControls for Windows 8 HTML__).
						![installation-nuget 3](../Media/InstallationDeployment\installation-nuget_3.png)

* 

Click Install. After the package is installed, your project will have a new folder, __Telerik.UI__,
							containing all files needed to run RadControls for Windows 8 / HTML.
						![installation-nuget 4](../Media/InstallationDeployment\installation-nuget_4.png)

* 

Add references in your HTML to the following files in this exact order:

	
							<link href="Telerik.UI/css/common.css" rel="stylesheet" />
							<link href="Telerik.UI/css/dark.css" rel="stylesheet" />
							<script src="Telerik.UI/js/jquery.js"></script>
							<script src="Telerik.UI/js/ui.js"></script>
						



Now you can use the controls in your project. Note that there isn't an SDK installed, so you will not find them in the
					References window.
				

# Updating the package

To update RadControls for Windows 8 / HTML, you need to replace the older package file with a newer version in the same directory and then update it in
					Visual Studio through the __Manage NuGet packages__ dialog box. Now, instead of Online, choose the
					__Updates__ option and then click __Update__ button shown for the 
					__RadControls for Windows 8 HTML__
					package.
				![installation-nuget 5](../Media/InstallationDeployment\installation-nuget_5.png)

# Related Topics
