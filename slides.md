---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# Assignment Presentation

Slide Presentation for Circle 7

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Controlling Forms In JavaScript
Forms are Key for user input and interaction in web development. In oder to create dynamic and interactive websites, it is important to understand how to work with forms using javaScript. In order to access forms using javascript, document.forms is being used. It is a named-collection which means you can access forms using both their names and index. We could create a form with javaScript using the createElement() method.
A form may have one or many fieldset elements inside it. They also have elements property that lists form controls inside them. The HTML fieldset element gets used to group several controls as well as labels (label) within a web form. We can access the Fieldset properties via the form.elements property.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->
---
transition: slide-up
level: 2
---
For example:
````
// create form element
const form = document.createElement('form');
form.id = 'form';
const fieldset = document.createElement('fieldset');
fieldset.name = 'fields';
// create a legend
const legend = document.createElement('legend');
legend.textContent = "Personal details";
// create input element
const input = document.createElement('input');
input.type = 'text'
input.id = 'name'

fieldset.appendChild(input, legend);
form.appendChild(fieldset);
document.body.appendChild(form);
````
---
---
# Referencing and Accessing Form Elements
In JavaScript, every element is linked to the form and can be accessed using the name or the index. For example:
````
<form>
<input type = "text" name = "user" />
</form>
<script>
// form → element
let user = form.user // targets the the name;

// element → form
console.log(user.form) //gets the form which the 'user' input belongs to;
</script>
````
---
---
# Form Properties
Form elements has different properties that allows us to interact with them programmatically.
For instance, you can use the "value" property to access and modify form elements like the input and textarea. Thi property could be a string (input.value) or boolean(input.checked), for checkboxes and radio buttons. Unlike the input and textarea elements, the select element has a wider range of properties you can use to interact with a form, these properties are as follows:<br>.option<br>.value<br>.selectedIndex.
---
---
# Focusing: focus/blur
Managing focus and blur events is crucial to a web developer when making forms and other input elements user friendly. This gives the developer control over what happens when a user clicks or hover over input fields like text-boxes, drop downs etc, thereby enhancing the user experience. Focus indicates that a user is ready to input data into a certain element. This focus is achieved when the element gains the attention of the user, especially when the user clicks or navigates their way to the element with a keyboard.  
---
---
# Blur
When a user moves away from an input element especially by clicking on another element, the previously focused element starts to blur. Blur event helps indicates that a user has finished interacting with a specific field. An example of the use case of the blur event is as follow: 
````
input.onblur = function(){
  if (!input.value.includes('@')) {
    input.classList.add('invalid');
    error.innerHTML = "Please enter a valid email";
  };
}
````
This example is an email validation where the input is blurred out when the user clicks outside the input field, indicating the end of interaction. 
---
---
# Form Events
## Change
A change event is an event that fires when there is a change in a form and the user has already finished interacting with the input field. In other form elements like checkboxes and  radio button, the change gets triggered as soon as the value is changed.

## Input
The input event doesn't require the user to finish interaction with the input field, instead, the event starts at the slightest modification. It ideal in scenarios where there is need for immediate feedback like showing the password strength or live search.
---
---
## Cut, Copy and Paste
The cutting, copying and pasting operations are handled by these events. They are part of the clipboardEvent class that gives access to the clipboard's contents. The event.clipboardData objects provides access to the data being cut, copied or pasted and this behaviour can be prevented using event.preventDefault().
````
<input type="text" id="myInput" placeholder="Try copy, cut or paste here">
<script>
const input = document.getElementById("myInput");

// Copy event
input.addEventListener("copy", function (event) {
  alert("You copied text from the input!");
});

// Cut event
input.addEventListener("cut", function (event) {
  alert("You cut text from the input!");
});

// Paste event
input.addEventListener("paste", function (event) {
  alert("You pasted text into the input!");
});
</script>
````
---
---

# Form Submission Events and Methods
Form submission allows users to input data and send it over to the server for processing and in JavaScript, there are two ways to handle form submissions.<br>
- The submit event<br>
- The form.submit() method<br>
## The Submit Event
The submit event gets triggered the moment a form is submitted. it is used to validate form data before it gets sent to the server or to prevent the default submission behavior and handle it with JavaScript instead.
### How is the submit event triggered?
The submit events get triggered when the user submits a form by either clicking submit or pressing the enter button while focused on an input field within the form.
---
---

## Code Example For The Submit Event

````
<form id="myForm">
  <input type="text" name="username" placeholder="Enter your name" required>
  <button type="submit">Submit</button>
</form>

<script>
const form = document.getElementById("myForm");

form.addEventListener("submit", function (event) {
  event.preventDefault(); // Prevents page from reloading
  alert("Form has been submitted!");
});
</script>
````
This code above is used to validate input before submitting data.<br><br>
Apparently, pressing enter to submit a form simulates a click event even when no click actually occurred.
---
---
## The <kbd>form.submit()</kbd> Method
WHen a developer programmatically submit a form without user interaction, the form.submit() method is used. This method is used in scenarios like, surveys, or sign-up wizards, where each steps submits partial data silently without the user noticing.<br>
Code example:
````
function createForm() {
const myForm = document.createElement('form');
myForm.method ='POST';
myForm.action = '/api/submit';

// create input element
const Input = document.createElement('input');
Input.type = 'text';
Input.name = 'username';
Input.value = 'Amarachi Ezendu';

myForm.appendChild(Input);
document.body.appendChild(myForm);

myForm.submit();
}
createForm();
````
---
---
# Form Validation
It is crucial that data submitted by users is accurate and secure and in order to ensure this, web developers use form validation.<br>
There are three important aspects of form validation:<br>
- The novalidate Attribute
- HTML validation Attributes
- Constraint VAlidation API
---
---
## The novalidate Attribute
When a web developers wants to implement custom validation logic, or use JavaScript library for form validation, they use the novalidate attribute to disable the browser's default validation behavior. <br>
NB: Iy is used on the form element<br>
For example
````
<form novalidate>
<label for="email">Email:</label>
<input type="text" id="email" required />
<button type="submit">Submit</button>
</form>
````
Even though the "required" attribute is used on the input type="email" the browser will not perform the default validation when the form is submitted because of the novalidate attribute.
---
---
## HTML Validation Attributes
These are special attributes added to form elements  to ensure that the user enters valid data before the form can be submitted. They prevent incomplete or incorrect form inputs without involving JavaScript. These attributes include:<br>
- Required
- Minlength/maxlength
- Min/max
- Pattern
- Type
- Step
- Readonly
- Disabled
---
---
Example:
````
<form>
  <input type="text" required minlength="3" maxlength="10" placeholder="Username" />
  <input type="email" required placeholder="Email" />
  <input type="number" min="1" max="100" />
  <input type="submit" />
</form>
````
## Constraint Validation API
The Constraint Validation API is a set of JavaScript properties and methods that lets developers interact with HTML form validation. It allows developers to:<br>
- Check if a form or input is valid
- Trigger validation manually
- Get validation error messages
- Customize or override validation behavior.
---
---
## CONT'D
The Constraint Validation APIs include:
- validity
- validationMessage
- willValidate
- checkValidity()
- reportValidity()
- set customValidity()
---
---
Example
````
<form id="myForm">
  <input id="username" type="text" required minlength="3" />
  <button type="submit">Submit</button>
</form>

<script>
  const form = document.getElementById('myForm');
  const input = document.getElementById('username');

  form.addEventListener('submit', function (e) {
    if (!input.checkValidity()) {
      input.setCustomValidity("Username must be at least 3 characters!");
      input.reportValidity(); // Show the message
      e.preventDefault(); // Stop form from submitting
    } else {
      input.setCustomValidity(""); // Clear custom message
    }
  });
</script>
````
---
---
# THE END
---