---
title: Understanding Layouts
---
Layouts in the `primefaces-showcase/src/main/webapp/WEB-INF/layouts` directory refer to the structure and arrangement of visual elements in the application. They define the overall appearance of the application and how the components are organized and interact with each other. The `standard.xhtml` file, for example, is a layout file that defines the standard structure of a page in the application, including the head and body sections, and placeholders for inserting specific content.

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/layouts/standard.xhtml" line="1">

---

# Layout File Structure

This is an example of a layout file in the application. It defines the common structure of the pages, including the head and body sections. The `<ui:insert>` tags are placeholders where unique content will be inserted for each page.

```html
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"
	xmlns:h="http://java.sun.com/jsf/html"
	xmlns:f="http://java.sun.com/jsf/core"
	xmlns:ui="http://java.sun.com/jsf/facelets"
	xmlns:p="http://primefaces.org/ui">
<f:view contentType="text/html">
<h:head>
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	<title>JSF 2, Spring Web Flow, and PrimeFaces Showcase</title>
	<link rel="stylesheet" href="${request.contextPath}/app/resources/styles/blueprint/screen.css" type="text/css" media="screen, projection" />
	<link rel="stylesheet" href="${request.contextPath}/app/resources/styles/blueprint/print.css" type="text/css" media="print" />
	<!--[if lt IE 8]>
		<link rel="stylesheet" href="${request.servletPath}/styles/blueprint/ie.css" type="text/css" media="screen, projection" />
	<![endif]-->
	<ui:insert name="headIncludes"/>
</h:head>
<h:body>
<div class="container">
	<div>
```

---

</SwmSnippet>

# Using the Layout

To use this layout in a page, you would use the `<ui:composition>` tag and specify the layout file as the template. Then, within the `<ui:define>` tags, you would specify the unique content for that page, matching the names of the `<ui:insert>` tags in the layout file.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
