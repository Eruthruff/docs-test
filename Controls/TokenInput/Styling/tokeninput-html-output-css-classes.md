---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of __RadTokenInput__ in basic scenarios 
        (some HTML attributes have been removed for simplicity).
      

# Basic Output

Below you can see the basic HTML output of the __RadTokenInput__ and descriptions of its elements.
        


 __html__
    


		    <span class="t-list win-interactive">
		        <div class="k-widget k-multiselect k-header">
			        <div class="k-multiselect-wrap k-floatwrap">
				        <ul class="k-reset"></ul>
				        <input class="k-input">
				        <span class="k-icon k-loading k-loading-hidden"></span>
			        </div>
	                <select style="display: none">
	                    <option>Option 1</option>
	                    <option>Option 2</option>
	                </select>
		        </div>
	        </span>



Class/selector name

Description

__.t-list__

The __RadTokenInput__ wrapper element. This is the element that is
                passed in the control's constructor.
              

__.k-multiselect__

The wrapper of the token input elements and the hidden *select* element, which holds the selected value.
              

__.k-multiselect .k-multiselect-wrap__

The wrapper of the token input elements - the input text box and the drop down list arrow.
              

__.k-multiselect-wrap ul__

The list container in which the token boxes are added.
              

__.k-multiselect-wrap .k-input__

The input text box of the token input.
              

__.k-multiselect-wrap .k-loading__

The loading indicator of the token input.
              

# Additional States

These CSS classes are added to the __.k-multiselect__ in different scenarios
          (when the widget is focused, hovered, disabled, etc.).
        

Class/selector name

Description

__.k-state-hover.k-multiselect__

This class is added to the __.k-multiselect__ when the mouse hovers over the __RadTokenInput__.
              

__.k-state-focused.k-multiselect__

This class is added to the __.k-multiselect__ when the __RadTokenInput__ is focused.
              

__.k-state-disabled.k-multiselect__

This class is added when the __RadTokenInput__ is disabled. That is when the __enabled__ 
                property is set to *false*.
              

__.k-state-border-down.k-multiselect__

This class is added to the __.k-multiselect__ when the popup is opened below the text box.
              

__.k-state-border-up.k-multiselect__

This class is added to the __.k-multiselect__ when the popup is opened above the text box.
              

# TokenInput Items

When an item from the drop down list is selected, it populates the __.k-multiselect-wrap ul__ element. 
          Below you can see the HTML output of the box items, that are in the selected list.
        


 __html__
    


		    <li class="k-button">
		        <span>Item</span>
		        <span class="k-icon k-delete">delete</span>
	        </li>



Class/selector name

Description

__.k-multiselect-wrap .k-button__

The box item in the selected list.
              >
                  One additional CSS class is added to the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-button</legacyBold> when the mose hovers over the box item - 
                  <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-state-hover</legacyBold>.
                

__.k-multiselect-wrap .k-delete__

The delete icon of the box item.
              

# List Container Output

Below you can see the basic HTML output of the dropdown list container of the __RadTokenInput__ and descriptions of its elements.
        


 __html__
    


		    <div class="k-animation-container">
		        <div class="k-list-container k-popup k-group k-reset">
			        <ul class="k-list k-reset">
				        <li class="k-item">Suggestion 1</li>
				        <li class="k-item">Suggestion 2</li>
			        </ul>
		        </div>
	        </div>



Class/selector name

Description

__.k-animation-container__

The element that wraps the list popup when it is animated.
              

__.k-list-container.k-popup__

The wrapper element of the popup.
              >
                  Two additional CSS classes are added to the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-popup</legacyBold>.
                

* 

__.k-state-border-down__ - This class is added to the widget when the popup is opened below the input box.
                    

* 

__.k-state-border-up__ - This class is added to the widget when the popup is opened above the input box.
                    

__.k-popup .k-list__

The list container with the results.
              

__.k-popup .k-list .k-item__

A single item from the results.
              

# Additional States of the items

These CSS classes are added to the __.k-item__ element in different scenarios (when it is focused or hovered).
        

Class/selector name

Description

__.k-popup .k-state-hover.k-item__

This class is added to the list item when the mouse hovers over it.
              

__.k-popup .k-state-focused.k-item__

This class is added to the list item when it is focused.
              

# Related Topics
