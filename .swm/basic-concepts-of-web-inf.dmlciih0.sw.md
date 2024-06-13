---
title: Basic Concepts of WEB-INF
---
The `WEB-INF` directory in a Java web application is a location for resources such as configuration files, JSP files, and libraries. It is a secure directory because its contents are not directly accessible from the browser.

In the `webflow-showcase` application, the `WEB-INF` directory contains the `web.xml` file, which is the deployment descriptor for the application. It configures the `DispatcherServlet` that handles incoming requests.

The `WEB-INF` directory also contains subdirectories for layouts, views, flows, and Spring configuration. The `layouts` directory contains JSP files that define the layout for the application. The `views` directory contains JSP files for individual views. The `flows` directory contains Spring Web Flow definitions.

The `spring` directory contains Spring configuration files. These files define beans and other components for the application context.

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/web.xml" line="1">

---

# 'web.xml' File

The 'web.xml' file is the deployment descriptor of the application. It defines the servlet mapping for the 'DispatcherServlet', which is the entry point for handling requests in Spring MVC applications.

```xml
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
		 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://java.sun.com/xml/ns/javaee https://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
		 version="3.0">

	<servlet>
		<servlet-name>DispatcherServlet</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<init-param>
			<param-name>contextConfigLocation</param-name>
			<param-value>/WEB-INF/spring/servlet-context.xml</param-value>
		</init-param>
		<load-on-startup>1</load-on-startup>
	</servlet>
		
	<servlet-mapping>
		<servlet-name>DispatcherServlet</servlet-name>
		<url-pattern>/</url-pattern>
	</servlet-mapping>

</web-app>
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/spring/servlet-context.xml" line="6">

---

# Spring Configuration Files

The 'servlet-context.xml' file is one of the Spring configuration files. It is specified as the 'contextConfigLocation' parameter in the 'web.xml' file. This file typically contains beans definitions that are specific to the web layer of the application.

```xml
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd
		http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd">

	<!--
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/flow.xml" line="4">

---

# Flow Definitions

The 'flow.xml' files define the flows for the Spring Web Flow. Each flow is a module of the application that encapsulates a sequence of steps that guide the user through a controlled navigation.

```xml
	xsi:schemaLocation="
		http://www.springframework.org/schema/webflow 
		https://www.springframework.org/schema/webflow/spring-webflow.xsd">

	<view-state id="step1" view="embeddedFlow/step1">
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/views/home.jsp" line="1">

---

# JSP View Templates

The JSP files in the 'views' directory are the view templates of the application. They define the presentation of the data that is sent to the client.

```java server pages
<div>
```

---

</SwmSnippet>

# Spring Web Flow Endpoints

Understanding Spring Web Flow Endpoints

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="15">

---

## Root Endpoint (/)

The root endpoint (/) is mapped to the 'home' view. This means when a user navigates to the base URL of the application, they are served the 'home' view.

```xml
	<mvc:view-controller path="/" view-name="home" />
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="16">

---

## /embeddedFlowContainer Endpoint

The /embeddedFlowContainer endpoint is not mapped to a specific view. This suggests that the endpoint is handled by a controller method, which would determine the appropriate view to return.

```xml
	<mvc:view-controller path="/embeddedFlowContainer" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
