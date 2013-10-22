---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of __RadDropDownList__ in basic scenarios 
        (some HTML attributes have been removed for simplicity).
      

# Basic Output

Below you can see the basic HTML output of the __RadDropDownList__ and descriptions of its elements.
        


 __html__
    


		    <span class="t-list win-interactive">
		        <span class="k-widget k-dropdown k-header">
			        <span class="k-dropdown-wrap k-state-default">
				        <span class="k-input">Default optionLabel</span>
				        <span class="k-select">
					        <span class="k-icon k-i-arrow-s">select</span>
				        </span>
			        </span>
		        </span>
	        </span>



Class/selector name

Description

__.t-list__

The __RadDropDownList__ wrapper element. This is the element that is
                passed in the control's constructor.
              

__.k-dropdown__

The wrapper of the drop down widget and the hidden selected value's input box.
              >
                  Two additional CSS classes are added to the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-dropdown</legacyBold>.
                

* 

__.k-state-border-down__ - This class is added to the widget when the popup is opened below the input box.
                    

* 

__.k-state-border-up__ - This class is added to the widget when the popup is opened above the input box.
                    

__.k-dropdown .k-dropdown-wrap__

The wrapper of the drop down widget.
              

__.k-dropdown .k-dropdown-wrap .k-input__

The text element of the widget.
              

__.k-dropdown .k-dropdown-wrap .k-select__

The drop down arrow container.
              

__.k-dropdown .k-dropdown-wrap .k-i-arrow-s__

The actual drop down arrow symbol.
              

# Additional states of the control

These CSS classes are added to the __.k-dropdown-wrap__ in different scenarios 
          (when the widget is focused, hovered, disabled, etc.).
        

Class/selector name

Description

__.k-dropdown .k-dropdown-wrap.k-state-hover__

This class is added to the widget when the mouse hovers over the __RadDropDownList__.
              

__.k-dropdown .k-dropdown-wrap.k-state-focused__

This class is added to the widget when the __RadDropDownList__ is focused.
              

__.k-dropdown .k-dropdown-wrap.k-state-disabled__

This class is added to the widget when the widget is disabled. That is when the __enabled__ property is set to
                *false*.
              

__.k-dropdown .k-dropdown-wrap.k-state-border-down__

This class is added to the widget when the popup is opened below the text box.
              

__.k-dropdown .k-dropdown-wrap.k-state-border-up__

This class is added to the widget when the popup is opened above the text box.
              

__.k-dropdown .k-dropdown-wrap.k-state-active__

This class is added to the widget when the popup is opened, no matter if above or below the input text box.
              

# List Container Output

Below you can see the basic HTML output of the dropdown list container of the __RadDropDownList__ and descriptions of its elements.
        


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

__.k-animation-container.km-popup__

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

These CSS classes are added to the __.k-item__ element in different scenarios (when it is focused, hovered or selected).
        

Class/selector name

Description

__.k-popup .k-state-hover.k-item__

This class is added to the list item when the mouse hovers over it.
              

__.k-popup .k-state-focused.k-item__

This class is added to the list item when it is focused.
              

__.k-popup .k-state-selected.k-item__

This class is added to the list item when it is selected from the dropdown.
              

# Related Topics
