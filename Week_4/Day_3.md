# Ajax

# Asynchronous Javascript and XML (eXtensible Markup Language)
- Industry turned to JSON now, no more XML

## Make HTTP requests (an receive responses) without refreshing the browser
- Get back raw data instead of html page (no presentation)
- Do rendering on the client side with jQuery

### XMLHttpRequest XHR (go read MDN)
- We use jQuery to do it
- If you JSON.parse something that is already parse, you will get a token error

### For API that takes callback/ promise
- It evaluate if callback is true, if not, just return a promise

```js
// This is the long form
$.ajax({
  url: '/products',
  method: 'GET/POST/PUT/PATCH/DELETE',
  dataType: 'JSON',
  success: (response) => {},
  error: (err) => {}
})

$.post()
$.get()
$.getJSON()

```

#### Integrete
- A hash from CDN to valid the resource, security purpose
- You can delete it, no recommanded, but it works anyway


#### Make sure JS load after DOM ready
- You are declare your func outside of the callback
- Only invoke (call) them inside the callback

```js
$(document).ready(()=>{});

// retreive the data via AJAX
$(()=>{
  $.ajax({
  url: '/products',
  method: 'GET/POST/PUT/PATCH/DELETE',
  dataType: 'JSON',
  success: (response) => {},
  error: (err) => {}
  })
});

```

Under Network Tap, XHR, will see your Ajax request & response

```js
sucess:(recipes) => {
  console.log(recipes);
  const $ul = $('#recipes'); // <= put it here instead!
  // iterate through the array
  for (const recipe of recipers) {
    // $('li') <= query for this element
    // $('<li>') <= create an empty element <li></li>

    // turn each object into an LI
    const $li = $('<li>').text(recipe.title);  // <li>recipe.title</li>

    // the $ at front, semantic! tell other dev it's a jQuery obj
    // hungarian notation (Wiki)
    // append each LI to the UL in the DOM
    // we need somewhere to attached the element we created! In the DOM!
    // make an anchor point! container? ul?

    const $ul = $('#recipes'); // <= we can pull it out of the for-loop, while inside the document ready, to make it run faster
    $ul.append($li) // last child, like arr.push()
    $ul.prepend($li) // first child, like arr.shift()

  }

},


```

#### Ajax with Promise instead of Callback
- jQuery.getJSON(url, [,data][,success (callback)])
- We gonna not use the callback, so it returns a promise
```js

(()=>{
  $ol = $('#ingredient')
  $.getJSON('http://xxxxxxx')
    .then((ingredients) => {
      console.log(ingredients);
      for (const ingredient of ingredients) {
        const $li = $('<li>').text(ingredient.name);
        $ol.prepend($li);  // reverse order!
      }
    })
})


```
#### Base URL
- the url that is not changing, put it to the top of the file
const BaseURL = http://my-json-server.xxxxxx
```js
$.getJSON(`${baseURL}/recipes`)
  .then((recipes)=>{

  })


```

#### POST with Ajax & jQuery
- jQuery.post(url [,data][,success])
- form/ input without method/ action on the html
- because we are submitting from Ajax

```html
<form id="new-recipe form">
  <label for="new-recipe">New Recipe:</label>
  <input id="new-recipe" name="new-recipe" />
  <button type="submit">Save!</button>
</form>
```
- serialize()

```js
const $form = $('#new-recipe-form');

// $form.submit()
$form.on('submit', (event) => {
  event.preventDefault();
  const serialized = $(this).serialize(); // $form.serialize();
  console.log(serialized);

  $.post(`${baseURL}/recipes`, serialized)
    .then((recipe)=> {
      console.log(`server response: ${response}`)
    })

})


```




``` js
const ingredientPromise = $.getJSON(`${baseURL}/ingredients`);
const recipePromise = $.getJSON(`${baseURL}/recipes`);

const promises = [ingredientPromise, recipePromise];

Promise.all(promises) // it only takes an array, it starts it all at the same time
  .then([arrResult]/*the exact order as the promise arr*/=>{
    const ingredients = arrResult[0];
    const recipePromise = arrResult[1];
    etc ...
  })

```