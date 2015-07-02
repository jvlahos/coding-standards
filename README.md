# Coding Standards
Coding standards help write more consistent code across a project or team. 
Use these standards as-is, or fork them and modify them to your liking.
Copy these standards to your project's repository as `coding-standards.md` for all project contributors to reference. Utilize and customize the supplied EditorConfig and linter files based upon these guidelines.
Let these standards grow and change as your project grows and changes.

* [Principles](#principles)
* Code Standards
  * HTML
    * Syntax
  * CSS
    * Philosophy
    * Syntax
    * Declaration Order
    * Shorthand Notations
    * Nesting
    * Comments
    * Naming & Abbreviation Patterns
    * Mixin and @extend usage
  * File & Folder Organization
  * Editor Helpers & Preferences
    * .editorconfig
    * Linters (scss-lint)
  
<a name="principles"></a>
## Code Principles
* Every line of code should appear to be written by a single person.
* Enforce the agreed-upon style. 
* Follow the rules when it makes sense — break them when it doesn't. Write all code with intent.
* Write readable and understandable code.


## HTML
Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible.

#### Syntax
* Use soft tabs with two spaces—they're the only way to guarantee code renders the same in any environment.
* Nested elements should be indented once (two spaces).
* Always use double quotes, never single quotes, on attributes.
* Don't include a trailing slash in self-closing elements—the HTML5 spec says they're optional.
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

#### Attribute order
HTML attributes should come in this particular order for easier reading of code.

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







