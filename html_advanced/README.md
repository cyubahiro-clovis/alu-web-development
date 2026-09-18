# SmileSchool: Building a Designer's Page in Pure HTML

This is the first stage of an advanced front end project at ALU. The goal is to take a finished
design from Figma and rebuild it from scratch as a real webpage.

The catch, and the point of the exercise, is that this stage is **HTML only**. No CSS, no
JavaScript, no frameworks. Nothing that makes it look good yet. Just the structure underneath,
written with the correct semantic tags, and it has to pass the W3C validator.

Building the skeleton before the styling forces you to think about what each piece of content
actually *is* rather than how it should look. A navigation bar is a list of links, whether or not
it ends up sitting in a row. A testimonial is a quote with an attribution. Once the structure is
honest, the CSS in the next project has clean hooks to attach to.

## The design

![SmileSchool page design](images/design.png)

SmileSchool is a fictional site that teaches people how to smile. The full page runs from a hero
section down through instructor profiles, a testimonial, video tutorials, membership benefits,
an FAQ and a footer.

## The wireframe

![Page wireframe](images/wireframe.png)

The wireframe is the version I actually work from. Stripping the design back to labelled boxes
makes the nesting obvious: which blocks sit inside which, what repeats, and where a list is
hiding. The four instructor cards are not four separate things, they are one pattern repeated
four times, and the wireframe is what makes that jump out.

## What the page contains

Reading the wireframe from top to bottom:

| Section | Structure |
| --- | --- |
| Header | Logo on the left, three navigation links on the right |
| Hero | Title, a three word tagline, a call to action button |
| Learn from the pros | Section title, then four instructor cards of image, name and subtitle |
| Testimonial | An image beside a quote, its author and their job title |
| Most popular tutorials | Section title, then four video cards with image, title, text, author and rating |
| Free membership | Section title, four benefit blocks of image, title and text, then a button |
| FAQ | Section title, then four question and answer pairs in two rows |
| Footer | Logo, three social media icons, a line of copyright text |

## Project structure

```
html_advanced/
    README.md
    images/
        design.png
        wireframe.png
    index.html
```

`index.html` arrives with the next task. For now this README and the reference images are the
deliverable.

## How to view it

No build step and no server needed. Once `index.html` exists, open it directly in a browser:

```
open index.html
```

Or just double click the file. That is one of the quiet advantages of plain HTML.

## Concepts behind this project

Writing these down in my own words, because the project asks me to be able to explain them
without looking anything up.

**HTML** stands for HyperText Markup Language. It is the language that describes the content and
structure of a web page. It is not a programming language, since it has no logic, no variables
and no loops. It only says what things are.

**A markup language** annotates text to say something about it. In HTML the annotations are tags
wrapped in angle brackets. The plain sentence `Get schooled` becomes a top level heading when I
mark it up as `<h1>Get schooled</h1>`. The words did not change, but now the browser, a search
engine and a screen reader all understand what role they play.

**An element** is a complete unit of content: an opening tag, the content, and a closing tag.
`<p>Learn from the pros</p>` is one paragraph element. **A tag** is just the marker itself, the
`<p>` or the `</p>`. People use the two words interchangeably in conversation, but the
distinction is real. A few elements, like `<img>` and `<br>`, are void elements and have no
closing tag or content at all.

**An attribute** is extra information placed inside the opening tag, written as `name="value"`.
`<a href="index.html">` uses `href` to say where the link goes. `<img src="logo.png" alt="Logo">`
uses `src` for the file and `alt` for the text shown if the image cannot load, which is also what
a screen reader reads aloud. Some attributes are required for the page to be valid, and `alt` on
an image is one of them.

**The DOM** is the Document Object Model. When a browser reads my HTML it does not keep the text,
it builds a tree of objects in memory, one node per element, nested exactly as my tags were
nested. That tree is the DOM. It matters for two reasons. CSS selectors walk it to decide what to
style, and JavaScript manipulates it to change a page after it has loaded. A missing closing tag
does not just look untidy, it produces the wrong tree, and everything downstream inherits the
mistake.

**Semantic tags** describe meaning rather than appearance. `<header>`, `<nav>`, `<main>`,
`<section>`, `<article>`, `<aside>` and `<footer>` all render as plain blocks with no styling, so
visually they are interchangeable with `<div>`. The difference is that a screen reader can offer
to skip straight to `<main>`, and a search engine can tell the article from the sidebar. Choosing
`<div>` everywhere throws that away for no gain.

## Tags I expect to use

| Tag | Job |
| --- | --- |
| `<header>` `<nav>` | Top bar and its link list |
| `<main>` | The one block of content unique to this page |
| `<section>` | Each major band of the page |
| `<article>` | A self contained card, such as one tutorial |
| `<aside>` | Content tangential to the main flow |
| `<footer>` | Closing bar with logo and social links |
| `<h1>` to `<h6>` | Headings, in order, never skipped for size |
| `<p>` | Paragraphs of text |
| `<ul>` `<li>` | Navigation links, and any repeated card set |
| `<a>` | Links |
| `<img>` | Images, always with `alt` |
| `<blockquote>` `<cite>` | The testimonial and its attribution |
| `<button>` | The two call to action buttons |

## Requirements

* Every file ends with a newline
* No external libraries. Plain HTML, CSS and JavaScript only. No NodeJS, React, VueJS or Bootstrap
* All code passes the [W3C Validator](https://validator.w3.org/)
* This README is mandatory and lives at the root of the project folder

## Validating

Paste the file into the **Validate by Direct Input** tab at
[validator.w3.org](https://validator.w3.org/), since the page is not published anywhere yet. The
target is "Document checking completed. No errors or warnings."

Two traps I already know about from earlier projects. Writing a literal `<h1>` inside a paragraph
breaks the tree, because the browser reads it as a real tag, so it has to be escaped as
`&lt;h1&gt;`. And the `charset` attribute on a `<script>` tag is obsolete in HTML5 even though
plenty of copy and paste snippets still include it.

## Author

Mwiseneza Cyubahiro Clovis, ALU Front End Web Development.

Design file provided by the course on Figma.
