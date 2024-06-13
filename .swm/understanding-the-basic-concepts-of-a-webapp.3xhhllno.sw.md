---
title: Understanding the Basic Concepts of a Webapp
---
Webapp in the booking-faces project refers to the main directory that contains all the resources needed for the web application. It includes HTML, CSS, images, and configuration files.

The WEB-INF directory within the webapp directory is a container for resources such as XML configuration files and XHTML files that define the application's user interface.

The styles directory contains CSS files and themes for the application's visual appearance, while the images directory holds the image files used in the application.

The META-INF directory contains metadata about the application, such as the MANIFEST.MF file.

The index.html file in the webapp directory is the entry point of the application, which redirects to the 'intro' page.

<SwmSnippet path="/booking-faces/src/main/webapp/index.html" line="1">

---

# HTML Files

The `index.html` file is the entry point of the web application. It redirects the user to the `spring/intro` URL.

```html
<html>
<head>
  <meta http-equiv="Refresh" content="0; URL=spring/intro">
</head>
</html>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/styles/booking.css" line="34">

---

# Stylesheets

The `booking.css` file contains the CSS styles for the web application. It defines styles for various classes and selectors, such as `.summary` and `label`.

```css
.summary {
	width: 100%;
	border: 1px solid #414f23;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/beans.xml" line="1">

---

# Configuration Files

Configuration files such as `beans.xml` are stored in the WEB-INF directory. These files are used to configure various aspects of the Spring application.

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://staging.swimm.cloud/)</sup></SwmMeta>
