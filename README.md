# CSS - An Introduction

## Lesson Objectives - I Will Be Able To (IWBAT)...

- [Define CSS and describe its use](#define)
- [How to add CSS rules to your app](#rules)
- [Diagram the structure of CSS](#diagram)
- [Demonstrate how to apply rules to a specific tag](#demonstrate)
- [List some common element properties that can be styled](#list)
- [Describe ids and classes. Explain when should we use which](#ids-and-classes)
- [Describe "The Cascade"](#cascade)
- [Describe how to combine various selectors](#combine)
- [Describe Specificity](#specificity)
- [Conclusion](#conclusion)

<br>

## <a name="define">Define CSS and describe its use</a>

**QUESTION**: Can anyone describe CSS for us?

HTML gives our site structure, but it doesn't do much in terms of how the site looks.  This is where CSS comes in. CSS stands for:

- **Cascading** - We'll Define shortly
- **Style** - making things pretty!
- **Sheets** - it's just a sheet of text, not a program we write

<br>

## <a name="rules">How to add CSS rules to your app</a>
There are 3 ways to add CSS style rules to your app:

- **A separate CSS file** - This is the best practice. It allows multiple HTML pages to access a single file and share same set of CSS rules. You'll add a link to the CSS file in the `head` of your HTML page.

```html
<html>
	<head>
		<link rel="stylesheet" type="text/css" href="mystyle.css">
	</head>
	<body>
		
	</body>	
</html>	
```


- **`<style></style>` tags** - You can add CSS rules to your HTML by adding `style` tags to the `head` of your HTML page. The rules would only be accessible by that HTML page.

```html
<html>
  <head>
    <style>
	  p {
		  color: red
		}
	</style>
  </head>
  <body>
		
  </body>	
</html>	
```  
	
- **Inline styling** - This is when you add CSS rules directly to the HTML element. It's the least preferred way to write CSS. 

```html
<p style="color: red">Hello World!</p>
```

<br>

![](http://i.imgur.com/2BtC2Zx.gif)

What are 3 ways to add CSS rules to your page? Which is the best practice?

<br>

## <a name="diagram">Diagram the structure of CSS</a>

A CSS file is composed of many rules.  Each rule governs the appearance of certain elements.  The generalized form looks like:

```css
selector {
	property:value;
	property:value;
	property:value;
}
```

 Everything inside the curly braces is called the "declaration block"

<br>


![wedo](http://i.imgur.com/6Kce0ca.png)

Let's code along and set up our Cloud9 workspace.

<br>

![](http://i.imgur.com/2BtC2Zx.gif)

What are the 3 components of a CSS rule?

<br>


## <a name="demonstrate">Demonstrate how to apply rules to a specific tag</a>

If you wanted to style all the `<p>` tags of a page, you could style it by writing:

```css
p {
	property:value;
	property:value;
	property:value;
}
```

<br>

## <a name="list">List some common element properties that can be styled</a>

Here are some properties that you can set for an element

####color
	
- names
	- blue, red, yellow, white, grey, black, green, orange, purple
	- http://www.crockford.com/wrrrld/color.html
- value
	- hexidecimal number (0-F), six places
		- `#0088FF`
	- https://color.adobe.com

#### background
- color
- url()

#### font-size
- measured in px (for now)
 
#### font-family
- System fonts
	- Single word fonts
		- Arial, Courier, Times, etc
	- Multi word fonts must be placed in quotes
		- "Times New Roman", "Arial Black", "Lucinda Console"
	- Use http://www.cssfontstack.com/ to see what fonts are available on what operating systems
- Generic fonts
		- serif, sans-serif, cursive, fantasy, monospace.
	- can have several font families as a value
		- starts with first and goes down the line until it finds one it has

#### font-weight
- normal, bold

#### text-align
- left, right, center

![Imgur](http://i.imgur.com/ylb6WX9.gif)


- Create an html page with a `p` tag and some placeholder text
2. Change its text color to a hex value that you choose from http://color.adobe.com
3. Give it a background color
4. Make the size of the text larger
5. Change its font family to a sans-serif font
6. Make the text bold
7. Center the text


<br>

## <a name="ids-and-classes">Describe ids and classes. Explain when should we use which.</a>

Sometimes just targeting an element is not enough.  We can target other attributes of elements in our selectors.

#### ids
- `<div id="left-column"></div>`
- `#left-column {}`
- each id on a page must be unique
- great for locations on a page that occur only once
	- e.g. left column, contact form, etc

#### classes
- `<div class="large-module"></div>`
- `.large-module {}`
- each class on a page does not have to be unique
- great for repeatable ideas
	- module
		- e.g. ad unit, comment block, etc
	- function
		- e.g. active, important,etc

![Imgur](http://i.imgur.com/ylb6WX9.gif)


- Add two more `p` tags.
2. Give one `p` tag an id
3. Give the other two `p` tags the same class
4. Use just the ids and classes to style `p` tag with the id differently from the ones with a class


<br>

## <a name="cascade">Describe "The Cascade"</a>

Some properties of elements are passed down to their children. In general:

- Properties dealing with text are inherited by their children
- Properties dealing with spacing are not inherited by their children
- https://www.w3.org/TR/CSS2/propidx.html

<br>

![Imgur](http://i.imgur.com/ylb6WX9.gif)


- Create a `p` tag within a `section` tag
2. Put some text in the `section` tag, but outside the `p` tag
3. Put some text in the `p` tag
4. Style just the `section` tag to give its text some color
5. Note that the `p` tag has also been affected

<br>

## <a name="combine">Describe how to combine various selectors</a>

Selectors can be more complex than just an element, id, or class.

- You can have a set of rules affect multiple sections by listing them
	- `p, #left-column {}`
		- will style all `<p>` tags and whichever tag has and id of "left-column"
1. You can combine attributes (i.e. tag, class, id) to narrow down how many elements are effected
	- `a.important {}`
		- styles all anchor tags that also have an "important" class
			- `<a class="important"></a>`
	- `#left-column.visible {}`
		- styles whichever tag that has the id of "left-column", but only when it also has a class of "visible"
			- styled: `<div id="left-column" class="visible"></div>`
			- not-styled: `<div id="left-column"></div>`
	- `.profile.minimized {}`
		- styles all tags that have two classes (separated by a space): "profile" and "minimized"
		- `<div class="profile minimized"></div>`
	- `div#left-column {}`
		- you could combine tags and ids, but there's only ever going to be one tag with an id of "left-column"
		- it's not like you would have a group of tags with the same id, from which you want to select only those that are `div` tags
		- might as well just write `#left-column {}` and leave out the div
1. You can filter out tags based on their ancestors
	- `main p {}`
		- will style all `<p>` tags that are descendants of `<main>` tags
		
		```html
		<main>
		  <p></p>
		</main>
		```
		```html
		<main>
		  <section>
		    <p></p>
		  </section>
		</main>
		```
		
![Imgur](http://i.imgur.com/ylb6WX9.gif)


- Create a rule for all `p` tags that also have a class of `active`
- For this rule, make the text bold
- Add an `active` class to a few of your p tags
- Create a rule for all `div` tags that also have a class of `active`
- For this rule, make the text very large
- Create a `div` tag with the class of `active`


<br>

## <a name="specificity">Describe Specificity</a>

When an element is being styled by two rules at the same time, the browser calculates which rule is more specific and applies that rule.  To do this it looks at the selector.  If both rules have the same specificity, the last rule is applied.

#### Count the number of ids in each rule's selector.
- Apply whichever rule has more ids in its selector
- In theory there should only be one or zero ids in each selector
	- `#left-column #comments`
		- do not need to filter by ancestor
		- can just write `#comments`

#### If the number of ids in each rule's selector is the same, count the number of classes
- Apply whichever rule has more classes in its selector

#### If the number of ids and classes in each rule's selector is the same, count the number of tags
- Apply whichever rule has more tags in its selector

#### Scoring
Specificity is actually quite easy to calculate (these numbers are for example only):

| selector | value |
|:-- |:----------- |
| **tag** | 1 point  |
| **class**  | 10 points   |
| **id** | 100 points  |
| **inline** | 1000 points   |

#### Specificity Ties
When two selectors have the same net specificity score, then the last one applied wins. Note that stylesheets are read from top to bottom, and their styles are applied in order… therefore, styles defined lower within your stylesheet will win.

For example, an inline CSS style rule would have priority over a rule in a CSS stylesheet.

<br>

### ![Imgur](http://i.imgur.com/2BtC2Zx.gif)

<details>
	<summary>What is the net specificity of this selector `div#features a.slide h3 span`</summary>
	<br>
	This selector is worth **114 points**.
</details>


What type of CSS rule would take precidence? 

1. seperate stylesheet 
2. inline
3. within `style` tags?




![Imgur](http://i.imgur.com/ylb6WX9.gif)

1. Create a rule for the tag with an id of `blue`
1. Set the text color for this rule to blue
1. On the next line of your css file, create a rule for all tags with classes of `red`
1. Set the text color for this rule to red
1. In your HTML, create a `span` tag with both an id of `blue` and a class of `red`
1. Note that the color of the `span` tag should be blue

<br>

## <a name="conclusion">![Imgur](http://i.imgur.com/wPefQjh.png)</a>

- Check out [W3 Schools CSS](http://www.w3schools.com/css/default.asp) documentation for extra stuff
- [CSS Specificity](http://www.standardista.com/css3/css-specificity/)
