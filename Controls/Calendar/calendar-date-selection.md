---
title: Date Selection
meta_title: Date Selection
meta_description: description.
slug: 
tags:date,selection
publish:True
---


Since Q3 2013 __RadCalendar__ offers three built-in date selection modes to choose from: 
        single date, single range and multiple ranges. The modes are set through the __selection.mode__ property.
        In the following help article you can find information regarding the selection modes and how to use them.
      

# Section1Single Date Selection

The single date selection mode allows the user to select a single date cell from 
          __RadCalendar__. Selecting another cell will remove any previous selection. 
          This is also the default selection mode. To explicitly allow this mode, set the __mode__ 
          option value of the __selection__ property to *"singleDate"*.
        


 __html__
    


				<div id="singleDateCalendar" data-win-control="Telerik.UI.RadCalendar" data-win-options="{
	                    selection: {
	                        mode: 'singleDate'
	                    }
	                }"></div>



In this mode __RadCalendar__ has a single date as a value. To get or set it use the 
          __value__ property.
        


 __js__
    


				    var singleDateCalendar = Telerik.UI.find.Calendar("#singleDateCalendar");
				    singleDateCalendar.value = new Date(2013, 8, 7);
				    var calendarValue = singleDateCalendar.value;



# Single Range Selection

This selection mode allows the user to select a single range of dates from __RadCalendar__. 
          Selecting another cell or range of cells will remove any previous selection. To configure __RadCalendar__ 
          to use this mode, set the __mode__ option value of the __selection__ property 
          to *"singleRange"*.
        


 __html__
    


				<div id="singleRangeCalendar" data-win-control="Telerik.UI.RadCalendar" data-win-options="{
	                    selection: {
	                        mode: 'singleRange'
	                    }
	                }"></div>



In this mode __RadCalendar__ has a single range object as a value. The range object has two 
          properties, that accept single dates: __start__ and __end__. To get or set 
          the range use the __selectedDateRange__ property.
        


 __js__
    


				    var singleRangeCalendar = Telerik.UI.find.Calendar("#singleRangeCalendar");
				    singleRangeCalendar.selectedDateRange = {
				        start: new Date(2013, 8, 1),
	                    end: new Date(2013, 8, 31)
				    };
				    var calendarValue = singleRangeCalendar.selectedDateRange;



The single range selection mode also provides a built-in option to use two instances of the control for one date range. 
          The user can select a starting date for the range from the first __RadCalendar__ and an end date 
          from the second control. This selection method is particularly useful when the user can select a range spanning in different months. 
          То configure this feature you need to first enable the single range selection mode for the start date calendar. Then 
          provide a query selector pointing to the second (end date) calendar to the __selection.singleRange.endCalendar__ 
          property. The second __RadCalendar__ control does not need to have any properties set.
        


 __html__
    


	            <div id="singleRangeStartCalendar" data-win-control="Telerik.UI.RadCalendar" data-win-options="{
	                    selection: {
	                        mode: 'singleRange',
	                        singleRange: {
	                            endCalendar: '#singleRangeEndCalendar'
	                        }
	                    }
	                }"></div>
	            <div id="singleRangeEndCalendar" data-win-control="Telerik.UI.RadCalendar"></div>



Below is an image of the two calendars and how the range appears in both of them.
        ![calendar-selection-singlerange-twocalendars](../Media/Controls\Calendar\calendar-selection-singlerange-twocalendars.png)

To get or set the date range with this feature enabled use the __selectedDateRange__ property of the 
          first (start date) __RadCalendar__ control. The second control is used only for UI purposes.
        

# Multiple Ranges Selection

The multiple ranges selection mode allows the user to select multiple ranges of dates 
          from __RadCalendar__. Selecting a single date cell will remove any previous selection. To 
          add а date cell range to the previous selection, the user has to either hold and swipe over a range on a touch 
          enabled device or to drag over a range with a mouse. To add a single date cell to a previous selection on a device 
          with no touch screen, the user has to press the *Ctrl* key and select the cell. 
          To allow this selection mode, set the __mode__ option value of the __selection__ 
          property to *"multipleRanges"*.
        


 __html__
    


				<div id="multipleRangesCalendar" data-win-control="Telerik.UI.RadCalendar" data-win-options="{
	                    selection: {
	                        mode: 'multipleRanges'
	                    }
	                }"></div>



In this selection mode you have a set of selected ranges as value. To get or set the ranges use the 
          __selectedDateRanges__ property. It holds an array of range objects.
        


 __js__
    


				    var multipleRangesCalendar = Telerik.UI.find.Calendar("#multipleRangesCalendar");
				    multipleRangesCalendar.selectedDateRanges = [
	                    {
				            start: new Date(2013, 7, 1),
				            end: new Date(2013, 7, 15)
	                    },
	                    {
	                        start: new Date(2013, 8, 1),
	                        end: new Date(2013, 8, 15)
	                    }
				    ];
				    var calendarValue = multipleRangesCalendar.selectedDateRanges;

>
            Note, that you can set date ranges through the <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">selectedDateRanges</legacyBold> in any order, but 
            if they are later modified through the UI of the control, the control will sort the ranges chronologically and 
            consolidate ranges where needed. This means the array, that is returned by <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">selectedDateRanges</legacyBold> 
            might be different than the one you set.
          

# Related Topics
