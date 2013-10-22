---
title: Overview
meta_title: Overview
meta_description: description.
slug: 
tags:overview
publish:True
---


RadGrid offers keyboard navigation through all of its elements, as well as keyboard support for most of its features: __sorting__, 
        __filtering__, __data editing__ and __selecting__.
      

# 

In order to enable the built-in keyboard support of the __RadGrid__ control, you need to set its __navigatable__ 
          property to *true*.
        

Below you can find a list of the recognized keys by the keyboard support logic of the
          __RadGrid__.
        

* 

Focus the control: __TAB__ key when __RadGrid__ is next in the tab order.
            

* 

Actions applied on the grid cells:
            ![grid-keyboard-cells](../Media/Controls\Grid\grid-keyboard-cells.png)

* 

Navigating the grid cells: __Arrow keys__.
                

* 

Expand/collapse group or hierarchical table: __Enter__ on header/parent cell.
                

* 

Select currently highlighted cell/row: __Space__.
                

Whether only the highlighted cell or the whole row of the highlighted cell will
                  be selected depends on the chosen selection mode ('cell', 'row', 'multiple, cell', 'multiple, row').
                

* 

Select currently highlighted cell/row with persistence of previous selection: __Ctrl + Space__. Requires one of the two 'multiple' 
                  selection modes to be enabled.
                

* 

Actions applied on the grid header:
            ![grid-keyboard-header](../Media/Controls\Grid\grid-keyboard-header.png)

* 

Navigating the grid header: __Arrow keys__.
                

* 

Sort by a column: __Enter__.
                

* 

Open filter menu: __Alt + down arrow__.
                

* 

Close filter menu: __Esc__.
                

* 

Navigate filter menu: __TAB__.
                

* 

Navigate filter menu backwards: __Shift + TAB__.
                

* 

Scrolling:
            

* 

Scroll down: __Page Down__.
                

* 

Scroll up: __Page Up__.
                

* 

Scroll to bottom: __End__.
                

* 

Scroll to top: __Home__.
                

* 

Keyboard support with data editing:
            

* 

Enter edit mode on highlighted cell/row: __Enter__.
                

Note that in a hierarchy scenario, you will not be able to enter edit mode for the parent row, as the __Enter__ key will expand/collapse the 
                  child table. You can still enter edit mode using the mouse or touch commands.
                

* 

Submit cell/row edit: __Enter__ when already in edit mode.
                

* 

Dismiss cell/row edit: __Esc__.
                

* 

Edit next cell: __TAB__.
                >
            To be able to use <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">RadGrid's</legacyBold> built-in keyboard support for features like <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">sortable</legacyBold>, <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">filterable</legacyBold>,
            <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">selectable</legacyBold> or <legacyBold xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5">editable</legacyBold>, you need to first enable those features when you initialize the control.
          

# Related Topics
