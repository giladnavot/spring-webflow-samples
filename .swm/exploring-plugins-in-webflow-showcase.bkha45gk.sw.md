---
title: Exploring Plugins in Webflow Showcase
---
Plugins in the webflow-showcase project refer to additional sets of CSS stylesheets that enhance the functionality and aesthetics of the web application. They are located in the 'styles/blueprint/plugins' directory. Each plugin has its own directory, such as 'fancy-type', 'buttons', 'rtl', and 'link-icons', each containing a 'screen.css' file and a 'readme.txt' file. The 'screen.css' file contains the actual CSS rules that implement the plugin's functionality, while the 'readme.txt' provides additional information about the plugin.

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/plugins/buttons/screen.css" line="1">

---

# Button Plugin

The Button plugin provides styles for button elements. It includes different color schemes for different button states (hover, active), and for positive and negative actions.

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

# RTL Plugin

The RTL (Right-to-Left) plugin provides styles for supporting right-to-left languages. It mirrors the layout of the Blueprint grid system and adjusts the typography for right-to-left reading.

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

<SwmSnippet path="/webflow-showcase/src/main/webapp/styles/blueprint/plugins/link-icons/screen.css" line="1">

---

# Link Icons Plugin

The Link Icons plugin provides styles for adding icons to links based on their protocol or file type. For example, external links get an external link icon, email links get an email icon, and links to PDF files get a PDF icon.

```css
/* -------------------------------------------------------------- 
  
   link-icons.css
   * Icons for links based on protocol or file type.
   
   See the Readme file in this folder for additional instructions.

-------------------------------------------------------------- */

/* Use this class if a link gets an icon when it shouldn't. */
body a.noicon { 
	background:transparent none !important; 
	padding:0 !important; 
	margin:0 !important; 
}

/* Make sure the icons are not cut */
a[href^="http:"], a[href^="mailto:"], a[href^="http:"]:visited, 
a[href$=".pdf"], a[href$=".doc"], a[href$=".xls"], a[href$=".rss"], 
a[href$=".rdf"], a[href^="aim:"] {
  padding:2px 22px 2px 0;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
