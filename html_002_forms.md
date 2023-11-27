# HTML Forms

```html
      <h3 class="title">Forms</h3>
      <div class="content">
        <div class="subject">
          <form action="" method="">
            <p>Below is 'label' and 'input' with type '[text/email/tel]':</p>
            <label for="form_name">enter name:</label>
            <input type="text" name="name" id="form_name" placeholder="name" required>
            <br>
            <label for="form_email">enter email:</label>
            <input type="email" name="user_email" id="form_email" placeholder="email">
            <br>
            <label for="form_phone">enter phone:</label>
            <input type="tel" name="" id="form_phone" placeholder="phone number">
            <br>
            <p>Below is 'textarea':</p>
            <textarea name="" id="form_description" cols="30" rows="5" minlength="5" maxlength="20">This is a 'textarea' tag </textarea>
            <br>
            <p>Below is 'input' with type 'radio':</p>
            <input type="radio" name="color" id="" value="gold">Gold 
            <input type="radio" name="color" id="" value="silver">Silver
            <input type="radio" name="color" id="" value="bronze">Bronze
            <p>Below is 'input' with type 'radio':</p>
            <input type="radio" name="answer" id="" value="y">Yes
            <input type="radio" name="answer" id="" value="n">No
            <br>
            <p>Below is 'input' with type 'checkbox':</p>
            <input type="checkbox" name="sweet" value="kitkat" checked>kitkat
            <input type="checkbox" name="sweet" value="nutella">nutella
            <input type="checkbox" name="sweet" value="oreo">oreo
            <br>
            <p>Below is are radio buttons, made using label</p>
            <label for="light"> 
              <input id="light" type="radio" name="light-dark" value="light">light
            </label>
            <label for="dark">
              <input id="dark" type="radio" name="light-dark" value="dark">dark
            </label>
            <br>
            <div>
                <label for="quantity">Quantity</label>
            </div>
            <input type="number" id="quantity" name="quantity" min="1" value="0">
            <div>
            <!--Select+Option-->
            <p>Below is 'select' and in it 'option'</p>
            <select name="type" id="">
              <option value="magenta">magenta -'option'</option>
              <option value="magenta">pastel -'option'</option>
            </select>
            <br>
            <br>
            <!--Fieldset-->
            <fieldset>
              <legend>Using 'fieldset' as holding tag, while I'm a 'legend' tag.</legend>
              <input id="one" type="radio" name="items" value="one">
              <label for="one">Choice One</label><br>
              <input id="two" type="radio" name="items" value="two">
              <label for="two">Choice Two</label><br>
              <input id="three" type="radio" name="items" value="three">
              <label for="three">Choice Three</label>
            </fieldset>
            <br>
            <!--Date-->
            <label for="input1">Enter a date:</label>
            <input type="date" id="input1" name="input1">
            <br>
            <div>
                <label for="zip_code">Postal / Zip Code:</label>
            </div>

            <input type="text" id="zip_code" name="zip_code" pattern="(\d{5}([\-]\d{4})?)" required>
            <br>
            <button type="submit">Submit</button>
          </form>
        </div>
      </div>
```

<h3 class="title">Forms</h3>
<div class="content">
<div class="subject">
    <form action="" method="">
    <p>Below is 'label' and 'input' with type '[text/email/tel]':</p>
    <label for="form_name">enter name:</label>
    <input type="text" name="name" id="form_name" placeholder="name" required>
    <br>
    <label for="form_email">enter email:</label>
    <input type="email" name="user_email" id="form_email" placeholder="email">
    <br>
    <label for="form_phone">enter phone:</label>
    <input type="tel" name="" id="form_phone" placeholder="phone number">
    <br>
    <p>Below is 'textarea':</p>
    <textarea name="" id="form_description" cols="30" rows="5" minlength="5" maxlength="20">This is a 'textarea' tag </textarea>
    <br>
    <p>Below is 'input' with type 'radio':</p>
    <input type="radio" name="color" id="" value="gold">Gold 
    <input type="radio" name="color" id="" value="silver">Silver
    <input type="radio" name="color" id="" value="bronze">Bronze
    <p>Below is 'input' with type 'radio':</p>
    <input type="radio" name="answer" id="" value="y">Yes
    <input type="radio" name="answer" id="" value="n">No
    <br>
    <p>Below is 'input' with type 'checkbox':</p>
    <input type="checkbox" name="sweet" value="kitkat" checked>kitkat
    <input type="checkbox" name="sweet" value="nutella">nutella
    <input type="checkbox" name="sweet" value="oreo">oreo
    <br>
    <p>Below is are radio buttons, made using label</p>
    <label for="light"> 
        <input id="light" type="radio" name="light-dark" value="light">light
    </label>
    <label for="dark">
        <input id="dark" type="radio" name="light-dark" value="dark">dark
    </label>
    <br>
    <div>
        <label for="quantity">Quantity</label>
    </div>
    <input type="number" id="quantity" name="quantity" min="1" value="0">
    <div>
    <!--Select+Option-->
    <p>Below is 'select' and in it 'option'</p>
    <select name="type" id="">
        <option value="magenta">magenta -'option'</option>
        <option value="magenta">pastel -'option'</option>
    </select>
    <br>
    <br>
    <!--Fieldset-->
    <fieldset>
        <legend>Using 'fieldset' as holding tag, while I'm a 'legend' tag.</legend>
        <input id="one" type="radio" name="items" value="one">
        <label for="one">Choice One</label><br>
        <input id="two" type="radio" name="items" value="two">
        <label for="two">Choice Two</label><br>
        <input id="three" type="radio" name="items" value="three">
        <label for="three">Choice Three</label>
    </fieldset>
    <br>
    <!--Date-->
    <label for="input1">Enter a date:</label>
    <input type="date" id="input1" name="input1">
    <br>
    <div>
        <label for="zip_code">Postal / Zip Code:</label>
    </div>
<input type="text" id="zip_code" name="zip_code" pattern="(\d{5}([\-]\d{4})?)" required>
    <br>
    <button type="submit">Submit</button>
    </form>
</div>
</div>


## The form element

```html
<form action="example.com/path" method="post">

</form>
```

```action``` attribute takes a URL value that tells the form where it should send its data to be processed

```method``` attribute tells the browser which HTTP request method it should use to submit the form. The GET and POST request methods are the two you will find yourself using the most.

## Input

```html
<label for="first_name">First Name:</label>
<input type="text" id="first_name" name="first_name" placeholder="Alice...">
```

```type``` attribute which tells the browser what type of data it should expect and how it should render the input element.

Give our inputs a ```label``` to inform users what type of data they are expected to enter. Labels accept a ```for``` attribute, which associates it with a particular input. The input we want to associate with a label needs an ```id``` attribute with the same value as the label’s ```for``` attribute.

To guide users on what to enter in form elements, we can include ```placeholder``` text in input fields

We also need to let the backend, where we send our data, know what each piece of data represents.
We do this by adding a ```name``` attribute to our inputs

> To get a better understanding of what this looks like we can submit a form to http://httpbin.org/. This service will send back a response which will let us view what data was submitted

## Using form controls outside of forms

```html
<div>
  <label for="username">What's your name?</label>
  <input type="text"id="username">
  <button class="greet-btn">Greet Me</button>
</div>

<h1 class="greeting"></h1>
```

```js
const name = document.querySelector("#username")
const greetMeButton = document.querySelector(".greet-btn")
const greetingOutput = document.querySelector(".greeting")

greetMeButton.addEventListener('click', (event) => {
   greetingOutput.innerText = `Hello ${name.value}`;
})
```

## Submit and Reset

### Submit
```html
<button type="submit">Submit</button>
```

### Reset
```html
<button type="reset">Reset</button>
```

## Fieldset and Legend

<details>
<summary>Another Example</summary>

```html
<fieldset>
  <legend>What would you like to drink?</legend>

  <div>
    <input type="radio" name="drink" id="coffee" value="coffee">
    <label for="coffee">Coffee</label>
  </div>

  <div>
    <input type="radio" name="drink" id="tea" value="tea">
    <label for="tea">Tea</label>
  </div>

  <div>
    <input type="radio" name="drink" id="soda" value="soda">
    <label for="soda">Soda</label>
  </div>
</fieldset>
```

<fieldset>
  <legend>What would you like to drink?</legend>

  <div>
    <input type="radio" name="drink" id="coffee" value="coffee">
    <label for="coffee">Coffee</label>
  </div>

  <div>
    <input type="radio" name="drink" id="tea" value="tea">
    <label for="tea">Tea</label>
  </div>

  <div>
    <input type="radio" name="drink" id="soda" value="soda">
    <label for="soda">Soda</label>
  </div>
</fieldset>

</details>


## Styling Validations

```css
input {
  border: 2px solid #000;
  margin-bottom: 15px;
  padding: 5px;
  border-radius: 5px;
}

input:invalid:required {
  background-image: linear-gradient(to right, pink, lightgreen);
}

input:invalid {
  border-color: red;
}

input:valid {
  border-color: green;
}
```

## Regex

For the ```pattern``` attribute


- ```a``` — Matches one character that is a (not b, not aa, and so on).
- ```abc``` — Matches a, followed by b, followed by c.
- ```ab?c``` — Matches a, optionally followed by a single b, followed by c. (ac or abc)
- ```ab*c``` — Matches a, optionally followed by any number of bs, followed by c. (ac, abc, abbbbbc, and so on).
- ```a|b``` — Matches one character that is a or b.
- ```abc|xyz``` — Matches exactly abc or exactly xyz (but not abcxyz or a or y, and so on).
- ...

Example:
```html
pattern="[Bb]anana|[Cc]herry"
```

## With Javascript

https://www.w3schools.com/js/js_validation_api.asp

https://developer.mozilla.org/en-US/docs/Learn/Forms/Form_validation#validating_forms_using_javascript