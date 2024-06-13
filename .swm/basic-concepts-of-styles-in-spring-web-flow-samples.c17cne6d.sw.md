---
title: Basic Concepts of Styles in Spring Web Flow Samples
---
Styles in the spring-webflow-samples project refer to the CSS rules defined in the styles directory. These rules are used to control the appearance of the web pages in the project. For example, there are selectors like 'del' and 'ul', and classes like '.loud' defined in the typography.css file. These styles are applied to the corresponding HTML elements to control their visual presentation.

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/screen.css" line="1">

---

# Blueprint CSS Framework

This file is part of the Blueprint CSS framework, which is a design tool for creating flexible grid layouts. It includes styles for typography, forms, and a grid system.

```css
/* -----------------------------------------------------------------------


 Blueprint CSS Framework 0.9
 http://blueprintcss.org

   * Copyright (c) 2007-Present. See LICENSE for more info.
   * See README for instructions on how to use Blueprint.
   * For credits and origins, see AUTHORS.
   * This is a compressed file. See the sources in the 'src' directory.

----------------------------------------------------------------------- */

/* reset.css */
html, body, div, span, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, code, del, dfn, em, img, q, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td {margin:0;padding:0;border:0;font-weight:inherit;font-style:inherit;font-size:100%;font-family:inherit;vertical-align:baseline;}
body {line-height:1.5;}
table {border-collapse:separate;border-spacing:0;}
caption, th, td {text-align:left;font-weight:normal;}
table, td, th {vertical-align:middle;}
blockquote:before, blockquote:after, q:before, q:after {content:"";}
blockquote, q {quotes:"" "";}
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/src/ie.css" line="1">

---

# Internet Explorer Specific Styles

This file contains styles specifically for Internet Explorer. It includes various hacks to ensure that the web application displays correctly in this browser.

```css
/* -------------------------------------------------------------- 
   
   ie.css
   
   Contains every hack for Internet Explorer,
   so that our core files stay sweet and nimble.
   
-------------------------------------------------------------- */

/* Make sure the layout is centered in IE5 */
body { text-align: center; }
.container { text-align: left; }

/* Fixes IE margin bugs */
* html .column, * html div.span-1, * html div.span-2, 
* html div.span-3, * html div.span-4, * html div.span-5, 
* html div.span-6, * html div.span-7, * html div.span-8, 
* html div.span-9, * html div.span-10, * html div.span-11, 
* html div.span-12, * html div.span-13, * html div.span-14, 
* html div.span-15, * html div.span-16, * html div.span-17, 
* html div.span-18, * html div.span-19, * html div.span-20, 
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/plugins/fancy-type/screen.css" line="1">

---

# Fancy Type Plugin

This file is part of the Fancy Type plugin for the Blueprint CSS framework. It provides advanced classes for manipulating text, such as indentation, reduced size type, and uppercase words.

```css
/* -------------------------------------------------------------- 
  
   fancy-type.css
   * Lots of pretty advanced classes for manipulating text.
   
   See the Readme file in this folder for additional instructions.

-------------------------------------------------------------- */

/* Indentation instead of line shifts for sibling paragraphs. */
   p + p { text-indent:2em; margin-top:-1.5em; }
   form p + p  { text-indent: 0; } /* Don't want this in forms. */
   

/* For great looking type, use this code instead of asdf: 
   <span class="alt">asdf</span>  
   Best used on prepositions and ampersands. */
  
.alt { 
  color: #666; 
  font-family: "Warnock Pro", "Goudy Old Style","Palatino","Book Antiqua", Georgia, serif; 
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/plugins/buttons/screen.css" line="1">

---

# Buttons Plugin

This file is part of the Buttons plugin for the Blueprint CSS framework. It provides styles for creating CSS-only buttons.

```css
/* -------------------------------------------------------------- 
  
   buttons.css
   * Gives you some great CSS-only buttons.
   
   Created by Kevin Hale [particletree.com]
   * particletree.com/features/rediscovering-the-button-element

   See Readme.txt in this folder for instructions.

-------------------------------------------------------------- */

a.button, button {
  display:block;
  float:left;
  margin: 0.7em 0.5em 0.7em 0;
  padding:5px 10px 5px 7px;   /* Links */
  
  border:1px solid #dedede;
  border-top:1px solid #eee;
  border-left:1px solid #eee;
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/plugins/rtl/screen.css" line="1">

---

# Right-to-Left Language Support

This file provides styles for supporting right-to-left languages. It mirrors the Blueprint CSS framework to accommodate languages that are read from right to left.

```css
/* --------------------------------------------------------------

   rtl.css
   * Mirrors Blueprint for left-to-right languages
   
   By Ran Yaniv Hartstein [ranh.co.il]
   
-------------------------------------------------------------- */

body .container { direction: rtl; }
body .column, body div.span-1, body div.span-2, body div.span-3, body div.span-4, body div.span-5, body div.span-6, body div.span-7, body div.span-8, body div.span-9, body div.span-10, body div.span-11, body div.span-12, body div.span-13, body div.span-14, body div.span-15, body div.span-16, body div.span-17, body div.span-18, body div.span-19, body div.span-20, body div.span-21, body div.span-22, body div.span-23, body div.span-24 {
  float: right;
  margin-right: 0;
  margin-left: 10px;
  text-align:right; 
}

body div.last { margin-left: 0; }
body table .last { padding-left: 0; }

body .append-1   { padding-right: 0; padding-left: 40px; }  
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
