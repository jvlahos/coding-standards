# Coding Standards
Coding standards help write more consistent code across a project or team. 
Use these standards as-is, or fork them and modify them to your liking.
Copy these standards to your project's repository as `coding-standards.md` for all project contributors to reference. Utilize and customize the supplied EditorConfig and linter files based upon these guidelines.
Let these standards grow and change as your project grows and changes.

* [Principles](#principles)
* [HTML](#html)
  * [Syntax](#html-syntax)
  * [Attribute Order](#html-attr-order)
* [CSS / SCSS](#css-scss)
  * [Syntax](#css-syntax)
  * [Declaration Order](#css-declaration-order)
  * [Comments](#css-comments)
  * [@extends and mixins](#extends-and-mixins)
  * [Vendor prefixes](#vendor-prefixes)
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

<a name="css-scss"></a>
## CSS / SCSS

<a name="css-syntax"></a>
#### Syntax

* **Indent style:** Spaces
* **Indent size:** 2
* **Quotes:** Double
* **Hex format:** Lowercase; shorthand when possible 
  * e.g., `#fff` and `#bada55`, not `#ffffff` and `#BADA55`
* **Leading Zeroes:** Yes
  * e.g., `0.5px`, not `.5px`
* **Units on Zero-Values:** No
  * e.g., `margin: 0`, not `margin: 0px`

* Use one discrete selector per line in multi-selector rulesets.
* Include a single space before the opening brace of a ruleset.
* Include one declaration per line in a declaration block.
* Use one level of indentation for each declaration.
* Include a single space after the colon of a declaration.
* Use lowercase and shorthand hex values, e.g., #aaa.
* Use double or single quotes consistently. e.g., content: "".
* Quote attribute values in selectors, e.g., input[type="checkbox"].
* Where allowed, avoid specifying units for zero-values, e.g., margin: 0.
* Include a space after each comma in comma-separated property or function values.
* Include a semi-colon at the end of the last declaration in a declaration block.
* Place the closing brace of a ruleset in the same column as the first character of the ruleset.
* Separate each ruleset by a blank line.

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

<a name="css-nesting"></a>
## Nesting
Avoid unnecessary nesting. Just because you can nest, doesn't mean you always should. Consider nesting only if you must scope styles to a parent and if there are multiple elements to be nested.

* At most, aim for two levels.
* Nest [psuedo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) and media queries at the end of the declaration block, separated from other properties by an empty line.


<a name="css-comments"></a>
## Comments

Well commented code is extremely important. Take time to describe components, how they work, their limitations, and the way they are constructed.

* Place comments on a new line above subject.
* Make liberal use of comments to break CSS code into discrete sections.
* Comment style should be simple and consistent within a single code base.

**Example:**

```scss
/* ==========================================================================
   Section comment block
   ========================================================================== */

/* Sub-section comment block
   ========================================================================== */

/**
 * Short description using Doxygen-style comment format
 *
 * The first sentence of the long description starts here and continues on this
 * line for a while finally concluding here at the end of this paragraph.
 *
 * The long description is ideal for more detailed explanations and
 * documentation. It can include example HTML, URLs, or any other information
 * that is deemed necessary or useful.
 *
 * @tag This is a tag named 'tag'
 *
 * TODO: This is a todo statement that describes an atomic task to be completed
 *   at a later date. It wraps after 80 characters and following lines are
 *   indented by 2 spaces.
 */

// Basic comment
```

<a name="extends-and-mixins"></a>
## @extends and mixins

* Always place `@extend` statements on the first line of a declaration block.
* Place `@include` statements at a sensible spot in the relevant ruleset group.

##### Example:

```css
.box-red {
    @extend .box;
    
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    @include size(100px);
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    margin: 10px;
    padding: 10px;
    border: 10px solid #333;
}
```

<a name="vendor-prefixes"></a>
## Vendor Prefixes

Use [Autoprefixer](https://github.com/postcss/autoprefixer) to post-process your CSS with the necessary vendor prefixes.




