

The RadNumericBox control supports a number of standard and custom number formats that govern how the number in the numeric box will look like.
				To apply a format to the control, assign one of the possible values described below to its __format__ property.
			

# StandardNumericFormatsStandard numeric formats

* 

__"n" for number__

A number like 1234.567 will be displayed like 1,234.57 with format "n"(thousands separator and two digits after the decimal point).

A number like 1234.567 will be displayed like 1,235.567  with format "n3" (thousands separator and three digits after the decimal point).

* 

__"c" for currency__

A number like 1234.567 will be displayed like $1,234.57 with format "c" (currency sign, thousands separator, and two digits after the decimal point).

A number like 1234.567 will be displayed like $1,235 with format "c0" (currency sign, thousands separator, and no digits after the decimal point).

* 

__"p" for percentage__ (number is multiplied by 100)

A number like 0.222 will be displayed like 22.20 % with format "p" (percent sign and two digits after the decimal point).

A number like 0.222 will be displayed like 22 % with format "p0" (percent sign and no digits after the decimal point).

* 

__"e" for exponential__

A number like 0.122 will be displayed like 1.22e-1 with format "e" (two digits after the decimal point and exponent).

A number like 0.122 will be displayed like 1.2200e-1 with format "e4" (four digits after the decimal point and exponent).

# CustomNumericFormatsCustom numeric formats

You can create custom numeric format string using one or more custom numeric specifiers. Custom numeric format string is any that is not a 
					standard numeric format. Here is a list of the supported format specifiers:
				

* 

__"0" - zero placeholder__

Replaces the zero with the corresponding digit if one is present; otherwise, zero appears in the result string - 1234.5678 formatted with "00000" will look like 01235.

* 

__"#" - digit placeholder__

Replaces the pound sign with the corresponding digit if one is present; otherwise, no digit appears in the result string - 1234.5678 formatted with "#####" will look like 1235.

Note: "#" specifier cannot be used to format a number as telephone number, i.e. (###)-###-####

* 

__"." - decimal placeholder__

Determines the location of the decimal separator in the result string - 0.45678 formatted with "0.00" becomes 0.46.

* 

__"," - group separator placeholder__

Insert localized group separator between each group - 12345678 formatted with  "##,#" becomes 12,345,678.

* 

__"%" - percentage placeholder__

Multiplies a number by 100 and inserts a localized percentage symbol in the result string.

* 

__";" - section separator__

Defines sections wih separate format strings for positive, negative, and zero numbers.

* 

__"string"/'string'__ - Literal string delimiter

Indicates that the enclosed characters should be copied to the result string.

# Related Topics