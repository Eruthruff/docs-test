---
title: Day Template
meta_title: Day Template
meta_description: description.
slug: 
tags:day,template
publish:True
---


RadCalendar allows you to specify a template for its cells. This way you can implement special days and display additional content in their cells. Or you
				can simply style only specific cells. This article describes two main scenarios - how to provide common formatting for given dates; and how to display different
				content in cells based on their corresponding dates.
			

# Section1Highlight specific dates

If you want to apply identical formatting, or display identical content for certain dates in RadCalendar, you can use the __dates__
					property in combination with the __month.template__ one. __dates__ accepts an array of __Date__
					objects, which will be passed to the template. __month.template__ allows you to specify a template for each cell in the calendar. In this
					template you can make comparison between the current date and the dates in the array you have specified. When you find a match, you can output different content
					for the cell.
				

The following sample defines three days and when encountered in the template function, their value is returned wrapped in a __div__
					element with a custom CSS class assigned:
				


 __js__
    


					var highlightDates = [
						new Date(2013, 6, 12),
						new Date(2013, 6, 16),
						new Date(2013, 6, 24)
					];
	
					var highlightCalendarCtrl = new Telerik.UI.RadCalendar(document.getElementById("highlightCalendar"), {
						dates: highlightDates,
						value: new Date(2013, 6, 11),
						month: {
							template: "#=Templates.highlightDates(data)#"
						}
					});



And the template function looks like this:


 __js__
    


		highlightDates: function (data) {
			for (var i = 0; i < data.dates.length; i++) {
				if (data.date - data.dates[i] == 0) {
					return "<div class='template'>" + data.date.getDate() + "</div>"
				}
			}
			//#return the date string only if there is no match
			return data.date.getDate();



Now, to apply a background color and to position the template content the same way as other cells are positioned, the following styles are added:


 __none__
    


	.template {
		background-color: #faecca;
		height: calc(100% + 6px); /*expand the cell content vertically*/
		width: calc(100% + 6px); /*expand the cell content horizontally*/
		text-align: left;
		display: -ms-flexbox;
		-ms-flex-align: end;
		margin-left: -3px;
		margin-bottom: -3px;
		padding-left: 3px;
		padding-bottom: 3px;
	}



Here is an image of the resulting look:![calendar-templates-simple](../Media/Controls\Calendar\calendar-templates-simple.png)

# Custom day templates

When you have a list of dates with different types of events associated with them, you would need a bit more custom logic. Following is an example which
					implements such scenario.
				

First, we define an array with the event dates and their description (this could, of course, be retrieved from a remote service or local file).


 __js__
    


		events: [
			{ Date: new Date(2013, 6, 10), Event: "Jessie Birthday" },
			{ Date: new Date(2013, 6, 7), Event: "Veronica Party" },
			{ Date: new Date(2013, 6, 21), Event: "Martin Birthday" }



Now, we can define RadCalendar with a call to a custom template function:


 __js__
    


					var eventsCalendarCtrl = new Telerik.UI.RadCalendar(document.getElementById("eventsCalendar"), {
						value: new Date(2013, 6, 1),
						month: {
							template: "#=Templates.getTemplate(data, Templates.events)#"
						}
					});



In the template function we first check for a date match and if such occurs, the type of event is extracted from the event name. Based on the event type,
					a different image is output in the calendar cell:
				


 __js__
    


		getTemplate: function (data, events) {
			//for each day, traverse the events and look for equal dates
			for (var i = 0; i < events.length; i++) {
				if (data.date - events[i].Date == 0) {
					//if dates are equal, check the type of associated event and output the relevant image,
					// along with a title, that will be shown as tooltip when the image is hovered
					if (events[i].Event.indexOf("Birthday") != -1) {
						return "<img width='24px' src='bday.png' title='" + events[i].Event + "'/>";
					}
					else {
						return "<img width='24px' src='cocktail.png' title='" + events[i].Event + "'/>";
					}
				}
			}
			//#return the date string only if there is no match
			return data.date.getDate();
		}



The result is shown below:![calendar-templates-advanced](../Media/Controls\Calendar\calendar-templates-advanced.png)

# Related Topics

 * [Using Templates in RadControls]({{slug:using-templates-in-radcontrols}})
