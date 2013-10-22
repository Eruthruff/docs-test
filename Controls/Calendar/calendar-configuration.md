---
title: Properties and Configuration
meta_title: Properties and Configuration
meta_description: description.
slug: 
tags:properties,and,configuration
publish:True
---


This help article will introduce you to the configuration options of RadCalendar.

# Setting culture

You can explicitly set culture to RadCalendar through its __culture__ property. Valid values are represented as a 
          [BCP-47](http://tools.ietf.org/html/bcp47) language tag, e.g. *"fr-FR"*. For more information regarding Telerik culture support you 
          can visit this article: [Culture Support](d3c7ea15-4986-48fe-9cc7-db2f1c03a57f).
        

Changing the culture results in translating the day, week and month names, as well as ordering the week days in accordance to the culture. For example, in a
					calendar using "en-US" culture, the week starts on Sunday, while in a "fr-FR" calendar, the week starts on Monday.
				

The following sample defines a RadCalendar using French culture:


 __js__
    


					var frCalendar = new Telerik.UI.RadCalendar(document.getElementById("calendar1"), {
						culture: "fr-FR"
					});

![calendar-configuration-culture](../Media/Controls\Calendar\calendar-configuration-culture.png)

# Setting min and max date

To limit the range of dates from which the user can select, you can set the __min__ and __max__ properties.
					__min__ will define the earliest date available for selection and __max__ - the latest. The dates outside of this
					range will be disabled.
				

The following example sets min date to be today and max date - three months after today. You can see in the image how the two months at the end of the
					range look:
				


 __js__
    


					var today = new Date();
					var minMaxCalendar = new Telerik.UI.RadCalendar(document.getElementById("calendar2"), {
						min: today,
						max: new Date(today.getFullYear(), today.getMonth() + 3, today.getDate())
					});

![calendar-configuration-min-max](../Media/Controls\Calendar\calendar-configuration-min-max.png)

# Controlling the navigation views

You can choose which view in the calendar to be accessible to the end-user. For example, you may want them to be able to select a month and not display
					the separate days to them. In this case you can set __start__=*"year"*
					and then set __depth__=*"year"*.
				

The __start__ property defines the view which will be
					initially visible to the user. It accepts string values from the following list: *"month"* (default),
					*"year"*, *"decade"* and *"century"*.
				

__depth__ determines the navigation depth. It recognizes the same list of values: *"month"* (default),
					*"year"*, *"decade"* and *"century"*.
				

You can see the above scenario in the sample below:


 __js__
    


					var navDepthCalendar = new Telerik.UI.RadCalendar(document.getElementById("calendar3"), {
						start: "year",
						depth: "year"
					});

![calendar-configuration-start-depth](../Media/Controls\Calendar\calendar-configuration-start-depth.png)

# Footer settings

# Controlling footer visibility

You can decide whether RadCalendar's footer is visible or not, by setting __footer.enabled__ property to
							*true* or *false*.
						


 __js__
    


					var hiddenFooterCalendar = new Telerik.UI.RadCalendar(document.getElementById("calendar4"), {
						footer: {
							enabled: false
						}
					});

![calendar-configuration-footer](../Media/Controls\Calendar\calendar-configuration-footer.png)

# Changing footer text

The footer contains a quick link to today's date. By clicking/tapping it, the end user can navigate to today's date in month view from any other view in
							the calendar. By default, the link displays today's date, formatted according to the current culture. You can customize the text, shown in the footer by
							setting its __template__ property. The current date is passed as string variable, named *data*:
						


 __js__
    


					var footerTemplateCalendar = new Telerik.UI.RadCalendar(document.getElementById("calendar5"), {
						footer: {
							template: "Navigate to today: #=new Date(data).toDateString()#"
						}
					});
	

![calendar-configuration-footer-template](../Media/Controls\Calendar\calendar-configuration-footer-template.png)

# Related Topics
