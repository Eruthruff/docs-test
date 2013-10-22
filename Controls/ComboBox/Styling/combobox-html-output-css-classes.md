---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of __RadComboBox__ in basic scenarios (some HTML attributes have 
        been removed for simplicity).
      

# Basic Output

Below you can see the basic HTML output of the __RadComboBox__ and descriptions of its elements.
        


 __html__
    


		    <span class="t-list win-interactive">
		        <span class="k-widget k-combobox k-header">
			        <span class="k-dropdown-wrap k-state-default">
				        <input class="k-input" placeholder="Default Placeholder">
				        <span class="k-select">
					        <span class="k-icon k-i-arrow-s">select</span>
				        </span>
			        </span>
	                <input style="display: none" />
		        </span>
	        </span>



Class/selector name

Description

__.t-list__

The __RadComboBox__ wrapper element. This is the element that is
                passed in the control's constructor.
              

__.k-combobox__

The wrapper of the combobox widget. It wraps the search input box, the dropdown list arrow and the selected value's input box, which is 
                hidden.
              

__.k-combobox .k-dropdown-wrap__

Wraps only the search input box and the dropdown list arrow.
              

__.k-combobox .k-dropdown-wrap .k-input__

The search input text box element of the widget.
              

__.k-combobox .k-dropdown-wrap .k-select__

The dropdown list arrow container.
              

__.k-combobox .k-dropdown-wrap .k-i-arrow-s__

The actual dropdown list arrow symbol.
              

# Additional states of the control

These CSS classes are added to the __.k-dropdown-wrap__ in different scenarios (when the widget is focused, hovered, disabled, etc.).
        

Class/selector name

Description

__.k-combobox .k-dropdown-wrap.k-state-hover__

This class is added to the widget when the mouse hovers over the __RadComboBox__.
              

__.k-combobox .k-dropdown-wrap.k-state-focused__

This class is added to the widget when the __RadComboBox__ is focused.
              

__.k-combobox .k-dropdown-wrap.k-state-disabled__

This class is added to the widget when the widget is disabled. That is when the __enabled__ property is set to
                *false*.
              

__.k-combobox .k-dropdown-wrap.k-state-border-down__

This class is added to the widget when the popup is opened below the input text box.
              

__.k-combobox .k-dropdown-wrap.k-state-border-up__

This class is added to the widget when the popup is opened above the input text box.
              

__.k-combobox .k-dropdown-wrap.k-state-active__

This class is added to the widget when the popup is opened, no matter if above or below the input text box.
              

# List Container Output

Below you can see the basic HTML output of the dropdown list container of the __RadComboBox__ and descriptions of its elements.
        


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
