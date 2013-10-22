---
title: Adding RadControls to an HTML Page
meta_title: Adding RadControls to an HTML Page
meta_description: description.
slug: 
tags:adding,radcontrols,to,an,html,page
publish:True
---


Before you start using the RadControls for Windows 8 / HTML you must make sure that they are installed correctly on the development machine and that your 
			Visual Studio project is using one of the JavaScript Windows Store templates.

# AddingProjectSectionAdding a Project Reference

Right-click on the project node in the Visual Studio Solution Explorer window and select "Add Reference...". In the newly opened window select the 
				checkbox next to "RadControls for Windows 8" and click OK to continue. After that you should see "RadControls for Windows 8 HTML" in the project references 
				next to "Windows Library for JavaScript 1.0".![add reference](../Media/InstallationDeployment\add_reference.png)

# AddingContentSectionAdding References on a Content Page

You must add the references to Telerik scripts and styles on each page where the controls will be used. Make sure the following code is present in the 
				head section of the page:

	
					<head>
					...
					<!-- Telerik references -->
					<link href="///Telerik.UI/css/common.css" rel="stylesheet" />
					<link href="///Telerik.UI/css/dark.css" rel="stylesheet" />
					<script src="///Telerik.UI/js/jquery.js"></script>
					<script src="///Telerik.UI/js/ui.js"></script>
					...
					</head>
				



Note the second CSS file reference in the code above. You should also add one of the skin-specific CSS files depending on which theme you are using in your application (dark/light):

	
					<link href="///Telerik.UI/css/dark.css" rel="stylesheet" />
					<!-- OR -->
					<link href="///Telerik.UI/css/light.css" rel="stylesheet" />
				



Now you should be able to see the Telerik classes in IntelliSense and can add a RadControl of your choice to the page.

For further instructions on adding the different RadControls, check their Getting Started articles.

# Related Topics[Using RadControls in a JavaScript-based Windows 8 Application (Telerik Helper blog)](http://telerikhelper.net/2012/11/02/using-radcontrols-in-javascript-based-windows-8-application/)
