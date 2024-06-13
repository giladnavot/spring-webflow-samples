---
title: Introduction to Layouts in Booking MVC
---
Layouts in the booking-mvc application are used to define the structure of the web pages. They provide a consistent look and feel across all pages by defining common elements such as headers, footers, and navigation menus. The standard.html file in the layouts directory is a Thymeleaf template that serves as the main layout for the application. It includes links to stylesheets, scripts, and other resources, and defines placeholders for the page-specific content.

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/layouts/standard.html" line="1">

---

# Layout Structure

This is the standard layout used in the booking-mvc application. It defines the HTML structure of the page, including the head and body sections. The body section includes common elements such as the header, content, and footer. The unique content for each page is inserted at the specified location in the layout.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 
      xmlns:th="http://www.thymeleaf.org"
      xmlns:sec="http://www.thymeleaf.org"
      lang="en">

<head>

    <title>Spring Travel: Spring MVC and Web Flow Reference Application</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    
    <link rel="stylesheet" type="text/css" media="screen, projection" 
          href="../../styles/blueprint/screen.css" 
          th:href="@{/resources/styles/blueprint/screen.css}" />
    
    <link rel="stylesheet" type="text/css" media="print" 
          href="../../styles/blueprint/print.css" 
          th:href="@{/resources/styles/blueprint/print.css}" />
    
    <!--[if lt IE 8]>
        <link rel="stylesheet" type="text/css" media="screen, projection"
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/layouts/standard.html" line="26">

---

# Using Stylesheets in Layouts

This is an example of how stylesheets are included in the layout. The `booking.css` stylesheet is linked in the head section of the layout, making its styles available to all pages that use this layout.

```html
    <link rel="stylesheet" type="text/css" media="screen" 
          href="../../styles/booking.css" 
          th:href="@{/resources/styles/booking.css}" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
