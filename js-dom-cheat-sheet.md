# Javascript DOM Cheat Sheet

## Learning Objectives
- Use Javascript to:
  - select elements from the DOM
  - get & modify elements/content in the DOM
  - add elements to the DOM
  - remove elements from the DOM
  - respond to events on the DOM
  - loop through jQuery objects using the `each()` method

## Setup
Create 2 files we'll need:

```bash
$ touch index.html
$ touch script.js
```

in `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Document</title>
  </head>
  <body>
    <h1>If you can see this in your browser, your Javascript is not working!</h1>
    <script src="script.js"></script>
  </body>
</html>
```

In `script.js`:

```js
document.addEventListener("DOMContentLoaded", function(){
  document.querySelector('h1').textContent("If this wasn't in document.ready, it wouldn't work.");
  for(var i = 0; i < 10; i++){
    document.body.appendChild("<div class='awesome'>What a great div!</div>");
  }
});
```
## Selecting elements

- `document.querySelector()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
  - returns first element that matches the specified selector or group of selectors. Where the selectors used are any CSS selector as a string (tagNames, classes, Ids)

  ```js
  var el = document.querySelector('.myClass')
  ```

- `document.querySelectorAll()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)
  - returns an array of all of the elements that match the specified selector or group of selectors. Where the selectors used are any CSS selector as a string (tagNames, classes, Ids)

  ```js
  var matches = document.querySelectorAll('div')
  ```


## Get/Modify content

- _element_`.innerHTML()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
  - get or set the HTML contents **can also be used to add HTML elements**
  - get: no argument, know that it returns everything between the tags of the specified element

  ```javascript
  var currentContent = element.innerHTML
  // currentContent contains all of the elements children
  ```

    - set: one argument that you want the html content to be

  ```javascript
  element.innerHTML = newContent
  // removes all of the elements children and replaces with whatever newContent is
  ```

- _element_`.textContent` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
  - similar to innerHTML except that it will not turn markup into elements and will keep strings intact

  ```javascript
  var text = element.textContent;
  // returns the content of the selected element as a string, and store it in the variable `text`
  element.textContent = newContent;
  // removes all of the elements children and replaces with whatever newContent is
  ```

- _element_`.style.<propertyName>` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)
  - used to set and modify CSS properties, where `<propertyName>` is the name of the desired CSS attribute to get or set

  ```js
  var currentValue = element.style.backgroundColor;
  // will return what the current backgroundColor of the selected element, and store it in the variable `currentValue`

  element.style.height = someNewValue;
  // will set the height of the selected element to whatever someNewValue is
  ```

Add an input tag to the `index.html`:

```html
<input type="text" class="search" placeholder="some text here ....">
```

- _element_`.value` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement)
  - only works for input tags - gets current value in the input

> We need to be able to get information from users. Input tags are a great way to do that. But more importantly we need to be able to access those values so that our JS can act on it. Think about auto complete on search forms. As we type something into google, it starts giving us options. For every key stroke we make, the callback that is fired is probably using some form of `.value`. This will also be extremely important moving forward in week 7 with AJAX.

## Adding content

- `document.createElement(tagName)` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
  - creates the specified HTML tag

  ```js
  var element = document.createElement('div');
  // will return a created div and store it in the variable element
  ```

- `element.appendChild()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)

- `element.insertBefore()` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore)

  > Think about how facebook statuses work. When we add a new status, does it go to the bottom of the list? or is it right at the top? Maybe they're using a prepend here ...

## Removing content

- `element.removeChild()`

- `element.innerHTML = ''`

## Responding to events

- `element.addEventListener('event', callbackFn)`
  - a way to create event listeners
  - takes two arguments normally
    - first argument is the event(lots of them)
    - second argument is the callback

    ```javascript

    ```

> What is `$(this)` here? Refers to the jquery object you called `.on` on, as long as you're in the scope of the `.on` function

### Other

- `element.className` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Element/className)

- `element.setAttribute` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Element/setAttribute)

- `element.children` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/ParentNode/children)

- `element.parentNode` [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Node/parentNode)
