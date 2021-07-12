# [Django Forms](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Django/Forms)

An HTML Form is a group of one or more fields/widgets on a web page, which can be used to collect information from users for submission to a server. Forms are a flexible mechanism for collecting user input because there are suitable widgets for entering many different types of data, including text boxes, checkboxes, radio buttons, date pickers and so on. Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site request forgery protection.

## HTML Forms

The form is defined in HTML as a collection of elements inside``` <form>...</form>``` tags, containing at least one ```input``` element of ```type="submit"```.

 The form attributes define the HTTP method used to send the data and the destination of the data on the server (action):

**action:** The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
**method:** The HTTP method used to send the data: post or get.
The **POST method** should always be used if the data is going to result in a change to the server's database because this can be made more resistant to cross-site forgery request attacks.
The **GET method** should only be used for forms that don't change user data (e.g. a search form). It is recommended for when you want to be able to bookmark or share the URL.
The role of the server is first to render the initial form state — either containing blank fields or pre-populated with initial values. After the user presses the submit button, the server will receive the form data with values from the web browser and must validate the information. If the form contains invalid data, the server should display the form again, this time with user-entered data in "valid" fields and messages to describe the problem for the invalid fields. Once the server gets a request with all valid form data, it can perform an appropriate action (e.g. saving the data, returning the result of a search, uploading a file, etc.) and then notify the user.

## Django form handling process

![Django form handling process](https://mdn.mozillademos.org/files/14205/Form%20Handling%20-%20Standard.png)

**The main things that Django's form handling does are:**

1. Display the default form the first time it is requested by the user.
    - The form may contain blank fields (e.g. if you're creating a new record), or it may be pre-populated with initial values (e.g. if you are changing a record, or have useful default initial values).
    - The form is referred to as unbound at this point, because it isn't associated with any user-entered data (though it may have initial values).
2. Receive data from a submit request and bind it to the form.
    - Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
3. Clean and validate the data.
    - Cleaning the data performs sanitization of the input (e.g. removing invalid characters that might be used to send malicious content to the server) and converts them into consistent Python types.
    - Validation checks that the values are appropriate for the field (e.g. are in the right date range, aren't too short or too long, etc.)
4. If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
5. If all data is valid, perform required actions (e.g. save the data, send an email, return the result of a search, upload a file, etc.)
6. Once all actions are complete, redirect the user to another page.


## Renew-book form using a Form and function view

**Form**
The Form class is the heart of Django's form handling system. It specifies the fields in the form, their layout, display widgets, labels, initial values, valid values, and (once validated) the error messages associated with invalid fields. The class also provides methods for rendering itself in templates using predefined formats (tables, lists, etc.) or for getting the value of any element (enabling fine-grained manual rendering).

***Declaring a Form***

The declaration syntax for a Form is very similar to that for declaring a Model, and shares the same field types (and some similar parameters). This makes sense because in both cases we need to ensure that each field handles the right types of data, is constrained to valid data, and has a description for display/documentation.

Form data is stored in an application's ```forms.py``` file, inside the application directory. 

***Form fields***

There are a lot of form fileds tayp but the arguments that are common to most fields are listed below (these have sensible default values):

- **required:** If True, the field may not be left blank or given a None value. Fields are required by default, so you would set required=False to allow blank values in the form.

- **label:** The label to use when rendering the field in HTML. If a label is not specified, Django will create one from the field name by capitalizing the first letter and replacing underscores with spaces.

- **label_suffix:** By default, a colon is displayed after the label. This argument allows you to specify a different suffix containing other character(s).

- **initial:** The initial value for the field when the form is displayed.

- **widget:** The display widget to use.

- **help_text:** Additional text that can be displayed in forms to explain how to use the field.

- **error_messages:** A list of error messages for the field. You can override these with your own messages if needed.

- **validators:** A list of functions that will be called on the field when it is validated.

- **localize:** Enables the localization of form data input.

- **disabled:** The field is displayed but its value cannot be edited if this is ```True```. The default is ```False```.

***Validation***

Django provides numerous places where you can validate your data. The easiest way to validate a single field is to override the method ```clean_<fieldname>()``` for the field you want to check. 

***URL configuration***

The URL configuration will redirect URLs with the format``` /catalog/book/<bookinstance id>/renew/``` to the function named ```renew_book_librarian()``` in ```views.py```, and send the BookInstance id as the parameter named ```pk```. The pattern only matches if ```pk``` is a correctly formatted ```uuid```.

***View***

The view has to render the default form when it is first called and then either re-render it with error messages if the data is invalid, or process the data and redirect to a new page if the data is valid. In order to perform these different actions, the view has to be able to know whether it is being called for the first time to render the default form, or a subsequent time to validate data. 

For forms that use a POST request to submit information to the server, the most common pattern is for the view to test against the POST request type ```if request.method == 'POST':``` to identify form validation requests and GET (using an else condition) to identify the initial form creation request. If you want to submit your data using a GET request, then a typical approach for identifying whether this is the first or subsequent view invocation is to read the form data.

- ```get_object_or_404():``` Returns a specified object from a model based on its primary key value, and raises an Http404 exception (not found) if the record does not exist. 
- ```HttpResponseRedirect:``` This creates a redirect to a specified URL (HTTP status code 302). 
- ```reverse():``` This generates a URL from a URL configuration name and a set of arguments. It is the Python equivalent of the url tag that we've been using in our templates.
- ```datetime:``` A Python library for manipulating dates and times. 

***Other ways of using form template variable*** 

We can also render each field as a list item (using``` {{ form.as_ul }}``` ) or as a paragraph (using ```{{ form.as_p }}```).

It is also possible to have complete control over the rendering of each part of the form, by indexing its properties using dot notation. 

## ModelForms

If you just need a form to map the fields of a single model then your model will already define most of the information that you need in your form: fields, labels, help text and so on. Rather than recreating the model definitions in your form, it is easier to use the **ModelForm** helper class to create the form from your model. This **ModelForm** can then be used within your views in exactly the same way as an ordinary Form.

***Generic editing views***

Django abstracts much of "boilerplate" by creating generic editing views for creating, editing, and deleting views based on models. Not only do these handle the "view" behavior, but they automatically create the form class (a ModelForm) for you from the model.

## Summary

Creating and handling forms can be a complicated process! Django makes it much easier by providing programmatic mechanisms to declare, render, and validate forms. Furthermore, Django provides generic form editing views that can do almost all the work to define pages that can create, edit, and delete records associated with a single model instance.
