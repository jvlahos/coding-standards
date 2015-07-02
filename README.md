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
* Indent style: Spaces
* Indent size: 2
* Quotes: Double quotes
* Indent nested elements once.
* Don't include a trailing slash in self-closing elements.
* Don’t omit optional closing tags (e.g. `</li>` or `</body>`).

```html 
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
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


```html
<a class="..." id="..." data-toggle="modal" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```







