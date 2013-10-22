---
title: Getting Started
meta_title: Getting Started
meta_description: description.
slug: 
tags:getting,started
publish:True
---


__RadRadialMenu__ for Windows 8 is an HTML/JavaScript component that provides rich APIs for constructing a 
        circular context menu. In this getting started article, you will learn how to create a basic radial menu, reference it in JavaScript, 
        modify its properties, and attach event handlers to it.
      

# prerequisitesPrerequisites

Before you declare a RadControl in your application, make sure that you have added the references to the needed JavaScript and CSS
          resources, as described here:
        

[Adding RadControls to an HTML Page](c2af6caa-6b40-4378-b20b-2e35a0425962)

# creationCreating a RadRadialMenu

You can initialize __RadRadialMenu__ like all other RadControls for Windows 8 HTML components. To 
          create a __RadRadialMenu__ in the HTML markup, add an empty __div__ element with 
          a __data-win-control__ attribute with a value of __Telerik.UI.RadRadialMenu__.
        


 __html__
    


	            <div data-win-control="Telerik.UI.RadRadialMenu"></div>



Alternatively, you can initialize __RadRadialMenu__ programmatically by first defining an empty 
          __div__ element with an __id__ and passing it to the control's constructor in 
          JavaScript.
        


 __html__
    


	            <div id="myRadialMenu"></div>




 __js__
    


				    var myRadialMenu = new Telerik.UI.RadRadialMenu(document.getElementById("myRadialMenu"));



Defining __RadRadialMenu__ with no properties set will not produce a usable control. A context menu needs 
          at least some items to serve its purpose. You can see a basic example of declaring a usable __RadRadialMenu__ 
          in __Code Listing 4__ in the next section.
        

# optionsSetting RadRadialMenu Options

Just like any other Windows Runtime JavaScript control, __RadRadialMenu__ options can be defined through 
          the __data-win-options__ attribute in the mark-up. In the following example two menu items are added and 
          a textarea HTML element is set as a target for the radial menu.
        


 __html__
    


	            <textarea id="target1"></textarea>
	            <div data-win-control="Telerik.UI.RadRadialMenu" data-win-options="{
	                    target: '#target1',
	                    items: [
	                        {
	                            text: 'Font size',
	                            icon: '\uE1C8'
	                        }, {
	                            text: 'Font',
	                            icon: '\uE185'
	                        }
	                    ]
	                }"></div>



Alternatively, you can programmatically pass an options object as a second argument to the control constructor:
        


 __html__
    


	            <textarea id="target2"></textarea>
	            <div id="myMenuWithOptions"></div>




 __js__
    


				    var myMenuWithOptions = new Telerik.UI.RadRadialMenu(document.getElementById("myMenuWithOptions"), {
				        target: '#target2',
				        items: [
	                        {
	                            text: 'Font size',
	                            icon: '\uE1C8'
	                        }, {
	                            text: 'Font',
	                            icon: '\uE185'
	                        }
				        ]
				    });



For detailed information regarding __RadRadialMenu__'s properties refer to the related articles at the bottom 
          of the article.
        

Both examples produce the same output. You can see the radial menu in __Figure 1__ below.
        Figure 1: Basic RadRadialMenu![radialmenu-getting-started-options](../Media/Controls\RadialMenu\radialmenu-getting-started-options.png)

# accessingReferencing RadRadialMenu Control Instance

At some point you might need to access the control in JavaScript to modify properties or get data. If __RadRadialMenu__ 
          has been initialized in the mark-up, you will need to get a reference to it.
          As described in
          [this MSDN article about adding controls to a Windows Store app](http://msdn.microsoft.com/en-us/library/windows/apps/hh465493.aspx),
          any control in a Windows Runtime JavaScript application requires a call to __WinJS.UI.processAll()__ for proper
          initialization. The same holds true for any of the Telerik UI controls. Once, the WinJS framework has initialized all the controls
          on the page, the __RadRadialMenu__ control instance associated with a host HTML element can be retrieved using the
          __winControl__ expando property of the host HTML element.
        


 __js__
    


	            WinJS.UI.processAll().then(function () {
	                //wait for the processAll() method to finish, then find the
	                //menu control from the host element's winControl property
	                var menuElement = document.getElementById("myRadialMenu");
	                var menuControl = menuElement.winControl;
	                console.log(menuControl instanceof Telerik.UI.RadRadialMenu); // true
	            });



# modifyingModifying RadRadialMenu Properties

Once __RadRadialMenu__ is loaded and the control is referenced in JavaScript, the control exposes an extensive 
          set of properties, methods and events. In the below example the __background__, __innerBackground__ 
          and __border__ property values are modified after the control's initialization.
        


 __js__
    


				    menuControl.background = "#000";
				    menuControl.innerBackground = "#72F0FF";
				    menuControl.border = "#72F0FF";



To see all available configuration options, look at the members, constructors, methods, properties and events available for 
          the T:Telerik.UI.RadRadialMenu class.
        

# eventsAttaching Events

A context menu is not of much use if the menu items don't do anything. To add function to __RadRadialMenu__, you need to attach 
          handlers to its events. You can either declare an event handler in the options object that 
          you pass to the control during initialization, or you can use the __addEventListener__ method to attach a 
          function for execution upon a certain event. Below you can see samples of both approaches:
        


 __js__
    


				    var changingColorsMenu = new Telerik.UI.RadRadialMenu(document.getElementById("changingColorsMenu"), {
				        target: '#target3',
				        onexpand: changeInnerBackground
				    });
	
	                // or
	
				    var changingColorsMenu = new Telerik.UI.RadRadialMenu(document.getElementById("changingColorsMenu"), {
				        target: '#target3',
				        onexpand: function (e) {
				            var colors = ["red", "green", "blue", "yellow"];
				            var randomColorIndex = Math.floor(Math.random() * 3);
	
				            var menu = e.menu;
				            menu.innerBackground = colors[randomColorIndex];
				        }
				    });

>
            You can also declare event handlers in HTML mark-up in the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">data-win-options</legacyBold> attribute. To do that 
            you need to mark the handler function as safe in your code, using the <externalLink xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5"><linkText>WinJS.Utilities.markSupportedForProcessing</linkText><linkUri>http://msdn.microsoft.com/en-us/library/windows/apps/hh967819.aspx</linkUri></externalLink> function.
          


 __js__
    


				    changingColorsMenu.addEventListener("expand", changeInnerBackground);



In the above examples, the radial menu's inner background color is randomized between four predefined colors when the
          __expand__ event is triggered.
        

You can also add event handlers to each single menu item to make it functional. This can be done in a declarative manner in the 
          options object of the control or through the __addEventListner__ method.
        


 __js__
    


				    var myMenu = new Telerik.UI.RadRadialMenu(document.getElementById("itemEventsMenu"), {
				        target: '#target4',
				        items: [
	                        {
	                            id: 'ChangeColor',
	                            text: 'Change Color',
	                            icon: '\uE186',
	                            onaction: changeInnerBackground
	                        }
				        ]
				    });
	
				    // or
	
				    myMenu.getItem('ChangeColor').addEventListener("action", changeInnerBackground);



# Related Topics
