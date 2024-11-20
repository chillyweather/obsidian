# Forms

It's better to organize our form elements into groups. For example, the street, city, and country fields make up an address, so it's natural that these fields should be grouped together. To create such groups, we have the `<fieldset>` element.

```html
<form> 
	<fieldset class="form__contact-info"> 
		<!-- form element for user contact information --> 
	</fieldset> 
	<fieldset class="form__delivery-info"> 
		<!-- and this one is for delivery time and address --> 
	</fieldset> 
</form>
```

In order to get information from the user, a form must contain some input fields. In most cases, these fields are created using the `<input>` element. Like the `<img>` element, the `<input>` element does not require a closing tag. Usually, when dealing with `<input>`, it doesn't matter what type of information you're expecting a user to enter in a field. Whether it be a phone number, name, or even a file, the `<input>` element will be sufficient to collect the necessary data.

![[Pasted image 20210725173626.png]]

```html

<input type="text">
<!-- For text -->
        
```

```html

<input type="number">
<!-- For numbers. On a mobile device,
the user will see a numerical pad when
they tap on this field. -->
        
```

```html

<input type="email">
<!-- For an email address. The browser
will automatically check if the field has
a period and an @ symbol, both of which are
required for any email address -->
        
```

```html

<input type="password">
<!-- For passwords. Instead of showing the
user input, the field displays the entered
symbols as * or • (asterisk or bullet) -->
        
```

```html

<input type="tel">
<!-- For phone numbers. Just like with
the "number" field, the user will see a
numerical keypad. -->
        
```

```html

<input type="url">
<!-- For a website address -->
        
```

```html

<input type="range">
<!-- Creates a slider that can be moved
between a minimum and maximum value -->
        
```

```html

<!-- Input fields for time and date in different formats: -->
    
```

```html

<input type="date">
<!-- date without time: 07/03/2009  -->
          
```

```html

<input type="datetime-local">
<!-- date with time: 04/10/1957 22:28 -->
        
```

```html

<input type="month">
<!-- year and month: 1988-11 -->
        
```

```html

<input type="week">
<!-- year and week: 2018-W45 -->
        
```

```html

<input type="time">
<!-- time: 03:14 -->
        
```

### Disabling fields
```html
<input type="submit" disabled>
```

### Min and Max values
```html
<input type="range" min="-20" max="500">
<input type="number" min="1970" max="2025">

<!-- The interval is 10 -->
<input type="range" min="20" max="50" step="10">
```

### Upload, Reset, Submit

```html
<input type="file"> <!-- this field allows you to upload files -->
```

```html
<form>
  <input type="text">
  <button>Submit</button>
</form>
```

There are three types of buttons:

1.  The first type is used to submit a form to the server. When you click on this type of button, it fires the `submit` event.
2.  The second type will reset the input fields. When this type of button is clicked, the `reset` event will fire and your form will clear anything you've typed.
3.  The third type is simply `button`. There's no default behavior for this type of button, so you can set it up to do whatever you want.

```html
<button type="submit">Submit</button>
<button type="reset">Reset form data</button>
<button type="button">Do something</button>
```

###### Textarea
in cases where you expect the user to enter a larger amount of text, like a paragraph or more, it's best to use the `<textarea>` element.
```html
<textarea></textarea>
```

###### Select
creates a drop-down list where each option is wrapped by `<option></option>` tags:
```html
<select>
  <option>Item 1</option>
  <option>Item 2</option>
</select>
```

###### Labels
```html
<label for="first-name">First name</label>
<input type="text" id="first-name">
<label for="last-name">Last name</label>
<input type="text" id="last-name">
```

###### # Submitted Values
You can also manually set a `value` attribute for regular text fields which will be sent to the server if the user doesn't enter any information themselves:
```html
<input type="text" name="firstname" value="No name entered">
<select name="search">
    <option value="google">Google</option>
    <option value="some-search">Another search engine</option>
</select>
<input type="submit" value="Submit the form now">
```

### Checkboxes and Radio Buttons

```html
<input type="radio"> <!-- a single choice field (radio button) -->
<input type="checkbox"> <!-- a multiple choice field (checkbox) -->
```

```html
<h2>Choose genres:</h2>
<label for="rock">Rock</label>
<input type="checkbox" name="genre" id="rock" value="rock">
<label for="pop">Pop</label>
<input type="checkbox" name="genre" id="pop" value="pop">
<label for="hip-hop">Hip hop</label>
<input type="checkbox" name="genre" id="hip-hop" value="hip-hop">
<label for="techno">Techno</label>
<input type="checkbox" name="genre" id="techno" value="techno">
```

By giving our radio buttons identical values for the `name` attribute, the radio buttons will be linked and the user will be restricted from selecting multiple options:

```html
<label for="yes">Yes</label>
<input type="radio" name="choice" id="yes" value="yes">
<label for="no">No</label>
<input type="radio" name="choice" id="no" value="no">
```

By default, all radio buttons and checkboxes are inactive when the page loads. You can change this by adding the `checked` attribute, which doesn't require a value. Simply write it inside the `<input>` element, and the element will become active. By doing this, we'll be able to set up a choice that is selected by default whenever users first encounter our form with checkboxes or radio buttons:

```html
<input type="checkbox" name="music" checked>
<input type="radio" name="choice" checked>
```

### Placeholders

```html
<input type="text" name="firstname" placeholder="John Doe">
```


### Required Fields

```html
<input type="text" required>
```

#### Notes...
There are certain styles that an input field doesn't inherit from its parent element by default. This includes font styles, so regardless of whether you apply a font to the form as a whole, the default browser styles will be applied to the input fields unless you explicitly specify otherwise. To make sure that a certain style is inherited, you can assign the `inherit` value to its property name:

```html
 input {
   font-family: inherit; 
   /* Now the input field inherits the font of its parent */
 }
```

Псевдо-класс для активного поля формы:

```css
input:focus {
    /* styles for the active field */
}
```

На случай если хочется поменять дефолтные установки:

```css
input:focus {
    outline-color: yellow;
    outline-style: dashed;
    outline-width: 3px;
}
```

### Post data to server
```html
<form action="link to the handler" method="POST">
```

## Resources
[Documentation on the input element](https://www.w3.org/TR/html52/sec-forms.html#the-input-element)

[Styling web forms](https://developer.mozilla.org/en-US/docs/Learn/Forms/Styling_web_forms)

[83 HTML and CSS checkbox examples](https://freefrontend.com/css-checkboxes/)

[Guide to HTML forms](https://www.freecodecamp.org/news/a-step-by-step-guide-to-getting-started-with-html-forms-7f77ae4522b5/)

[How to style `<input type="range">`](https://css-tricks.com/styling-cross-browser-compatible-range-inputs-css/)

[Styling a drop-down list](https://24ways.org/2019/making-a-better-custom-select-element/)