---
title: Basic Concepts of Blueprint in Webflow
---
Blueprint is a CSS framework that aims to cut down on your CSS development time. It gives you a solid CSS foundation to build your project on top of, with an easy-to-use grid, sensible typography, and even a stylesheet for printing.

In the context of this repository, Blueprint is used to style the web pages. It provides a set of CSS files that are used across the application to ensure a consistent look and feel. These files include a grid system (grid.css), typography rules (typography.css), form styling (forms.css), and specific styles for Internet Explorer (ie.css) and print layouts (print.css).

The grid system provided by Blueprint helps in creating page layouts through a series of containers, rows, and columns. The typography.css file provides styles for different HTML elements to ensure consistent typography across the application. The forms.css file provides styles for form elements, and the print.css and ie.css files provide specific styles for print layouts and Internet Explorer respectively.

In addition to these, Blueprint also provides helper classes that can be used to modify the appearance of elements. For example, the .loud class in typography.css can be used to make the text color black, and the .quiet class can be used to make the text color grey.

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/src/grid.css" line="30">

---

# Blueprint Grid System

The grid system in Blueprint is defined in the `grid.css` file. It provides classes for different column widths (`.span-1` to `.span-24`), which can be used to create a responsive layout.

```css
/* Sets up basic grid floating and margin. */
.column, div.span-1, div.span-2, div.span-3, div.span-4, div.span-5, div.span-6, div.span-7, div.span-8, div.span-9, div.span-10, div.span-11, div.span-12, div.span-13, div.span-14, div.span-15, div.span-16, div.span-17, div.span-18, div.span-19, div.span-20, div.span-21, div.span-22, div.span-23, div.span-24 {
  float: left;
  margin-right: 10px;
}

/* The last column in a row needs this class. */
.last, div.last { margin-right: 0; }

/* Use these classes to set the width of a column. */
.span-1 {width: 30px;}

.span-2 {width: 70px;}
.span-3 {width: 110px;}
.span-4 {width: 150px;}
.span-5 {width: 190px;}
.span-6 {width: 230px;}
.span-7 {width: 270px;}
.span-8 {width: 310px;}
.span-9 {width: 350px;}
.span-10 {width: 390px;}
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/src/typography.css" line="8">

---

# Blueprint Typography

The `typography.css` file in Blueprint sets up default typography for the web application. It provides styles for different heading levels (h1 to h6), paragraphs, links, and more.

```css
/* Default font settings. 
   The font-size percentage is of 16px. (0.75 * 16px = 12px) */
html { font-size:100.01%; }
body { 
  font-size: 75%;
  color: #222; 
  background: #fff;
  font-family: "Helvetica Neue", Arial, Helvetica, sans-serif;
}


/* Headings
-------------------------------------------------------------- */

h1,h2,h3,h4,h5,h6 { font-weight: normal; color: #111; }

h1 { font-size: 3em; line-height: 1; margin-bottom: 0.5em; }
h2 { font-size: 2em; margin-bottom: 0.75em; }
h3 { font-size: 1.5em; line-height: 1; margin-bottom: 1em; }
h4 { font-size: 1.2em; line-height: 1.25; margin-bottom: 1.25em; }
h5 { font-size: 1em; font-weight: bold; margin-bottom: 1.5em; }
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/src/forms.css" line="13">

---

# Blueprint Forms

Blueprint's `forms.css` file sets up default styling for forms. It provides classes for different form elements like input fields, checkboxes, and radio buttons.

```css
label       { font-weight: bold; }
fieldset    { padding:1.4em; margin: 0 0 1.5em 0; border: 1px solid #ccc; }
legend      { font-weight: bold; font-size:1.2em; }


/* Form fields
-------------------------------------------------------------- */

input[type=text], input[type=password],
input.text, input.title,
textarea, select {
  background-color:#fff;
  border:1px solid #bbb;
}
input[type=text]:focus, input[type=password]:focus,
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/src/reset.css" line="8">

---

# Blueprint Reset

The `reset.css` file in Blueprint resets default browser CSS. This helps in maintaining consistency in appearance across different browsers.

```css
html, body, div, span, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, code,
del, dfn, em, img, q, dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td {
  margin: 0;
  padding: 0;
  border: 0;
  font-weight: inherit;
  font-style: inherit;
  font-size: 100%;
  font-family: inherit;
  vertical-align: baseline;
}

body { 
  line-height: 1.5; 
}

/* Tables still need 'cellspacing="0"' in the markup. */
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
