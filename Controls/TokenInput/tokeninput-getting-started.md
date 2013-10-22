---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The RadTokenInput control for Windows 8 is an HTML/JavaScript component that allows the user to select multiple items from predefined or live 
				 data. It then displays the selection as tokens.
				To use the control, you must specify a data source—you can use a __Telerik.Data.DataSource__ control or even a simple JavaScript array.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadTokenInput

To create a RadTokenInput in the HTML markup, add an empty __span__ element with a __data-win-control__ attribute
							with a value of __Telerik.UI.RadTokenInput__.
						

	
							<span data-win-control="Telerik.UI.RadTokenInput">
							</span>
						



Alternatively, you can create a RadTokenInput programmatically through JavaScript by first defining a __span__ element
							with an id and then passing this id as a first argument to the RadTokenInput constructor.
						

	
							<span id="myTokenInput">
							</span>
						



	
							var tokenInput = new Telerik.UI.RadTokenInput(document.getElementById("myTokenInput"));
						



Creating a __RadTokenInput__ without any properties set will not result in a usable control. __RadTokenInput__ 
              needs at least a basic set of data for the user to select from. You can find a basic example of how you can set property values below.
            

# optionsSetting RadTokenInput Options

Just like any other Windows Runtime JavaScript control, the RadTokenInput options can be defined through the __data-win-options__
							attribute.
						


 __html__
    


				<span id="markupTokenInput" data-win-control="Telerik.UI.RadTokenInput" data-win-options="{
						    dataSource: {
	                            data: ['McLaren', 'Mercedes', 'Red Bull Racing']
	                        },
	                        placeholder: 'Choose a team...'
						}"></span>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor.
						


 __html__
    


				<span id="codeTokenInput"></span>




 __js__
    


				    var tokenInput = new Telerik.UI.RadTokenInput(document.getElementById("codeTokenInput"), {
				        dataSource: {
				            data: ['McLaren', 'Mercedes', 'Red Bull Racing']
				        },
				        placeholder: 'Choose a team...'
				    });



Both the markup and the JavaScript versions produce the same result. Here is an image of the control and its usage:
            ![tokeninput-gettingstarted](../Media/Controls\TokenInput\tokeninput-gettingstarted.png)

# accessAccessing and Modifying RadTokenInput

You can get ahold of the RadTokenInput object the same way as the native WinJS components—find its DOM element and access its
							__winControl__ property.
						

	
							var tokenInput = document.getElementById("myTokenInput").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							tokenInput.placeholder = "Start typing...";
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var tokenInput = new Telerik.UI.RadTokenInput(document.getElementById("myTokenInput"), {
								onchange: changeHandlerFnName });
							// OR
							var tokenInput = new Telerik.UI.RadTokenInput(document.getElementById("myTokenInput"), {
								onchange: function(e) {//...}
							});
						

>
								If you attach the event handler as shown above, in HTML mark-up, you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							tokenInput.addEventListener("change", changeHandlerFnName);
						



# selectGetting and Setting Selected Items

To access the selected values in __RadTokenInput__, use its __value__ property.
            

	
              var tokenInput = document.getElementById("myTokenInput").winControl;
              var selectedValues = tokenInput.value; //Array of selected values or null if there is no selection
              var firstSelectedValue = selectedValues[0];
            



The __value__ property can also be used to set selected items. You can assign a single value or an array of values. If there is no 
              match, no value will be selected.
            

	
              tokenInput.value = 1;
              tokenInput.value = [1, 3, 5]; //Array of item values
            



If you want to get the raw data items from the data source corresponding to the selected items, use the __dataItems()__
              method:
            

	
              var tokenInput = document.getElementById("myTokenInput").winControl;
              var selectedData = tokenInput.dataItems(); //Array of selected items' corresponding data entries
            



In order to select an item programmatically, you have to use the __select()__ method. It takes a "li" HTML element as an 
              argument and selects it from the list. The __list__ property returns a jQuery-wrapped list of the "li" elements in the control. You can
              then use jQuery selectors to search for a given string value in the list. The following example shows how this can be done:
            

	
              var items = tokenInput.list;
              var toSelect = $("li:contains('Andrew Fuller')",items);
              tokenInput.select(toSelect);
            



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Item Template]({{slug:item-template}})

 * [Tag Template]({{slug:tag-template}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Events]({{slug:events}})

 * [Interact with RadTokenInput Programmatically]({{slug:interact-with-radtokeninput-programmatically}})
