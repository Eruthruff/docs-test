---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


From Q2 2013 on, __RadControls__ for Windows 8 HTML offer culture support capabilities. You can set a global culture for all  
        __RadControls__ in your application or you can set a control specific culture. The controls that can be affected by a culture setting are 
        __RadCalendar__, __RadChart__, __RadDatePicker__, __RadTimePicker__
        and __RadNumericBox__. The following article explains the ways to set cultures and change them dynamically.
      

# Global Culture




To operate with cultures using __RadControls__ you must use the __Telerik.Culture__ namespace. Use the 
          __setCurrent()__ method to set a global culture for all __RadControls__:
        

	
          Telerik.Culture.setCurrent("de-DE", true);
        



The __setCurrent()__ method takes two parameters:
        

* 

*Culture string* - Available culture strings are any valid *BCP-47* language tags with the 
              language for the first part and region for the second, for example: *en-US*, *en-UK*, 
              *fr-FR*, *de-DE*, etc. The default culture is *en-US*.
            

* 

*24H/12H format* - The second parameter is of type boolean. If set to *true*, the time will be shown 
              as 24 hour format and if it is set to *false* the time will be in 12 hour format. The default value is the given 
              culture's native clock format.
            >
            To set a global culture for all RadControls in your application, you need to use the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">setCurrent()</legacyBold> method before 
            the controls are initialized, i.e., before the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">processAll()</legacyBold> method.
          >
            Also, if you want to change the global culture at a later moment in your application, be advised that only newly initialized controls will be 
            affected by the change.
          

To get the current global culture you can use the __getCurrent()__ method of the same namespace. The return value is a valid 
          *BCP-47* language tag.
        

	
          Telerik.Culture.getCurrent();
        



# Control Specific Culture

You can also set a culture for each __RadControl__ through its __culture__ property:
        

	
          <span id="numericBox" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
                culture: 'fr-FR',
                format: 'c0'
            }"></span>
        



You can also modify each control's __culture__ property programmaticaly:
        

	
          document.getElementById("numericBox").winControl.culture = "en-UK";
        

>
            There is one exception - the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadChart</legacyBold> has its <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">culture</legacyBold> option under the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">labels</legacyBold>
            property and is used only for date formatting.
          >
            Also, in case <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadChart's</legacyBold> culture has been changed after initialization, the control has to be refreshed for the new culture to take 
            effect. This is done by calling <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadChart's refresh()</legacyBold> method.
          

# 
        String Formatting with Culture
      

Cultures can be applied when you want to format a value with the __Telerik.Utilities.toString()__ method. The method takes three arguments: 
          an object value, a format string and a culture string. 
        

	
          Telerik.Utilities.toString(100, "c1", "en-US");
        



The above code will produce "$100.0". You can find a full list of format strings and explanation about them 
          [here](0c3b0ea5-3850-4c90-86b3-5d20f2a18c1e).
        

# Related Topics

 * [Define Culture Information]({{slug:define-culture-information}})

 * [Formatting]({{slug:formatting}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})
