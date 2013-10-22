---
title: Resizing
meta_title: Resizing
meta_description: description.
slug: 
tags:resizing
publish:True
---


By default, RadGrid splits its available width equally between all columns. In cases when the content of some column could vary in width, RadGrid allows you to
				enable resizing of its columns, so that the user can adjust them for easier readability. To turn on resizing, set the
				__resizable__ property to *true*. By default, resizing is disabled.
			

# Column Resizing

When resizing is enabled by setting __resizable__ to true, the user can perform the following actions:
				

* 

Click/tap and hold the grid column header. This will highlight the column header and the column header will display a drag handle.
						

* 

Drag the handle to resize the column that has been set for resizing. The column will start resizing and so will the grid.

* 

Click anywhere outside of the column header to hide the drag handle.![grid-columns-resizing](../Media/Controls\Grid\grid-columns-resizing.png)


 __js__
    


				<div id="grid1" data-win-control="Telerik.UI.RadGrid" data-win-options="{
					dataSource: {
						data: [
							{ FirstName: 'Nancy', LastName:'Davolio', Title:'Sales Representative', Notes:'Education includes a BA in psychology from Colorado State University in 1970. '},
							{ FirstName:'Andrew', LastName:'Fuller', Title:'Vice President, Sales', Notes:'Andrew received his BTS commercial in 1974 and a Ph.D. in international marketing from the University of Dallas in 1981.'  },
							{ FirstName:'Margaret', LastName:'Peacock', Title:'Sales Representative', Notes:'Margaret holds a BA in English literature from Concordia College.'  }
						]
					},
					resizable: true
				}">
				</div>



# Related Topics
