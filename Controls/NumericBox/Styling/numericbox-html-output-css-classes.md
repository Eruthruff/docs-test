---
title: Basic HTML Output and CSS Classes
meta_title: Basic HTML Output and CSS Classes
meta_description: description.
slug: 
tags:basic,html,output,and,css,classes
publish:True
---


This article will show and explain the HTML output and CSS classes of __RadNumericBox__ in basic scenarios 
        (some HTML attributes have been removed for simplicity).
      

# Section1Basic Output

Below you can see the basic HTML output of the __RadNumericBox__ and descriptions of its elements.
        


 __html__
    


		    <span class="t-numericbox win-interactive">
		        <span class="k-widget k-numerictextbox">
			        <span class="k-numeric-wrap k-state-default">
				        <input class="k-input" type="text"/>
				        <span class="k-select">
					        <span class="k-link">
						        <span class="k-icon k-i-arrow-n">Increase value</span>
					        </span>
					        <span class="k-link">
						        <span class="k-icon k-i-arrow-s">Decrease value</span>
					        </span>
				        </span>
			        </span>
		        </span>
	        </span>



Class/selector name

Description

__.t-numerictextbox__

The __RadNumericBox__ wrapper element. This is the element that is
                passed in the control's constructor.
              

__.k-numerictextbox .k-numeric-wrap__

The wrapper of the numeric box widget.
              

__.k-numerictextbox .k-numeric-wrap .k-input__

The input element of the widget.
              

__.k-numerictextbox .k-numeric-wrap .k-select__

The container of the selection arrows containers.
              

__.k-numerictextbox .k-numeric-wrap .k-select .k-link__

The selection arrows containers.
              

__.k-numerictextbox .k-numeric-wrap .k-select .k-link .k-icon__

The actual selection arrows.
              

__.k-numerictextbox .k-numeric-wrap .k-select .k-link .k-icon.k-i-arrow-n__

The "increase value" selection arrow.
              

__.k-numerictextbox .k-numeric-wrap .k-select .k-link .k-icon.k-i-arrow-s__

The "decrease value" selection arrow.
              

# Additional States of the Control

These CSS classes are added to the __.k-numeric-wrap__ in different scenarios 
          (when the widget is focused, hovered or disabled).
        

Class/selector name

Description

__.k-numerictextbox .k-numeric-wrap.k-state-hover__

This class is added to the widget when the mouse hovers over the __RadNumericBox__.
              

__.k-numerictextbox .k-numeric-wrap.k-state-focused__

This class is added to the widget when the __RadNumericBox__ is focused.
              

__.k-numerictextbox .k-numeric-wrap.k-state-disabled__

This class is added to the widget when the control is disabled. That is when the __enabled__ property is set to
                *false*.
              

# Related Topics
