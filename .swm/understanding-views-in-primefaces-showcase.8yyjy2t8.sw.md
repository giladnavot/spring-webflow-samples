---
title: Understanding Views in PrimeFaces Showcase
---
Views in the spring-webflow-samples repository, specifically in the primefaces-showcase project, refer to the XHTML files that define the user interface of the web application. These files are located in the WEB-INF/views directory. They use Facelets, a view technology for JavaServer Faces (JSF), to create the UI. The views are composed of various JSF and PrimeFaces UI components, and they define the layout and functionality of the web pages. For example, the login.xhtml view defines the login form of the application.

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/views/home.xhtml" line="1">

---

# Structure of a View

This is an example of a view. It uses the Facelets template language to define the structure of the page. The `<ui:composition>` tag is used to include content from a template, and the `<ui:define>` tags are used to define content for named sections of the template.

```html
<!DOCTYPE composition PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<ui:composition xmlns="http://www.w3.org/1999/xhtml"
	xmlns:ui="http://java.sun.com/jsf/facelets"
	xmlns:h="http://java.sun.com/jsf/html"
	xmlns:f="http://java.sun.com/jsf/core"
	xmlns:p="http://primefaces.org/ui"
	template="/WEB-INF/layouts/standard.xhtml">

<ui:define name="title"></ui:define>

<ui:define name="notes">
	<p>
		Note that in "development" mode you can make changes to flow definitions without the 
		need to restart the server. The development mode is specified in 
		<span class="alt">src/main/webapp/WEB-INF/spring/appServlet/webflow.xml</span>.
	</p>
	<hr/>
</ui:define>

<ui:define name="content">

```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/views/home.xhtml" line="22">

---

# Dynamic Content in Views

This part of the view defines dynamic content. The `<p:tabView>` tag is a PrimeFaces component that creates a tabbed view. The active tab is determined by the `activeIndex` attribute, which is bound to a request parameter. Each `<p:tab>` defines the content for a tab.

```html
	<p:tabView activeIndex="${param.tab}">

		<p:tab title="Ajax 101">
			<ul>
				<li>
					<h:outputLink value="ajax-jsf?tab=0" >
						<h:outputText value="JSF 2 commandButton with f:ajax" />
					</h:outputLink><br/>
					<span class="alt">Ajax request and responses with h:commandButton + nested f:ajax tag.</span>
				</li>
				<li>
					<h:outputLink value="ajax-primefaces?tab=0" >
						<h:outputText value="PrimeFaces commandButton" />
					</h:outputLink><br/>
					<span class="alt">Ajax request and response with the PrimeFaces commandButton.</span> 
				</li>
				<li>
					<h:outputLink value="ajax-render-action?tab=0" >
						<h:outputText value="Web Flow render action" />
					</h:outputLink><br/>
					<span class="alt">Integration between the Web Flow render action and PrimeFaces partial rendering.</span> 
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/views/login.xhtml" line="28">

---

# Form Handling in Views

This part of the view defines a form for user login. The form fields are bound to request parameters, and the form action is set to a URL that will handle the form submission. The form is enclosed in a `<p:panel>` component, which is a PrimeFaces component that creates a panel with a header.

```html
		<form name="f" action="${request.contextPath}/app/loginProcess" method="post">
			<p>
				User:
				<br />
				<input type="text" name="username" />
			</p>
			<p>
				Password:
				<br />
				<input type="password" name="password" />
			</p>
			<p>
				<input type="checkbox" name="_spring_security_remember_me"/> 
				Don't ask for my password for two weeks
			</p>
			<p>
				<input name="submit" type="submit" value="Login" />
			</p>
		</form>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
