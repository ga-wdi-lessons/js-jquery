# jQuery: Part I

## Learning Objectives

- Review how to select elements using Vanilla Javascript.
- Differentiate between a Javascript library and framework.
- Define the role that jQuery serves as a library
- Define what a CDN ("Content Delivery Network") is and how to use one.
- Use jQuery selectors to select DOM elements.
- Differentiate between DOM and jQuery objects.
- Explain when and how to use Vanilla JS vs. jQuery.
- Compare code examples in Vanilla JS and jQuery.
- Define `$(document).ready()` and some jQuery methods.

## Framing

jQuery is the world's most widely-used Javascript library. Its slogan is "write less; do more".

Which is easier to write?

```js
document.querySelectorAll(".hello")
$(".hello")
```

## Selecting DOM elements using Vanilla JS (20min)

Before we talk about jQuery, I want to make sure we're on top of our Javascript -- or as we'll refer to it today, "Vanilla JS" -- selectors.

If I want to select a DOM element using Vanilla JS, how would I do that?
- Q: Somebody demonstrate how to select all the `<p>` elements on a page.

Before we dive into the world of jQuery, let's make sure we've got our Vanilla JS selectors down pat with an exercise...

### Exercise: JS Selector Review (10min)

Follow along with "My Blawg": https://github.com/ga-wdi-exercises/my-blawg
- Clone: `$ git clone https://github.com/ga-wdi-exercises/my-blawg.git`
- Open: `$ open index.html`
- We'll be using this as an example throughout today's class.

### You Do: My Blawg, Part 1

We'll revisit this after talking about jQuery for a bit...  

## Intro to jQuery (10min)

### Javascript library
What is a library?
- Q: Has anybody used a JS library before?
- A collection of Javascript functions and methods that make writing Javascript an easier, smoother and ultimately shorter experience.
- Under the hood, all Javascript libraries are written using Javascript. So technically, there is nothing you can do using a library that can't already be done using Vanilla JS.
- There are tons of them: [https://www.javascripting.com/](https://www.javascripting.com/)
  - Some suited for particular uses like data visualization(D3.js), 3D imaging (Three.js), charts (Chart.js), autocomplete functionality (Typeahead.js) and many more...

Not the same thing as a Javascript framework.
- Not only provides tools like a library does, but also defines the architecture of your code (e.g., syntax, folder structure). Basically, a set of rules you have to follow.
- Examples: AngularJS, Ember.js.


Sometimes "library" and "framework" are used interchangeably, but they are not the same. The difference will be more apparent as you get some experience with both as the course progresses.  

### What is jQuery?
The "Write Less, Do More" JS library
- A general purpose library that provides an alternate and easier way to run Javascript.
- At its core, jQuery lets us select and manipulate DOM elements.
- Can also...
  - Manipulate CSS
  - Event listeners
  - AJAX
  - Animations

Like Javascript, jQuery works in all browsers.  

Because of all this, jQuery is the most popular JS library on the web.  

## Setting up jQuery (10min)

There are two ways to go about including jQuery on a website.
- In both cases, we include the jQuery script file (`jquery-2.1.4.js`) as we would our usual app.js file using `<script>`.
- Q: Where in our HTML should we include the `jquery-2.1.4.js` file?
  - How/when is Javascript processed by the browser?
  - Relative to the `<script>` that includes our `app.js` file?

### Download
- [https://jquery.com/download/](https://jquery.com/download/)
- Minified vs. Uncompressed
  - Minified
    - No whitespace, no comments, shortened variable names.
    - Q: Why would we want something minified?
      - Improve site load time.
      - If something goes wrong with your jQuery code, hard to debug since it's all on one line.
      - Used when a website is ready for production.
  - Uncompressed
    - Unmodified jQuery - can see it all!
    - Will use this in case we need to debug and take a look at what's going on under the hood.
    - Used when a website is in development.

### Import
You don't have to host jQuery yourself. You can pull it from the web via a Content Delivery Network (CDN).

What is a CDN?
- "Serve content to end-users with high availability and high performance."
- Broad term for a distributed system of servers -- sometimes spread across the world -- that serves content to users, whether that's videos, software or, in this case, a Javascript library.
  - In the case of jQuery, this CDN is usually Google.

Include with a `<script>` tag in HTML that links to some URL.
- Keep this handy: `<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.3/jquery.min.js"></script>`

## jQuery Selectors (20min)

The most basic concept of jQuery is to "select some elements and do something with them." Most jQuery looks like this:

```js
jQuery("h2").html("Hello");
```

This says "Select every `<h2>` and change its inner HTML to 'Hello'."

> If you've used jQuery before you've done it with a dollar sign. We'll talk about that in a minute.

Let's break it down:

- The selector: `jQuery( "h2" )`
  - Select a DOM element by its CSS selector.
  - jQuery runs the equivalent of `document.querySelectorAll()` on the DOM element you are selecting.
    - Q: What does `querySelectorAll()` do in Vanilla JS?
    - If you select an element of which there is more than one, jQuery will return all of them.
- Method: `.html()`
  - jQuery comes with tons of methods that we can use to traverse and modify the DOM, among other things.
  - In this example we're looking at `.html()`, which returns the HTML contents of a DOM object.
  - We'll go over a few today, and you'll go over a lot more of them with Andy during your second jQuery class.

### Wrap it in cash

Instead of writing `jQuery("h2")`, you can just write `$("h2")`. They do the same thing. Almost no-one writes `jQuery`.

`$` isn't a special character -- it's the name of a function. It returns a jQuery object.

I can create my own `$` function:

```js
function $(name){
  alert(name + " is wrapped in cash.");
}
$("Juan");
```

> Confusingly, Chrome has its own built-in `$()` function, which is completely unrelated.

We Do: What would `$( "h2" ).html();` look like in Javascript?

## The jQuery object

- `$("h2")` returns something that behaves like an array, but *isn't* an array
  - If I `console.dir(jQuery("h2"))` I can see that it has a bunch of extra properties
  - Getting things out of this not-quite-an-array is also a bit different

jQuery objects *look* like regular arrays or DOM elements, but they're very different

### You Do: jQuery vs DOM objects

Try the following snippets in your Chrome console. What's the difference between `[]` and `.eq()`?

```js
console.dir($("h2")[1]);

console.dir($("h2").eq(1));

console.log($("h2")[1].html());

console.log($("h2").eq(1).html());

console.log($("h2")[1].innerHTML);

console.log($("h2").eq(1).innerHTML);

console.log(document.querySelectorAll("h2")[1].innerHTML);

console.log(document.querySelectorAll("h2").eq(1).html());

console.log(document.querySelectorAll("h2")[1].html());
```

### You Do: My Blawg, Part 2

Reference: [https://api.jquery.com/](https://api.jquery.com/)

## jQuery vs. Vanilla JS (10min)

Q: Now that we've gone over jQuery for a bit, what are some reasons you think somebody would use jQuery over Vanilla JS?
- What about Vanilla JS over jQuery?

Easier
- Abstracts Vanilla JS into shorter, more concise and intuitive syntax
- Reduces development time
- ...but only if you're doing plenty of element selection and event handling!
  - Some people have a tendency to automatically include jQuery, regardless of what they're doing.
  - [needsmorejquery.com/](http://needsmorejquery.com/).

Speed
- Vanilla JS is faster. Only relevant, however, when dealing with large amounts of code.
- [http://www.sitepoint.com/jquery-vs-raw-javascript-1-dom-forms/](http://www.sitepoint.com/jquery-vs-raw-javascript-1-dom-forms/)

Make sure you're familiar with Vanilla JS and jQuery, but use whichever one you feel more comfortable with. Or use both!

Onto some jQuery methods!

## Getters and setters (10min)

Sometimes we want to select a particular aspect of a DOM element, like its HTML content or CSS properties.
- That's where jQuery's methods come in.

The jQuery methods we will be going over today are both "getters" and "setters".
- Q: Anybody want to guess what those two terms mean?
  - Getter: returns a value
  - Setter: sets/replaces a value
  - The version of the method that is triggered depends on how many arguments are fed into it.

### You Do: My Blawg, Part 3

## Event listeners

What does this do?

```js
$("h2").on("click", function(){
  console.log(this.innerHTML);
});
```

Why the following throw an error? How would I fix it?

```js
$("h2").on("click", function(){
  console.log(this.html());
});
```

Most event listeners have a jQuery method named after them.

Instead of writing `.on("click", function(){})` you can just write `.click(function(){})`;

## Document ready

What does this do?

```js
$(document).on("ready", function(){
  alert("Loaded!");
});
```

Code included inside `$( document ).ready()` will only run once the page Document Object Model (DOM) is ready for JavaScript code to execute.

**If your Javascript isn't working, the first thing to check is whether your code is wrapped inside `$(document).ready()`.**

Given this:

```js
$("h2").on("click", function(){

});

$("h2").click(function(){

});
```

...fill in the blank:

```js
$(document).on("ready", function(){

});

// Blank!
```

## Homework: Final Countdown

https://github.com/ga-wdi-exercises/final-countdown

## Other exercises

https://github.com/ga-wdi-exercises/atm

## References

- [Our own jQuery cheat sheet](./jquery-cheat-sheet.md)
- [The very thorough jQuery documentation](https://api.jquery.com/)
- [Download the jQuery documentation](http://www.jqapi.com/)
