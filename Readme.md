---
tags: cssi, javascript, jquery
level: 2
languages: javascript
---
#jQuery Basics

The jQuery library provides hundreds of methods for interacting with an HTML page. If you are looking for something in particular, check out the [jQuery Cheatsheet](http://oscarotero.com/jquery/) and look for what you want to do.

You will practice the essential methods in this prework, but don't worry about memorizing - you'll always be able to look up the syntax when you need to.

## JQuery - Selection and the DOM
In order to do anything with jQuery, we first need to be able to navigate the DOM. You can select all elements that match a certain criterion using the following  jQuery syntax:  

```js
$(selector).action()
```

* The selector is the criterion you are matching against - the selector can query for HTML elements, CSS classes or ids, or select the entire document.
* The `$` indicates that that .action() is a method found in the jQuery source file.

The following code would hide all paragraph tags. In fact, if you open up the JavaScript console, and paste that code in you'll see the tweets disappear. Using the jQuery method, `show()`, you can quickly resurrect those tweets.

```javascript
$("p").hide();
```


Some examples of jQuery selector syntax:


|CSS/HTML          |jQuery           |Selected        |
|---          |---              |---             |
|p            |$('p')           |All the paragraph elements|
|div          |$('div')         |All the div elements|
|.button      |$('.button')     |All elements with class=”button”|
|#headline    |$('#headline')   |The element with id=”headline”|
|.code strong |$('.code strong')|all of the strong elements with parent elements with the class="code"|
|header nav li.home|$('header nav.home')|All the li elements inside navs inside headers with the class home'|

##Filtering
jQuery has some great methods for choosing the particular elements you want from a set of them. For example `first()` and `last()` will select the bookends within your subset while `.eq(index)` will select the element at a certain index. You should chain methods by first filtering the elements, then applying the action to them.

The code below selects the fifth tweet and changes the text within.

```js
$( "p" ).eq( 5 ).text('Make Love Not War')
```

##DOM Traversal(Movement)
Sometimes the element you select doesn't have a handy id or class to easily fetch it with jQuery. This is where jQuery's `children()`, `parent()`, and `siblings()` functions come in.

It's a lot easier to talk about parents/children/siblings when you can actually see the markup so for this section, we'll be refering to the HTML below:

```html
<h1>The Onion</h1>
<div id="content">
  <div class="article">
    <h2>Dolphin Spends Amazing Vacation Swimming With Stockbroker</h2>
    <p><strong>ORLANDO, FL</strong> - Describing the encounter as a once-in-a-lifetime experience she'll never forget, local bottlenose dolphin Hazel reportedly recounted stories Tuesday from a recent vacation in which she got to go swimming with a stockbroker.
    </p>
  </div>
  <div class="article">
    <h2>Archaeological Dig Uncovers Ancient Race Of Skeleton People</h2>
    <p><strong>ORLANDO, FL</strong> - Describing the encounter as a once-in-a-lifetime experience she'll never forget, local bottlenose dolphin Hazel reportedly recounted stories Tuesday from a recent vacation in which she got to go swimming with a stockbroker.
    </p>
  </div>
</div>
```

The two `.article` divs are children of the `#content` div.

![call children on content](http://web-dev-readme-photos.s3.amazonaws.com/js/more-on-jquery/call-children-on-content.png)

The first `.article` div's parent is the `#content` div.

![call parent on article](http://web-dev-readme-photos.s3.amazonaws.com/js/more-on-jquery/call-parent-on-first-article.png)

The first `.article` div has two children: an H2 and a paragraph.

![call children on first article](http://web-dev-readme-photos.s3.amazonaws.com/js/more-on-jquery/call-children-on-first-article.png)

DOM elements that exist at the same level in a div, for instance, h2 and the paragraph, are called siblings. The article divs are also siblings.

![call siblings on first article](http://web-dev-readme-photos.s3.amazonaws.com/js/more-on-jquery/call-siblings-on-first-article.png)

These three methods, `children()`, `parent()`, and `siblings()`allow you to select an element that may not have any distinguishing characteristics, such as an id or a specific class.





##Adding and Removing Elements
You can use jQuery to add an element dynamically with `append()` or remove and element with `remove()`.

```
$('#my_list').append("<li>New element</li>")
```
And to remove an element:
```
$('#elementToRemove').remove()
```


## JQuery and CSS
In addition to modifying HTML, JQuery also works to change the style of a page. Here are some methods you can use to edit your CSS with JQuery:

* addClass() - Adds one or more classes to the selected elements
* removeClass() - Removes one or more classes from the selected elements
* toggleClass() - Toggles between adding/removing classes from the selected elements
* css() - Sets or returns the style attribute

To add an id, you can use the attr() method and pass id and the name of the id as parameters:
```js
$('h2').first().attr('id', 'big_headline');
```
