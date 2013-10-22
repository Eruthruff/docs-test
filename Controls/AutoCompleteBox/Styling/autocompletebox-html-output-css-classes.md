---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of __RadAutoCompleteBox__ in basic scenarios 
        (some HTML attributes have been removed for simplicity).
      

# Basic Output

Below you can see the basic HTML output of the __RadAutoCompleteBox__ and descriptions of its elements.
        


 __html__
    


		    <span class="t-list win-interactive">
		        <span class="k-widget k-autocomplete k-header k-state-default">
			        <input class="k-input" placeholder="Default Placeholder">
			        <span class="k-icon k-loading" style="display: none;"></span>
		        </span>
	        </span>



Class/selector name

Description

__.t-list__

The __RadAutoCompleteBox__ wrapper element. This is the element that is 
                passed in the control's constructor.
              

__.k-autocomplete__

The wrapper of the autocomplete widget. For different widget states - see the next section.
              

__.k-autocomplete .k-input__

The text element of the widget.
              >
                  One additional CSS class is added to the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.k-input</legacyBold>. When the user starts typing text and the placeholder is removed, the 
                  <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">.t-typed-text</legacyBold> class is added.
                

__.k-autocomplete .k-loading__

Loading indicator of the widget.
              

# Additional states of the control

These CSS classes are added to the __.k-autocomplete__ widget in different scenarios (when the widget is focused, hovered, disabled, etc.).
        

Class/selector name

Description

__.k-autocomplete.k-state-hover__

This class is added to the widget when the mouse is over the autocomplete widget.
              

__.k-autocomplete.k-state-focused__

This class is added to the widget when it is focused.
              

__.k-autocomplete.k-state-disabled__

This class is added to the widget when the widget is disabled. That is when the __enabled__ property is set to 
                *false*.
              

__.k-autocomplete.k-state-border-down__

This class is added to the widget when the popup is opened below the input box.
              

__.k-autocomplete.k-state-border-up__

This class is added to the widget when the popup is opened above the input box.
              

# List Container Output

Below you can see the basic HTML output of the dropdown list container of the __RadAutoCompleteBox__ and descriptions of its elements.
        


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

These CSS classes are added to the __.k-item__ element in different scenarios (when the widget is focused or hovered).
        

Class/selector name

Description

__.k-popup .k-state-hover.k-item__

This class is added to the list item when the mouse hovers over it.
              

__.k-popup .k-state-focused.k-item__

This class is added to the list item when it is focused.
              

# Related Topics
