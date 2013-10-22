---
title: Formatting
meta_title: Formatting
meta_description: description.
slug: 
tags:formatting
publish:True
---


RadControls that offer date and numeric formatting use common format strings. This article will introduce you to the formatting options
				available.
			

The format string is specified using the following pattern:

	
				"{0:formatPlaceholders}"
			



The format placeholders are listed in the following sections.

# Section1Formatting Numbers

# Standard Numeric Formats

* 

__"n"__ for number
								

A number like 1234.567 will be displayed like 1,234.57 with format "n"(thousands separator and two digits after the decimal point).

A number like 1234.567 will be displayed like 1,235.567  with format "n3" (thousands separator and three digits after the decimal point).

* 

__"c"__ for currency
								

A number like 1234.567 will be displayed like $1,234.57 with format "c" (currency sign, thousands separator, and two digits after the decimal point).

A number like 1234.567 will be displayed like $1,235 with format "c0" (currency sign, thousands separator, and no digits after the decimal point).

* 

__"p"__ for percentage (number is multiplied by 100)
								

A number like 0.222 will be displayed like 22.20 % with format "p" (percent sign and two digits after the decimal point).

A number like 0.222 will be displayed like 22 % with format "p0" (percent sign and no digits after the decimal point).

* 

__"e"__ for exponential
								

A number like 0.122 will be displayed like 1.22e-1 with format "e" (two digits after the decimal point and exponent).

A number like 0.122 will be displayed like 1.2200e-1 with format "e4" (four digits after the decimal point and exponent).

# Custom Numeric Formats

You can create custom numeric format string using one or more custom numeric placeholders. Custom numeric format string is any that is not a
							standard numeric format. Here is a list of the supported format placeholders:
						

* 

__"0"__ - zero placeholder
								

Replaces the zero with the corresponding digit if one is present; otherwise, zero appears in the result string - 1234.5678 formatted with "00000" will look like 01235.

* 

__"#"__ - digit placeholder
								

Replaces the pound sign with the corresponding digit if one is present; otherwise, no digit appears in the result
									string - 1234.5678 formatted with "#####" will look like 1235.
								

Note: The "#" placeholder cannot be used to format a number as a telephone number, i.e. (###)-###-####

* 

__"."__ - decimal placeholder
								

Determines the location of the decimal separator in the result string - 0.45678 formatted with "0.00" becomes 0.46.

* 

__","__ - group separator placeholder
								

Insert a localized group separator between each group - 12345678 formatted with  "##,#" becomes 12,345,678.

* 

__"%"__ - percentage placeholder
								

Multiplies a number by 100 and inserts a localized percentage symbol in the result string.

* 

__";"__ - section separator
								

Defines sections with separate format strings for positive, negative, and zero numbers.

* 

__"string"/'string'__ - literal string delimiter
								

Indicates that the enclosed characters should be copied to the result string.

# Formatting Dates

# Standard Date Formats

For the examples in the following list, we will use the date *Sat Nov 06 2010*.
						

* 

__"d"__ - short date pattern
								

The date will be formatted as: *11/6/2010*.
								

* 

__"D"__ - long date pattern
								

The date will be formatted as: *Monday, November 06, 2010*.
								

* 

__"F"__ - full date/time pattern (number is multiplied by 100)
								

The date will be formatted as: *Monday, November 06, 2010 12:00:00 AM*.
								

* 

__"g"__ - general date/time pattern (short time)
								

The date will be formatted as: *11/6/2010 12:00 AM*.
								

* 

__"G"__ - general date/time pattern (long time)
								

The date will be formatted as: *11/6/2010 12:00:00 AM*.
								

* 

__"m|M"__ - month/day pattern
								

With format "{0:m}" the date will be formatted as: *November 06*.
								

* 

__"u"__ - universal sortable date/time pattern
								

The date will be formatted as: *2010-11-06 00:00:00Z*.
								

* 

__"y|Y"__ - month/year pattern
								

With format "{0:y}" the date will be formatted as: *November, 2010*.
								

# Custom Date Formats

You can create custom date formats by using one or more custom date placeholders. A custom date format string is any that is not a
							standard date format. Here is a list of the supported format placeholder:
						

For the examples in the following list, we will use the date *Tue Jul 06 2010*.
						

* 

__"d"__ - the day of the month, from 1 to 31
								

* 

__"dd"__ - the zero-padded day of the month - from 01 to 31
								

* 

__"ddd"__ - the abbreviated name of the day of the week
								

With format "{0:__ddd__, d MMM, yyyy}" the date will be formatted as: *__Tue__, 6 Jul, 2010 *.
								

* 

__"dddd"__ - the full name of the day of the week
								

With format "{0:__dddd__, d MMM, yyyy}" the date will be formatted as: *__Tuesday__, 6 Jul, 2010 *.
								

* 

__"M"__ - the month, from 1 to 12
								

* 

__"MM"__ - the zero-padded month, from 01 to 12
								

* 

__"MMM"__ - the abbreviated name of the month
								

With format "{0:ddd, d __MMM__, yyyy}" the date will be formatted as: *Tue, 6 __Jul__, 2010 *.
								

* 

__"MMMM"__ - the full name of the month
								

With format "{0:dddd, d __MMMM__, yyyy}" the date will be formatted as: *Tuesday, 6 __July__, 2010 *.
								

* 

__"yy"__ - the year, from 00 to 99
                

With format "{0:dddd, d MMMM, __yy__}" the date will be formatted as: *
                    Tuesday, 6 July, __10__*.
                

* 

__"yyyy"__ - the year as a four-digit number
                

With format "{0:dddd, d MMMM, __yyyy__}" the date will be formatted as: *
                    Tuesday, 6 July, __2010__*.
                

* 

__"h"__ - the hour, using 12-hour clock - from 1 to 12
								

* 

__"hh"__ - the zero-padded hour, using 12-hour clock - from 01 to 12
								

* 

__"H"__ - the hour, using 24-hour clock - from 0 to 23
								

* 

__"HH"__ -  the zero-padded hour, using 24-hour clock - from 00 to 23
								

* 

__"m"__ - the minute, from 0 to 59
								

* 

__"mm"__ - the zero-padded minute, from 00 to 59
								

* 

__"s"__ -  the second, from 0 to 59
								

* 

__"ss"__ -  the zero-padded second, from 00 to 59
								

* 

__"f"__ - the tenths of a second
								

* 

__"ff"__ - the hundreds of a second
								

* 

__"fff"__ - the milliseconds
								

* 

__"tt"__ -  the AM/PM designator
								

# Related Topics

 * [Overview]({{slug:overview}})

 * [Define Culture Information]({{slug:define-culture-information}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})

 * [Properties and Configuration]({{slug:properties-and-configuration}})
