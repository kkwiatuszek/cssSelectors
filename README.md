# cssSelectors
A css selectors guide for test automation




## Class
### dot preceding a string
If html element has a class attribute, like ``<ul class="example">`` then css selector, that will find all elements with this class is  ``.example``. If class name is long and contains spaces, we can use just part of the class value, for example for ``<ul class="VeryLongExample AnotherOne OneMore">`` we could use just ``.VeryLongExample``.

**!** There could be more than one element with the same class.

## Id
### hash preceding a string

If html element has id attribute, like ``<div id="example"></div>`` then css selector, that will find all elements with this class is `#example`.
<br>
**!** There should be only one element with given id, so it is the easiest way to find a single element. If an element you want to find has an id, then use it.


## Html element
Examples of html elements could be:
- div - container for other html elements
- a - link
- img - image
- span - part of a text
- table: 
  th - table header
  td - table cell
  tr - table row
- input - could be a textbox or a button (submit)
- button - clickable button
- ul - list


## Combining html elements
In some cases you would need to combine multiple html elements to find what you need. Then just use <css selector> <space> <css selector> . Examples:

```
<span>Cheese</span>
<div>
    <span>Burger</span>
</div>
```
We want to select element "Burger". 
- ``span`` would find two elements, both "Cheese" and "Burger".
- ``div span`` would find "Burger" (span "Burger" is inside div).

```
<span class="Cheese">Bacon</span>
<div>
    <span>Burger</span>
    <span class="Cheese">Fries</span>
</div>
```

We want to select element "Fries". 
- ``div span`` would find two elements - "Burger" and "Fries". 
- ``.Cheese`` would find two elements selected, as there are two Cheese classes. 
- ``div .Cheese`` would find "Fries".

```
<span class="">Bacon</span>
<div>
    <span>Burger</span>
    <span class="Cheese">Fries</span>
    <div>
        <span class="Cheese">Nachos</span>
    </div>
</div>
```
We want to select "Nachos". 
- ``div span`` would find three elements: "Burger", "Fries" and "Nachos"
- ``.Cheese`` would find two elements: "Fries" and "Nachos"
- ``div span.Cheese`` would find two elements: "Fries" and "Nachos"
- ``div div span`` would find "Nachos".

## Attribute
### [attribute=value]
If an html element from "html element" examples have a value, like ``<div class="example"></div>`` then we can use attribute and value in square brackets to find this element. So for given example, we can use ``[class="example"]`` to find this element. Examples:

```<div></div>``` - this is empty html element. Everything that is added, is an attribute:
- ``<div class="lemonade"></div>`` - class is an attribute with value "lemonade"
- ``<div id="tea"></div>`` - id is an attribute with value "tea"

To find first element with attribute we could use ``.lemonade`` or ``[class="lemonade"]``. 
To find second element with attribute we could use ``#tea`` or ``[id="tea"]``.
<br>


## Attribute that contains value
### [attribute*=value]
If we have a case, where css attribute has a value that is dynamic (so could change) or very long, we could use * to match value. For ``<div class="example with a very long value that1234 is auto111generated0000"></div>`` we can use ``[class*="example"]`` -> this will match every class, that CONTAINS "example"
<br>
## Test id
### [data-testId=value]
In a perfect world, when there is no unique class or id available, the best solution is to add ``data-testId`` attribute to the website. This can be done by a developer or a QA. This has another advantage - when a developer is changing UI, seeing data-testId he/she knows that this is used in a unit or e2e tests. 
<br><br>

## How to check if my selector will work?
<br>
When looking for a css selector, you should use developer tools available in the browser. When you are on the "Elements" tab, click cmd+F or control+F and small search box should appear at the bottom. If you enter there a valid css selector, it will be highlighted. It also shows how many elements match a given selector.  <br><br>
**Remember, there should be only one!**

## Resources

I recommend w3schools website: https://www.w3schools.com/cssref/css_selectors.asp
