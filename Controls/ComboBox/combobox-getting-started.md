---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The RadComboBox control for Windows 8 is an HTML/JavaScript component that allows the user to select one item from predefined or live (xhr requested) data.
				To use the control, you must specify a datasource. You can use a __Telerik.Data.DataSource__ component or even a simple JavaScript array.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadComboBox

To create a RadComboBox in the HTML markup, add an empty __span__ element with a __data-win-control__ 
							attribute with a value of __Telerik.UI.RadComboBox__:
						

	
							<span data-win-control="Telerik.UI.RadComboBox">
							</span>
						



Alternatively, you can create a RadComboBox programmatically through JavaScript by first defining a __span__ element
							with an id and then passing it as a first argument to the RadComboBox constructor:
						

	
							<span id="myComboBox">
							</span>
						



	
							var combobox = new Telerik.UI.RadComboBox(document.getElementById("myComboBox"));
						



Defining __RadComboBox __ without any properties set will not render a usable control. Without data to search 
              from __RadComboBox__ cannot serve its purpose. Therefore, you need to at least specify a __dataSource__. The rest of
              __RadComboBox__'s properties will be set to their default values. You can see a basic example of defining a usable
              __RadComboBox__ in the next step.
            

# optionsSetting RadComboBox Options

Just like any other Windows Runtime JavaScript control, the RadComboBox options can be defined through the __data-win-options__
							attribute:
						


 __html__
    


				<span id="markupComboBox" data-win-control="Telerik.UI.RadComboBox" data-win-options="{
						dataSource: [
							{ Name: 'Mercedes', ID: 1 },
							{ Name: 'McLaren', ID: 2 },
							{ Name: 'Red Bull Racing', ID: 3 }
						],
	                    placeholder: 'Choose a team...',
	                    filter: 'startswith',
						dataTextField: 'Name',
						dataValueField: 'ID'
						}"></span>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						


 __html__
    


				<span id="codeComboBox"></span>




 __js__
    


				    var comboBox = new Telerik.UI.RadComboBox(document.getElementById("codeComboBox"), {
				        dataSource: [
							{ Name: 'Mercedes', ID: 1 },
							{ Name: 'McLaren', ID: 2 },
							{ Name: 'Red Bull Racing', ID: 3 }
				        ],
				        placeholder: 'Choose a team...',
	                    filter: 'startswith',
				        dataTextField: 'Name',
				        dataValueField: 'ID'
				    });



To see all available configuration options, go to the API reference for T:Telerik.UI.RadComboBox

Both of the above examples produce the same result. Below you can see an image of the control and its usage.
            ![combobox-gettingstarted](../Media/Controls\ComboBox\combobox-gettingstarted.png)

# accessAccessing and Modifying RadComboBox

You can get a reference to the RadComboBox object the same way as the native WinJS components - find its DOM element and access its
							__winControl__ property.
						

	
							var combobox = document.getElementById("myComboBox").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							combobox.autoSuggest = true;
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see examples of both
							approaches:
						

	
							var combobox = new Telerik.UI.RadComboBox(document.getElementById("myComboBox"), {
							onchange: changeHandlerFnName });
							// OR
							var combobox = new Telerik.UI.RadComboBox(document.getElementById("myComboBox"), {
							onchange: function(e) {//...}
							});
						

>
								Note that if you attach the event handler using the on[<legacyItalic xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">eventname</legacyItalic>] property, but in HTML mark-up, you would need 
								to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							combobox.addEventListener("change", changeHandlerFnName);
						



# valueGetting and Setting a Value

__RadComboBox__ allows the user to select an item from a dropdown list or to input any text. The __value__ property 
              allows you to select an item from the predefined item list. You can also use the __value__ property to get the value of the selected item.  
            

	
              var comboBox = document.getElementById("comboBox").winControl;

              var comboBoxVal = comboBox.value;
              comboBox.value = comboBoxVal;
            



Note that when you set a __value__ to the __RadComboBox__, if it matches a value of a predefined item, 
              the text in the input field will be updated with the item's text. If there is no match, the input box will still be populated with the value you set.
            

Use the __text__ property to get the input string from the control. The __text__ property can also be used 
              to select an item from the predefined list by its text. If there is no match, the input box will still be populated with the text you set.
            

	
              var comboBoxText = comboBox.text;
              comboBox.text = comboBoxText;
            



The __index__ property gets or sets the selected item through its index in the item list. Note that if the user does not select an
              item and types any text instead, the __index__ property will return *-1*. Once you have the selected item
              index, you can get the corresponding data entry through the __dataItem()__ method.
            

	
              comboBox.index = 0;
              var selectedItemIndex = comboBox.index;

              if (selectedItemIndex != -1) {
                item = comboBox.dataItem(selectedItemIndex);
              }
            



You can also use the __select()__ method to set a selected item. It takes a "li" HTML element as an argument and selects it from the list. 
              The __list__ property returns a jQuery-wrapped list of the "li" elements in the control. You can then use jQuery selectors to 
              search for a given string value in the list. The following example shows how this can be done:
            

	
              var items = comboBox.list;
              var toSelect = $("li:contains('Andrew Fuller')",items);
              comboBox.select(toSelect);
            



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Templates]({{slug:templates}})

 * [Events]({{slug:events}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Create Cascading ComboBox]({{slug:create-cascading-combobox}})
