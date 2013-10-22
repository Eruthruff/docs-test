---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The RadDropDownList control for Windows 8 is a HTML/JavaScript component that allows the user to select one item from a predefined or live (xhr requested) data.
				To use the control, you must specify a datasource - you can use a __Telerik.Data.DataSource__ control or even a simple JavaScript array.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to a HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadDropDownList

To create a DropDownList in the HTML markup, add an empty __span__ element with a __data-win-control__ attribute
							with a value of __Telerik.UI.RadDropDownList__:
						

	
							<span data-win-control="Telerik.UI.RadDropDownList">
							</span>
						



Alternatively, you can create a dropdown programmatically through JavaScript by first defining a __span__ element
							with an id and then passing it as a first argument to the dropdown constructor.
						

	
							<span id="myDropDownList">
							</span>
						



	
							var dropdown = new Telerik.UI.RadDropDownList(document.getElementById("myDropDownList"));
						



Defining __RadDropDownList__ without setting any properties will not result in a usable control. You need to at least specify 
              a __dataSource__ to have items in the drop down list to choose from. You can find how you can assign a 
              __dataSource__ and set other of __RadDropDownList__'s properties in the next section.
            

# optionsSetting RadDropDownList Options

Just like any other Windows Runtime JavaScript control, the RadDropDownList options can be defined through the __data-win-options__
							attribute.
						


 __html__
    


				<span id="markupDropDown" data-win-control="Telerik.UI.RadDropDownList" data-win-options="{
						dataSource: [
							{ Name: 'Mercedes', ID: 1 },
							{ Name: 'McLaren', ID: 2 },
							{ Name: 'Red Bull Racing', ID: 3 }
						],
						dataTextField: 'Name',
						dataValueField: 'ID'
						}"></span>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						


 __html__
    


				<span id="codeDropDown"></span>




 __js__
    


				    var dropDown = new Telerik.UI.RadDropDownList(document.getElementById("codeComboBox"), {
				        dataSource: [
							{ Name: 'Mercedes', ID: 1 },
							{ Name: 'McLaren', ID: 2 },
							{ Name: 'Red Bull Racing', ID: 3 }
				        ],
				        dataTextField: 'Name',
				        dataValueField: 'ID'
				    });



To see all available configuration options, go to T:Telerik.UI.RadDropDownList

Both of the examples above produce the same result. Here is an image of the control and its usage.
            ![dropdownlist-gettingstarted](../Media/Controls\DropDownList\dropdownlist-gettingstarted.png)

# accessAccessing and Modifying RadDropDownList

You can get hold of the RadDropDownList object the same way as the native WinJS components - find its DOM element and access its
							__winControl__ property.
						

	
							var dropdown = document.getElementById("myDropDown").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							dropdown.optionLabel = "Pick a name...";
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var dropdown = new Telerik.UI.RadDropDownList(document.getElementById("myDropDown"), {
								onopen: changeHandlerFnName });
							// OR
							var dropdown = new Telerik.UI.RadDropDownList(document.getElementById("myDropDown"), {
								onopen: function(e) {//...}
							});
						

>
								If you attach the event handler as shown above but in HTML mark-up you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							dropdown.addEventListener("open", changeHandlerFnName);
						



# selectionGetting and Setting a Selected Item

__RadDropDownList__ allows the user to choose an item from a dropdown list of predefined items.The __value__ property
              allows you to select an item from the predefined item list. You can also use the __value__ property to get the value of the selected item. 
              If there is no matching item value, the first item from the list is selected.
            

	
              var dropdown = document.getElementById("dropdown").winControl;

              var dropDownVal = dropdown.value;
              dropdown.value = dropDownVal;
            



Use the __text__ property to get the input string from the control. The __text__ property can also be used
              to select an item from the predefined list by its text. If there is no match, no item will be selected.
            

	
              var dropDownText = dropdown.text;
              dropdown.text = dropDownText;
            



To get or set the selected item's index you can use the __index__ property. Note that if the user does not select an
              item and types any text instead, the __index__ property will return *-1*.
              Once you have the selected item index, you can get the corresponding data entry through the __dataItem()__ method.
            

	
              dropdown.index = 0;
              var selectedItemIndex = dropdown.index;

              if (selectedItemIndex != -1) {
                item = dropdown.dataItem(selectedItemIndex);
              }
            



Additionally, you can set a selected item through the __select()__ method. It takes a "li" HTML element as an argument and selects 
              it from the list. The __list__ property returns a jQuery-wrapped list of the "li" elements in the control. You can 
              then use jQuery selectors to search for a given string value in the list. The following example shows how this can be done:
            

	
              var items = dropdown.list;
              var toSelect = $("li:contains('Andrew Fuller')",items);
              dropdown.select(toSelect);
            



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Templates]({{slug:templates}})

 * [Events]({{slug:events}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Create Cascading DropDownLists]({{slug:create-cascading-dropdownlists}})
