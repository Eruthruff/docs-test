---
title: Input Free Text with RadTokenInput
meta_title: Input Free Text with RadTokenInput
meta_description: description.
slug: 
tags:input,free,text,with,radtokeninput
publish:True
---


By default __RadTokenInput__ allows the user to search and select only from a list of predefined items.
        The following example shows how this behavior can be changed, so that the user can type and select free text while still be able
        to choose from the available items.
      

# Section1

* 

*Define a simple __RadTokenInput__ in the markup*. You need only the 
              data properties to be set - __dataSource__, __dataValueField__ and 
              __dataTextField__.
            


 __html__
    


				<span id="tokenInput" data-win-control="Telerik.UI.RadTokenInput" data-win-options="{
	                dataSource: {
	                    data: Tokens.SampleData
	                },
	                dataValueField: 'id',
	                dataTextField: 'text'
	            }"></span>



Below is a code sample of the sample data array and how it has been called from a namespace, so it can be used in the 
              markup definition of __RadTokenInput__. Also, the variable that will hold the control's object is 
              declared here.
            


 __js__
    


		var tokenInput,
	        sampleData = [
	        { id: 1, text: "New York" },
	        { id: 2, text: "Philadelphia" },
	        { id: 3, text: "Boston" }
	        ];
	
		WinJS.Namespace.define("Tokens", {
		    SampleData: sampleData
		});



* 

*
                Access the __RadTokenInput__ object and its input element.
              *
              Get __RadTokenInput__ instance and assign it to the already declared variable. Get the control's text input
              element by its class and add a "mousedown" event handler to it.
              This has to be done in the __ready()__ function when you are using single page navigation or in the 
              promise returned by the __processAll()__ function when building a blank application. This is 
              necessary, because in order to get elements or controls from the DOM, they have to be loaded or initialized there first.
            


 __js__
    


				    tokenInput = Telerik.UI.find.TokenInput("#tokenInput");
	
				    var tokenInputField = document.querySelector("#tokenInput .k-input");
				    tokenInputField.addEventListener("keydown", tokenKeyDownHandler);



* 

*Create the text input's "keydown" event handler*. The code sample below represents the following 
              logic.
            

* 

Check if the key that has been pressed is the Enter key.

* 

If the above is true, check if there is text written in the text input box.

* 

If there is a text in the input field, create a new object with the text and unique value and add it to
                  the control's __dataSource__.
                

* 

Finally, select the newly added item via the __select()__ method.
                

The control still handles the case when the input text matches a predefined item, so you don't need to handle it yourself.
            


 __js__
    


		function tokenKeyDownHandler(e) {
		    var enterKey = 13;
		    if (e.keyCode == enterKey) {
		        var text = e.target.value;
	
		        if (text) {
		            var data = tokenInput.dataSource.data;
	
		            var value = data[data.length - 1].id + 1;
		            var item = {
		                id: value,
		                text: text
		            };
		            tokenInput.dataSource.add(item);
	
		            var items = tokenInput.list;
		            var toSelect = $("li:contains('" + text + "')", items);
		            tokenInput.select(toSelect);
		        }
		    }
		}



*Alternatively, you can use __RadTokenInput's value__ property to select the values programmatically.*
              To visually refresh the control's selection, you need to assign the __value__ property an array of values.
              You need to copy all previously selected items, add the new item and assign the resulting array to the
              __value__ property.
            

Furthermore, when the user types something in the text input of the control, the __dataSource__ is
              automatically filtered. When they input a completely new text that is not to be found in the predefined items, the
              __dataSource__ is empty. Therefore, you must clear the __dataSource.filter__ 
              property before the new item is added, so that the previously selected items can be selected again. 
              Below is a code snippet for the second alternative.
            


 __js__
    


		function tokenKeyDownHandlerValue(e) {
		    var enterKey = 13;
		    if (e.keyCode == enterKey) {
		        var text = e.target.value;
	
		        if (text) {
		            var data = tokenInput.dataSource.data;
	
		            var value = data[data.length - 1].id + 1;
		            var item = {
		                id: value,
		                text: text
		            };
		            tokenInput.dataSource.filter = null;
		            tokenInput.dataSource.add(item);
	
		            var tokenValue = [];
		            for (var i = 0; i < tokenInput.value.length; i++) {
		                tokenValue[i] = tokenInput.value[i];
		            }
	
		            tokenValue.push(item.id);
		            tokenInput.value = tokenValue;
		        }
		    }
		}



With this functionality __RadTokenInput__ behaves just like __RadComboBox__ with 
          multiple selected items. The difference between the two is that the tokens can be unselected by the user with the 
          __RadTokenInput__ control.
        

This implementation is part of our
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link:
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *TokenInput/SelectFreeTextWithTokenInput*.
        

# Related Topics

 * [Events]({{slug:events}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})
