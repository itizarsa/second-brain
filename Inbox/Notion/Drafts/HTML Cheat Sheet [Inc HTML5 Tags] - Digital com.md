# HTML Cheat Sheet [Inc HTML5 Tags] - Digital.com

Source: Website
Status: Unprocessed
URL: https://digital.com/tools/html-cheatsheet/

![https://digital.com/wp-content/uploads/html-cheat-sheet.png](https://digital.com/wp-content/uploads/html-cheat-sheet.png)

---

[HTML%20Cheat%20Sheet%20%5BInc%20HTML5%20Tags%5D%20-%20Digital%20com%2011587a5ab5634f99afd69f4c3ede76b0/FFFFFF](HTML%20Cheat%20Sheet%20%5BInc%20HTML5%20Tags%5D%20-%20Digital%20com%2011587a5ab5634f99afd69f4c3ede76b0/FFFFFF)

![HTML%20Cheat%20Sheet%20%5BInc%20HTML5%20Tags%5D%20-%20Digital%20com%2011587a5ab5634f99afd69f4c3ede76b0/graybg.png](HTML%20Cheat%20Sheet%20%5BInc%20HTML5%20Tags%5D%20-%20Digital%20com%2011587a5ab5634f99afd69f4c3ede76b0/graybg.png)

[HTML%20Cheat%20Sheet%20%5BInc%20HTML5%20Tags%5D%20-%20Digital%20com%2011587a5ab5634f99afd69f4c3ede76b0/FFFFFF%201](HTML%20Cheat%20Sheet%20%5BInc%20HTML5%20Tags%5D%20-%20Digital%20com%2011587a5ab5634f99afd69f4c3ede76b0/FFFFFF%201)

### BR TAG

Line break. The HTML element line break <br> produces a line break in text (carriage-return). It is useful for writing a poem or an address, where the division of lines is significant. Do not use <br> to increase the gap between lines of text; use the CSS margin property or the <p> element.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<p>Digital.com<br>xx <br>xx</p>
```

### DD TAG

Description, definition, or value, part of a term- description group in a description list. The HTML <dd> element (HTML Description Element) indicates the description of a term in a description list (<dl>) element. This element can occur only as a child element of a description list and it must follow a <dt> element.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<dl>
  <dt>Digital.com</dt>
  <dd>Helps you find the best tools for running a small business website</dd>
</dl>
```

### DIV TAG

Container or section with no semantic meaning. The HTML <div> element (or HTML Document Division Element) is the generic container for flow content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the class or id attributes), or because they share attribute values, such as lang. It should be used only when no other semantic element (such as <article> or <nav>) is appropriate.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<div><p>Any kind of content here. Such as <p>, <table>. You name it!</p></div>
```

### DL TAG

An association list consisting of zero or more name-value groups (a description list). The HTML <dl> element (or HTML Description List Element) encloses a list of pairs of terms and descriptions. Common uses for this element are to implement a glossary or to display metadata (a list of key-value pairs). Prior to HTML5, <dl> was known as a Definition List.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<dl>
  <dt>Digital.com</dt>
  <dd>Helps you find the best tools for running a small business website</dd>
</dl>
```

### DT TAG

Term, or name, part of a term-description group in a description list. The HTML <dt> element (or HTML Definition Term Element) identifies a term in a definition list. This element can occur only as a child element of a <dl>. It is usually followed by a <dd> element; however, multiple <dt> elements in a row indicate several terms that are all defined by the immediate next <dd> element.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<dl>
  <dt>Digital.com</dt>
  <dd>Helps you find the best tools for running a small business website</dd>
</dl>
```

### FIGCAPTION TAG

Caption or legend for the figure element. The HTML <figcaption> element represents a caption or a legend associated with a figure or an illustration described by the rest of the data of the <figure> element which is its immediate ancestor which means <figcaption> can be the first or last element inside a <figure> block. Also, the HTML Figcaption Element is optional; if not provided, then the parent figure element will have no caption.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<figure>
  <img src="http://www.example.com/picture.png" alt="An awesome picture">
  <figcaption>A picture</figcaption>
</figure>
```

### FIGURE TAG

Contains elements related to single concept, such as an illustration or code example. The HTML <figure> element represents self-contained content, frequently with a caption (<figcaption>), and is typically referenced as a single unit. While it is related to the main flow, its position is independent of the main flow. Usually this is an image, an illustration, a diagram, a code snippet, or a schema that is referenced in the main text, but that can be moved to another page or to an appendix without affecting the main flow.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<figure>
  <img src="http://www.example.com/picture.png" alt="An awesome picture">
  <figcaption>A picture</figcaption>
</figure>
```

### HR TAG

Paragraph-level thematic break. The HTML <hr> element represents a thematic break between paragraph-level elements (for example, a change of scene in a story, or a shift of topic with a section). In previous versions of HTML, it represented a horizontal rule. It may still be displayed as a horizontal rule in visual browsers, but is now defined in semantic terms, rather than presentational terms.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<p>This is the first paragraph of text.</p><hr><p>This is second paragraph of text.</p>
```

### LI TAG

List item. The HTML <li> element (or HTML List Item Element) is used to represent an item in a list. It must be contained in a parent element: an ordered list (<ol>), an unordered list (<ul>), or a menu (<menu>). In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists, they are usually displayed with an ascending counter on the left, such as a number or letter.

**Attributes** (modifiers)
 value + [global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

### MAIN TAG

Specifies the main content area of an HTML document. The HTML <main> element represents the main content of the <body> of a document or application. The main content area consists of content that is directly related to, or expands upon the central topic of a document or the central functionality of an application. This content should be unique to the document, excluding any content that is repeated across a set of documents such as sidebars, navigation links, copyright information, site logos, and search forms (unless the document’s main function is as a search form).

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<main>
  <h1>Apples</h1>
  <p>The apple is the pomaceous fruit of the apple tree.</p>
  <article>
  <p>The apple is the pomaceous fruit of the apple tree.</p>
  </article>
</main>
```

### OL TAG

Ordered list. The HTML <ol> Element (or HTML Ordered List Element) represents an ordered list of items. Typically, ordered-list items are displayed with a preceding numbering, which can be of any form, like numerals, letters or Romans numerals or even simple bullets. This numbered style is not defined in the HTML description of the page, but in its associated CSS, using the list-style-type property. There is no limitation to the depth and overlap of lists defined with the <ol> and <ul> elements.

**Attributes** (modifiers)
 start | reversed | type + [global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

### P TAG

Paragraph content. The HTML <p> element (or HTML Paragraph Element) represents a paragraph of text. Paragraphs are usually represented in visual media as blocks of text that are separated from adjacent blocks by vertical blank space and/or first-line indentation. Paragraphs are block-level elements.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<p>This is the first paragraph of text.</p><p>This is second paragraph of text.</p>
```

### PRE TAG

A block of preformatted text. The HTML <pre> element (or HTML Preformatted Text) represents preformatted text. Text within this element is typically displayed in a non-proportional (“monospace”) font exactly as it is laid out in the file. Whitespace inside this element is displayed as typed.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<pre>
body {
  background-color:red;
}
</pre>
```

## Compare Popular Web Hosting Plans

We think the following plans will suit the majority of our visitor's needs.

1. [Visit Dreamhost Website](https://digital.com/go/dreamhost/)

### UL TAG

Unordered list. The HTML <ul> element (or HTML Unordered List Element) represents an unordered list of items, namely a collection of items that do not have a numerical ordering, and their order in the list is meaningless. Typically, unordered-list items are displayed with a bullet, which can be of several forms, like a dot, a circle or a squared. The bullet style is not defined in the HTML description of the page, but in its associated CSS, using the list-style-type property.

**Attributes** (modifiers)[Global attributes](https://digital.com/tools/html-cheatsheet/)

### Code example

```
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```