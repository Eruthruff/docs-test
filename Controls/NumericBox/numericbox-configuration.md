---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This article lists the options for customizing RadNumericBox and provides some examples of common scenarios involving the control.

# Culture

You can set the culture locally for the control. The __culture__ property takes any valid [BCP-47](http://tools.ietf.org/html/bcp47) language tag as a 
          value. The floating point sign, the currency sign and other display preferences depend on the __culture__
          property. For more information regarding Telerik culture support you
          can visit this article: [Culture Support](d3c7ea15-4986-48fe-9cc7-db2f1c03a57f).
        


 __html__
    


				<span id="NumericBoxFR" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
	                    culture: 'fr-FR',
						format: 'c2',
				}"></span>

![numericbox-culture](../Media/Controls\NumericBox\numericbox-culture.png)

# Formatting

You can use the __format__ property to provide a format string for the values displayed inside the RadNumericBox. Check the
					[Formatting](0c3b0ea5-3850-4c90-86b3-5d20f2a18c1e) article for detailed descriptions of the different options for formatting
					the control's value.
				


 __html__
    


				<span id="NumericBoxFR" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
	                    culture: 'fr-FR',
						format: 'c2',
				}"></span>

![numericbox-formatting](../Media/Controls\NumericBox\numericbox-formatting.png)

# Precision

To modify the precision of the control, use the __decimals__ property. It sets the number of digits shown after the decimal separator. 
					If it is not set, it will use the default precision defined by the current culture. Make sure the number format allows displaying the 
					desired precision in view mode of the numeric box.
				


 __html__
    


				<span id="numericBox2" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
						decimals: 3,
						format: '0.000'
				}"></span>



# Min and Max Value

Using the __min__ and/or __max__ options, you can produce a range of allowed values for the control.
					If the user tries to enter a value outside of the provided range, it will be reset to the closest allowed. *For example:* if the
					__min__ property is set to 3, and the user enters 0, the value of the numeric box will be automatically corrected to 3.
				

Furthermore, if you try to set a value outside of the allowed range of the control manually through the __value__ property, it will not
					be set. Also, no auto-correction will be performed in such case—the current value (even if empty) will be preserved. The code sample below shows how to set 
					a min value of 0 and max value of 255.
				


 __html__
    


				<span id="numericBox3" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
						min: 0,
						max: 255,
						placeholder: '(0 to 255)'
					}"></span>



# Increment/decrement Step

You can use the __step__ option to control at what step the value will change when pressing the increase/decrease buttons or using the mousewheel or 
          the swipe command. The sample below demonstrates changing the step to 0.1. 
				


 __html__
    


				<span id="numericBox4" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
						min: 0,
						max: 1,
						step: 0.1
				}"></span>



# Swipe

By default, when you swipe away from the input box, the numeric value increments/decrements depending on the direction, the distance and the increment/decrement step,
          set by the __step__ and __sensitivity__ properties. To disable the swipe command on the RadNumericBox, you must set the 
          __swipe__ property value to *false*.
        


 __html__
    


				<span id="numericBox5" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
	                    swipe: false
				}"></span>



# Swipe Sensitivity

To set how far you have to swipe (in px) before the numeric value increments/decrements by a step, use the __sensitivity__ property. 
          Please note, that the __sensitivity__ property has an effect only if the __swipe__ property is set to  
          *true*.
        


 __html__
    


				<span id="numericBox6" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
	                    step: 0.01,
	                    sensitivity: 50
				}"></span>



# Mouse Wheel

By default, the mouse wheel can be used to "scroll" through numeric values in steps, set by the __step__ property. In order to disable the mouse wheel 
          option, you must set the __wheel__ property value to *false*.
        


 __html__
    


				<span id="numericBox7" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
	                    wheel: false
				}"></span>



# Showing Empty Text

To display text that prompts the user about the expected value in RadNumericBox when there is no value set, use the __placeholder__
					property. The code sample below show how to use the __placehoder__ property to ask the user to enter their age.
				


 __html__
    


				<span id="numericBox8" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
						placeholder: 'Enter your age'
				}"></span>

![numericbox-placeholder](../Media/Controls\NumericBox\numericbox-placeholder.png)

# Tooltips

By default, when you hover over the increment and decrement buttons, tooltips are displayed, saying "Increase value" and "Decrease value". If you want to modify the
					text shown by the tooltips, set the __incrementTooltip__ and __decrementTooltip__ properties to the desired string values.
				


 __html__
    


				<span id="numericBox9" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
						incrementTooltip: '+1',
						decrementTooltip: '-1',
						step:1,
						value: 20,
						format: 'n0'
				}"></span>

![numericbox-tooltip](../Media/Controls\NumericBox\numericbox-tooltip.png)

# Disabling the Control

To prevent user interaction with the control at one point and allow it later, you can set the __enabled__ property value to
					true or false. When set to false, the buttons and input box become inactive.
				


 __html__
    


				<span id="numericBox10" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
						enabled: false
				}"></span>



# Related Topics
