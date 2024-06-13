---
title: 'Mapping <ui:insert> Tags to <ui:define> Tags in JSF'
---
This document will cover the use of `<ui:insert>` and `<ui:define>` tags in the application. We'll cover:

1. What are `<ui:insert>` and `<ui:define>` tags
2. How they are used in the application
3. How they correspond to each other in different pages of the application.

# What are `<ui:insert>` and `<ui:define>` tags

`<ui:insert>` and `<ui:define>` are Facelets tags used in JSF (JavaServer Faces) to create reusable templates. `<ui:insert>` is used in the template file to define a placeholder for content, while `<ui:define>` is used in the client pages to provide the actual content for these placeholders.

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/layouts/standard.xhtml" line="17">

---

# How they are used in the application

In this `standard.xhtml` layout file, `<ui:insert>` tags are used to define placeholders for `headIncludes`, `title`, `notes`, and `content`. These placeholders will be filled with actual content in the client pages using `<ui:define>` tags.

```html
	<ui:insert name="headIncludes"/>
</h:head>
<h:body>
<div class="container">
	<div>
		<h1>JSF 2, PrimeFaces, and Spring Web Flow</h1>
		<h3 class="alt">
			<ui:insert name="title"/>
		</h3>
		<hr/>
	</div>
	<div>	
		<ui:insert name="notes"/>
	</div>
	<div>
		<ui:insert name="content"/>
	</div>
```

---

</SwmSnippet>

# How they correspond to each other in different pages of the application

In the client pages of the application, `<ui:define>` tags are used to provide the actual content for the placeholders defined in the template file. The `name` attribute of the `<ui:define>` tag should match the `name` attribute of the corresponding `<ui:insert>` tag in the template file. For example, if there is a `<ui:insert name="content"/>` in the template file, there should be a `<ui:define name="content">Actual Content</ui:define>` in the client page.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
