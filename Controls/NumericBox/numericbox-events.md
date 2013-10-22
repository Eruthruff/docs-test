---
title: Events
meta_title: Events
meta_description: description.
slug: 
tags:events
publish:True
---


This article describes the events of RadNumericBox and its most notable event arguments.
			

# Section1Events

Event Name

Description

Arguments

__change__

Fires when the value is changed.
							

__e.target__ - The RadNumericBox control which value has changed. The new value can be accessed 
								through __e.target.value__.
							

__spin__

Fires when the value is changed from the spin buttons.
							

__e.target__ - The RadNumericBox control instance. The new value can be accessed through
								__e.target.value__.
							

Below you can see a sample where the __change__ event is handled to access the new RadNumericBox value:


 __html__
    


				<span id="myNumericBox" data-win-control="Telerik.UI.RadNumericBox" data-win-options="{
					onchange: NumericBox.Helpers.change
				}"></span>
				<p id="numericBoxInfo" style="color: #336699"></p>




 __js__
    


	WinJS.Namespace.define("NumericBox.Helpers", {
		change: WinJS.Utilities.markSupportedForProcessing(function (e) {
			document.getElementById("numericBoxInfo").innerText = "Numeric box value was changed to: " + e.target.value + ".";
		})
	});



# Related Topics
