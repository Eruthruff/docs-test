---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


The __RadAutoCompleteBox__ control for Windows 8 is an HTML/JavaScript component that allows the user to select items from 
        predefined or live (service/ajax requested) data. To use the control, you must specify a datasource - you can use a 
        __Telerik.Data.DataSource__ control or even a simple JavaScript array.
			

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
							resources, as described here:
						

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creating-autocompleteCreating a RadAutoCompleteBox

To create a __RadAutoCompleteBox__ in the HTML markup, add an empty __span__ element with a 
              __data-win-control__ attribute with a value of __Telerik.UI.RadAutoCompleteBox__:
						

	
							<span data-win-control="Telerik.UI.RadAutoCompleteBox">
							</span>
						



Alternatively, you can create an autocompletebox programmatically through JavaScript by first defining a __span__ element
							with an id and then passing it as a first argument to the autocompletebox constructor:
						

	
							<span id="myAutoCompleteBox">
							</span>
						



	
							var autocomplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("myAutoCompleteBox"));
						



Creating a __RadAutoCompleteBox__ like that without setting any properties will not result in a very useful control. You 
              need to define at least a set of items the __RadAutoCompleteBox__ can search from. In the next section you can see a 
              basic usage of the control.
            

# optionsSetting RadAutoCompleteBox Options

Just like any other Windows Runtime JavaScript control, the __RadAutoCompleteBox__ options can be defined through the 
              __data-win-options__ attribute:
						


 __html__
    


	            <span data-win-control="Telerik.UI.RadAutoCompleteBox" data-win-options="{
	                    placeholder: 'enter country...',
	                    dataSource: [ 'Germany', 'England', 'France', 'Greece'],
	                    filter: 'startswith'
	                }"></span>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
						


 __html__
    


				<span id="autoComplete"></span>




 __js__
    


				    var autoComplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("autoComplete"), {
				        placeholder: 'enter country...',
				        dataSource: ['Germany', 'England', 'France', 'Greece'],
				        filter: 'startswith'
				    });



Both of the above examples produce the same result. Here is an image that depicts the control and its usage.
            ![autocomplete-gettingstarted](../Media/Controls\AutoCompleteBox\autocomplete-gettingstarted.png)

# accessingAccessing and Modifying RadAutoCompleteBox

You can get hold of the __RadAutoCompleteBox__ object the same way as the native WinJS components - find its DOM element and access its
							__winControl__ property.
						

	
							var autocomplete = document.getElementById("myAutoCompleteBox").winControl;
						



Once you have a reference to the control, you can modify its properties as required:

	
							autocomplete.separator = ",";
						



# eventsAttaching Events

You can either declare an event handler in the options object that you pass to the control during initialization, or you can use the
							__addEventListener__ method to attach a function for execution upon a certain event. Below you can see samples of both
							approaches:
						

	
							var autocomplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("myAutoCompleteBox"), { 
								onchange: changeHandlerFnName });
							// OR
							var autocomplete = new Telerik.UI.RadAutoCompleteBox(document.getElementById("myAutoCompleteBox"), {
								onchange: function(e) {//...}
							});
						

>
								If you attach the event handler as shown above, in HTML mark-up, you would need to mark the handler function as safe
								in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
							

	
							autocomplete.addEventListener("change", changeHandlerFnName);
						



# valueGetting and Setting a Value

__RadAutoCompleteBox__ allows the user to input any text. Because of the nature of the control, the 
              __value__ and the __text__ properties are identical in their functionality. You can use both 
              to get or set the input text:
            

	
              var autoComplete = document.getElementById("autoComplete").winControl;

              var autoCompleteVal = autoComplete.value;
              autoComplete.value = autoCompleteVal;

              var autoCompleteText = autoComplete.text;
              autoComplete.text = autoCompleteText;
            



To populate the __RadAutoCompleteBox__ with one of the predefined data items you can use the __select()__ method. 
              It takes a "li" HTML element as an argument and selects it from the list. The __list__ property returns a jQuery-wrapped list of the 
              "li" elements in the control. You can then use jQuery selectors to search for a given string value in the list. The following example shows how this 
              can be done:
            

	
              var items = autoComplete.list;
              var toSelect = $("li:contains('Andrew Fuller')",items);
              autoComplete.select(toSelect);
            



# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Templates]({{slug:templates}})

 * [Events]({{slug:events}})

 * [Basic HTML Output and CSS Classes]({{slug:basic-html-output-and-css-classes}})

 * [Filter ListView with RadAutoCompleteBox]({{slug:filter-listview-with-radautocompletebox}})

 * [Highlight Matching Text in Suggestions]({{slug:highlight-matching-text-in-suggestions}})
