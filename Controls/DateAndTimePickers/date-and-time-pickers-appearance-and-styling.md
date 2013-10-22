---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This help article describes the rendering of the __RadDatePicker__ and __RadTimePicker__
        controls and the associated CSS classes with each element. Additionally, an overview of the composition
        of the built-in skins' CSS rules is given to aid custom styling.
      

Both controls have *identical rendering* and their
        *
          CSS classes differ
          at the picker and the selector containers
        *.
      


 __html__
    


	        <div class="t-date-picker">
	            <div class="t-picker">
	                <div class="t-input"></div>
	                <div class="t-arrow"></div>
	            </div>
	        </div>
	        <div class="t-date-selector">
	            <div class="t-header"></div>
	            <div class="t-body"></div>
	            <div class="t-footer">
	                <button class="t-cancel"></button>
	                <button class="t-ok"></button>
	            </div>
	        </div>




 __html__
    


	        <div class="t-time-picker">
	            <div class="t-picker">
	                <div class="t-input"></div>
	                <div class="t-arrow"></div>
	            </div>
	        </div>
	        <div class="t-time-selector">
	            <div class="t-header"></div>
	            <div class="t-body"></div>
	            <div class="t-footer">
	                <button class="t-cancel"></button>
	                <button class="t-ok"></button>
	            </div>
	        </div>



# Section1Structure selectors

Both controls' elements are targeted in a similar way in the built-in skins. Below you can find CSS selector examples with 
          __RadDatePicker__, but you can easily modify the selectors for __RadTimePicker__ 
          by replacing "date" with "time":
        

Class/selector name

Description

__.t-date-picker__

The picker container of the control.
              

__.t-date-selector__

The selector container of the control.
              

__.t-date-picker .t-{child-name}__

The CSS selector to access child elements of the picker container. Replace ".t-{child-name}" with the desired element's class name 
                (i.e. "t-picker", "t-input", "t-arrow")
              

__.t-date-selector .t-{child-name}__

The CSS selector to access child elements of the selector container. Replace ".t-{child-name}" with the desired element's class name 
                (i.e. "t-header", "t-body", "t-footer").
              

State Selectors

Description

__.t-date-picker .t-picker:hover__

The CSS selector for the state when the mouse hovers over the picker container.
              

__.t-date-picker .t-picker.t-focused__

The CSS selector for the state when the picker container is focused.
              

__.t-date-picker.t-disabled__

The CSS selector for the state when the control is disabled.
              

__.t-date-picker.t-empty__

The CSS selector for the state when the input box is empty.
              

# Related Topics
