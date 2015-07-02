# Coding Standards
Coding standards help write more consistent code across a project or team. 
Use these standards as-is, or fork them and modify them to your liking.
Copy these standards to your project's repository as `coding-standards.md` for all project contributors to reference. Utilize and customize the supplied EditorConfig and linter files based upon these guidelines.
Let these standards grow and change as your project grows and changes.

* [Principles](#principles)
* [HTML](#html)
  * [Syntax](#html-syntax)
  * [Attribute Order](#html-attr-order)
* CSS
  * Philosophy
  * Syntax
  * Declaration Order
  * Shorthand Notations
  * Nesting
  * Comments
  * Mixin and @extend usage
* Naming & Abbreviation Patterns
* File & Folder Organization
* Editor Helpers & Preferences
    * EditorConfig
    * Linters (scss-lint)
  
<a name="principles"></a>
## Code Principles
* Write readable, consistent, and understandable code.
* Every line of code should appear to be written by a single person.
* Enforce the agreed-upon style. Write all code with intent. 
* Follow the rules when it makes sense — break them when it doesn't.
* Review code with fellow contributors and peers.

<a name="html"></a>
## HTML
Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible.

<a name="html-syntax"></a>
#### Syntax
* **Indent style:** Spaces
* **Indent size:** 2
* **Quotes:** Double quotes
* Indent nested elements.
* Don't include a trailing slash in self-closing elements.
* Don’t omit optional closing tags (e.g. `</li>` or `</body>`).
* Use _end-of_ comments after the closing tag of a multi-line code block.
  * e.g., `<!--eo .class-name-->`

**Example:**
```html 
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
    <div class="mod">
      <div class="mod-item mod-item-1">
        Fun!
      </div><!--eo .mod-item-1-->
    </div><!--eo .mod-->
  </body>
</html>

```
<a name="html-attr-order"></a>
#### Attribute Order
HTML attributes should come in this particular order for easier reading of code. Most importantly, `class` should be first.

* `class`
* `id`, `name`
* `data-*`
* `src`, `for`, `type`, `href`, `value`
* `title`, `alt`
* `aria-*`, `role`

**Example:**
```html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

<a name="css"></a>
## CSS / SCSS

<a name="css-syntax"></a>
#### Syntax

* **Indent style:** Spaces
* **Indent size:** 2
* **Quotes:** Double quotes
* **Hex format:** Lowercase; shorthand when possible 
  * e.g., `#fff` and `#bada55`, not `#ffffff` and `#BADA55`
* **Leading Zeroes:** Yes
  * e.g., `0.5px`, not `.5px`
* **Units on Zero-Values:** No
  * e.g., `margin: 0`, not `margin: 0px`
* Include a blank line before and after rulesets.
* When grouping selectors, keep individual selectors to a single line.
* Add a single space before brackets (`{`), after colons (`:`), and after each comma (`,`) in comma-separated properties and values.
* Use one level of indentation for each declaration.
* Remove end-of-line whitespace. Configure your editor to do so automatically, or "show invisibles" and do so manually.
* Place the closing `}` of a ruleset in the same column as the first character of the ruleset

**Example:**

```css
.selector-one,
.selector-two {
  background-image: url("img/background-image.png");
  color: #bada55;
}

.selector-three {
	letter-spacing: 0.5px;
	margin: 0;
}
```

<a name="css-declaration-order"></a>
## Declaration Order

Declarations are to be consistently ordered based on a simple principle:

1. Positioning
2. Display & Box Model
3. Typography
4. Everything Else

##### Example:

```css
.selector {
    /* Positioning */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Display & Box Model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    margin: 10px;
    padding: 10px;
    border: 10px solid #333;

    /* Typography */
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
    color: #fff;

    /* Everything Else */
    background: #000;
    feelings: optimistic;
}
```

Comments above are for demonstration only. Within each chunk list declarations in order of importance, stacking related rules (e.g., width and height, margin and padding).

<a name="css-comments"></a>
## Comments

Well commented code is extremely important. Take time to describe components, how they work, their limitations, and the way they are constructed.

* Place comments on a new line above subject.
* Make liberal use of comments to break CSS code into discrete sections.
* Use `/* */` CSS comments when you are documenting CSS, such as section labels. <br>*(ProTip: Grunt should be configured to remove all comments from its compressed output, which is best for performance, but retaining CSS comments in a secondary, uncompressed  file can be a helpful way to view and refine your Sass-ing.)*
* Use `//` Sass comments when you are documenting Sass, such as mixins.
* Add `TODO` comments detailing unfinished tasks.

##### Example:

```css
/* This is a section of related styles
----------------------------------------------------------------- */

/* This is a sub-section or basic comment */

/*
The long description is ideal for more detailed explanations and 
documentation. It can include example HTML, URLs, or any other 
information that is deemed necessary or useful.

TODO: This is a todo statement that describes an atomic task to be 
completed at a later date. It wraps after 80 characters and following 
lines are indented by 2 spaces.
*/
```

[ASCII text](http://patorjk.com/software/taag/#p=display&f=Big&t=Code%20Standards) is OK for section level comments. It's fun and useful in some editors.

<a name="sass"></a>
## Sass

* Always place `@extend` statements on the first line of a declaration block.
* Group `@include` statements at the top of a declaration block after any `@extend` statements.
* Don't nest declaration blocks. It makes code hard to read on complex projects and often results unecessarily specific selectors. 
* Nesting [psuedo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) and media queries is OK. They should be last in the declaration block, separated from other properties with an empty new line.

##### Example:

```css
.selector {
    @extend .someRule;
    @include clearFix();
    @include boxSizing(border-box);
    width: gridUnit(1);
    
    &:last-child {
    	...
    }
    
    @media only screen and (min-width : 320px) {
      ...
    }
}
```

<a name="vendor-prefixes"></a>
## Vendor Prefixes

Use Sass mixins whenever possible. When writing CSS, use indentation to align values.

##### Example:

```css
.selector {
    -webkit-transition: background-color 500ms ease-out 1s;
       -moz-transition: background-color 500ms ease-out 1s;
         -o-transition: background-color 500ms ease-out 1s;
            transition: background-color 500ms ease-out 1s;
}
```

<a name="naming-conventions"></a>
## Naming Conventions

<a name="semantics">
### Summary of Semantics

* **Javascript:*** `.js-` prefixed class names for elements being relied upon for JavaScript selectors
* **Utilities** are prefixed with `.u-` for single purpose utility classes like `.u-underline` and `.u-capitalize`
* **Meaningful hypens and camelCase** clarify the separation between component, descendant components, and modifiers: `componentName-subComponent-modifier`
* **Stateful classes** use `.is-` to prefix classes often toggled by JavaScript, like `.is-disabled`

<a name="ids-and-classes">
### IDs & Classes

Only use IDs for top level layout elements such as `sidebar` or `masthead`. Use classes for everything else unless an ID is needed for JavaScript. IDs and classes are camelCase with hyphens separating elements that demonstrate hierarchal relationships (see [Component Naming](#components))*.

##### Example:

```css
.btn-primary {}
.post-postHeader {}
```

<a name="specificity"></a>
### Specificity

Too much *cascading* of stylesheets can introduce [unnecessary performance](https://developers.google.com/speed/docs/insights/PrioritizeVisibleContent#UseEfficientCSSSelectors) overhead. In general, only be as specific as you need to be. 

##### Example:

```css
/* Good: */
.userList a:hover { color: red; }

/* Too specific: */
ul.userList li span a:hover { color: red; }
```

<a name="javascript">
### JavaScript Selectors 

syntax: `js-targetName`

JavaScript-specific classes reduce the risk that changing the structure or theme of components will inadvertently affect any required JavaScript behaviour and complex functionality. It is not neccesarry to use them in every case, just think of them as a tool in your utility belt. If you are creating a class, which you dont intend to use for styling, but instead only as a selector in JavaScript, you should probably be adding the `js-` prefix, but **JavaScript-specific classes should not, under any circumstances, be styled.** In practice this looks like this:

```css
<a href="/login" class="btn btn-primary js-login"></a>
```

<a name="utilities">
### Utilities

Utility classes are simple structural and positional traits abstracted for use on any element. Multiple utilities can be used together, and utilities can be used alongside components. Utilities exist because certain CSS properties and patterns are used frequently. For example: clearing floats, vertical alignment, text truncation. Relying on utilities can help to reduce repetition and provide consistent implementations.





