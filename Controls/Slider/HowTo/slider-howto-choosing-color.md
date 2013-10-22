---
title: Choose a Color with RGB Sliders
meta_title: Choose a Color with RGB Sliders
meta_description: description.
slug: 
tags:choose,a,color,with,rgb,sliders
publish:True
---


This article will provide a simple implementation of a standard scenario using __RadSlider__ for user input.
        In the current example there are three sliders with available selection from 0 to 255 representing the three main colors of the
        RGB palette and their values. Sliding the drag handle or tapping on the scale on each of the three sliders immediately changes 
        the sample color on the right side. You can find a detailed explanation on how this can be achieved below.
      

# Markup

* 

*Declare three __RadSlider__ controls*. They should be indentical except for their ids.
              You can configure the following properties to suit the needs of the scenario.
            

* 

Set the __min__ and __max__ property values to *0* and
                  *255* respectively to match the RGB color values.
                

* 

The __orientation__ property value to *"vertical"* to force the control 
                  to render vertically.
                

* 

The __largeStep__ property value to *50* for a better visual appearance.
                

* 

The __smallStep__ property value to *5*, as this will be the step for the
                  color values. A lower value of the __smallStep__ property means a smoother transition between colors 
                  when the user drags the slide handle.
                

Here is the markup code sample for the three controls.
            


 __html__
    


	            <div id="sliderRed-container">
	                <p>Red</p>
	                <div id="sliderRed" data-win-control="Telerik.UI.RadSlider" data-win-options="{
	                        min: 0,
	                        max: 255,
	                        orientation: 'vertical',
	                        smallStep: 5,
	                        largeStep: 50,
	                        onslide: RGBSlider.ChangeSlideHandler,
	                        onchange: RGBSlider.ChangeSlideHandler
	                    }"></div>
	            </div>
	            <div id="sliderGreen-container">
	                <p>Green</p>
	                <div id="sliderGreen" data-win-control="Telerik.UI.RadSlider" data-win-options="{
	                        min: 0,
	                        max: 255,
	                        orientation: 'vertical',
	                        smallStep: 5,
	                        largeStep: 50,
	                        onslide: RGBSlider.ChangeSlideHandler,
	                        onchange: RGBSlider.ChangeSlideHandler
	                    }"></div>
	            </div>
	            <div id="sliderBlue-container">
	                <p>Blue</p>
	                <div id="sliderBlue" data-win-control="Telerik.UI.RadSlider" data-win-options="{
	                        min: 0,
	                        max: 255,
	                        orientation: 'vertical',
	                        smallStep: 5,
	                        largeStep: 50,
	                        onslide: RGBSlider.ChangeSlideHandler,
	                        onchange: RGBSlider.ChangeSlideHandler
	                    }"></div>
	            </div>



There are also __change__ and __slide__ event handlers added to all three
              __RadSliders__. The difference between the two events is that the __change__ event
              fires after the dragging action is complete or when the user taps on the slider scale, while the __slide__
              event fires during the dragging action. It is advisable to handle both events, because the user can choose to either drag the
              slider or tap on the scale. The handler is the same, because the events are very similar and it does the same thing for all
              three controls. You can see the event handler code in the section below.
            

* 

*Create an event handler function and declare a namespace that calls it*. This way the event handler 
              function can be used in the control declaration in the markup.
            


 __js__
    


		var colorContainer,
	        sliderRedValue = 0,
	        sliderGreenValue = 0,
	        sliderBlueValue = 0;
	
		function changeSlideHandler(e) {
		    var slider = e.target;
	
		    if (slider.element.id == "sliderRed") {
		        sliderRedValue = e.value;
		    } else if (slider.element.id == "sliderGreen") {
		        sliderGreenValue = e.value;
		    } else if (slider.element.id == "sliderBlue") {
		        sliderBlueValue = e.value;
		    }
	
		    colorContainer.style.background = "rgb(" + sliderRedValue + "," + sliderGreenValue + "," + sliderBlueValue + ")";
		}
	
		WinJS.Namespace.define("RGBSlider", {
		    ChangeSlideHandler: WinJS.Utilities.markSupportedForProcessing(changeSlideHandler)
		});



Here are the things, that the event handler does:
            

* 

Gets the event's __target__ argument. It holds the element, that fired the event. The element should be 
                  one of the three __RadSlider__ controls.
                

* 

Checks the element's id attribute to determine exactly which of the three controls fired the event.
                

* 

Gets the control's selection by calling the event's __value__ argument and changes the corresponding 
                  color's value.
                

* 

Manipulates the background style of a div element to match the selected RGB color values.
                

Because the event handler has been added to both the __change__ and __slide__ events, 
              the color in the div element will change gradually while the user drags the slider and it will still change if the user 
              taps somewhere on the scale.
            

Below is an image of the three sliders and the colored div element.
        ![slider-choose-color](../Media/Controls\Slider\slider-choose-color.png)

This implementation is part of our 
          [SDK Examples](78ad1869-5dec-42ff-b17a-cc19d395089e) and is available for download at the following link: 
          [Telerik Windows 8 HTML SDK](https://github.com/telerik/win8-html-sdk/tree/master) under *Slider/ChooseColorWithRGBSliders*.
        

# Related Topics

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Events]({{slug:events}})
