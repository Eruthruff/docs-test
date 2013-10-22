---
title: Validation
meta_title: Validation
meta_description: description.
slug: 
tags:validation
publish:True
---


Validation of data is of major importance when editing data. You need to prevent the user for typing in both invalid and malicious data into
				the edited cells. Achieving this with RadGrid and its built-in Telerik.Data.DataSource component is quite easy. All you need to do is describe
				how each field should be validated. Then, RadGrid will automatically perform validation on the input and display popup messages notifying
				the user about the invalid data entered.
			

This article presents a RadGrid, displaying all available validation options. For a more detailed
				description of setting the data model for editing, check this article: [](142aaf90-387f-4688-9e64-11e31edbdf75).
			

# Section1Validating RadGrid editing

Following is an example, demonstrating all validation options in RadGrid. Note that the following pieces of code are defined inside
					__dataSource.schema.model.fields__. Also, for better understanding of the validation shown below, here is an example
					of valid data for the RadGrid from this sample scenario:
				


 __js__
    


							{
								Name: "Jack Miles",
								BirthDate: new Date(1982, 9, 10),
								Email: "jack.miles@example.com",
								HomePage: "http://example.com",
								Points: 20,
								ParticipantID: "19822136", //first four digits are the year of birth
								RecID: 2
							}



# Required fields

Defining a field as required is done by setting __validation.required__ to *true*
							in its definition.
						


 __js__
    


										Name: {
											validation: {
												required: true
											}



# Date fields

Date validation is added to a field by setting __validation.date__ to *true*
							in its definition. However, note that if you have already defined the field as date (__type: "date"__),
							validation will not be needed since it renders a RadDatePicker which always works with valid __Date__
							objects.
						


 __js__
    


										BirthDate: {
											type: "date",
											validation: {
												date: true
											}



# Email validation

There is also built-in validation for email addresses. To apply it on an edited field, set
							__validation.email__ to *true*.
						


 __js__
    


										Email: {
											validation: {
												email: true
											}



# URL validation

You can set __validation.url__ to *true* to a field if it should contain only
							valid URLs.
						


 __js__
    


										HomePage: {
											validation: {
												url: true
											}



# Numeric validation

There are a few options for validating numeric values in RadGrid. In the validation object, you can set the following three
							properties:
						

* 

__min__: to compare the input against a minimum value.
								

* 

__max__: to compare the input against a maximum value.
								

* 

__step__: input will be valid only if it can be divided by the step value without remainder.
								

You can use any of these properties separately or combined.


 __js__
    


										Points: {
											type: "number",
											validation: {
												min: 0,
												max: 30,
												step: 5
											}



# Pattern (regular expression) validation

To validate a value against a regular expression, set __validation.pattern__ to a regular expression
							of your choice. You can see a sample in the next section.
						

# Custom validation

For more customized validation (for example accessing values from other cells), you can provide a custom validation function.
							You can give it any name (that is not a reserved JavaScript word). It accepts as value a jQuery object carrying the HTML element
							of the editor control. It must return *true* if validation has passed and
							*false* if it hasn't.
						

To provide a validation message, assign a custom attribute to the jQuery element
							which follows this namin model: *data-[fnName]-msg*, where [fnName] is the name of the custom validation
							function.
						

The following example combines a regular expression check on the value and custom validation, that checks whether the id
							starts with the year of birth of the participant.
						


 __js__
    


										ParticipantID: {
											validation: {
												pattern: "\\d{8}",
												checkYear: function (el) {
													var value = el.val().substring(0, 4);
													var year = grid.dataItem(el.closest("tr")[0]).BirthDate.getFullYear();
													if (value != year) {
														el.attr("data-checkYear-msg", "Participant ID does not match birth date");
														return false;
													}
													return true;
												}
											}



# Related Topics
