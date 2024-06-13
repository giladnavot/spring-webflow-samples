---
title: Basic Concepts of a Web App in Primefaces-Showcase
---
A Web app in the primefaces-showcase project refers to a Java-based web application. It is defined and configured using XML files located in the WEB-INF directory. These files include 'web.xml' which is the deployment descriptor of the application, 'beans.xml' for defining beans, 'faces-config.xml' for JSF configuration, and various other XML files for Spring and Web Flow configurations.

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/web.xml" line="1">

---

# Web App Configuration

This is the main configuration file for the web app. It defines the servlets, filters, listeners, and context parameters that are used by the application. It also specifies the welcome file for the application.

```xml
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
		 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://java.sun.com/xml/ns/javaee https://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
		 version="3.0">

	<!--
		SPRING ROOT WEB APPLICATION CONTEXT
	-->

	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>
			/WEB-INF/spring/root-context.xml,
			/WEB-INF/spring/servlet-context.xml
		</param-value>
	</context-param>

	<listener>
		<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
	</listener>

```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/root-context.xml" line="1">

---

# Spring Configuration

This file is part of the Spring configuration. It is referenced in the web.xml file and is used to configure the Spring root application context.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd">
	
	<!-- Root Context: defines shared resources visible to all other web components -->
	<import resource="security-config.xml"/>
	<import resource="servlet-context.xml"/>
	
</beans>

```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/faces-config.xml" line="1">

---

# JSF Configuration

This file is part of the JSF configuration. It is used to configure the JSF application, including the message bundle used for localization.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<faces-config xmlns="http://java.sun.com/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee https://java.sun.com/xml/ns/javaee/web-facesconfig_2_0.xsd"
        version="2.0">

	<application>
		<message-bundle>JsfMessageResources</message-bundle>
	</application>

</faces-config>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/webflow.xml" line="6">

---

# Spring Web Flow Configuration

This file is part of the Spring Web Flow configuration. It is used to configure the Spring Web Flow system, which handles the execution of flows within the application.

```xml
	xsi:schemaLocation="http://www.springframework.org/schema/webflow-config https://www.springframework.org/schema/webflow-config/spring-webflow-config.xsd
		http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/faces https://www.springframework.org/schema/faces/spring-faces.xsd">

	<!-- Executes flows: the central entry point into the Spring Web Flow system -->
```

---

</SwmSnippet>

# Web Application Endpoints

Understanding Web Application Endpoints

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="16">

---

## /login Endpoint

The `/login` endpoint is defined here. When a client makes a request to this URL, the application will display the login view. This is handled by the `UrlBasedViewResolver` in the servlet context, which resolves 'login' to `/WEB-INF/views/login.xhtml`.

```xml
	<mvc:view-controller path="/login" />
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="18">

---

## /home Endpoint

The `/home` endpoint is defined here. When a client makes a request to this URL, the application will display the home view. This is also handled by the `UrlBasedViewResolver` in the servlet context, which resolves 'home' to `/WEB-INF/views/home.xhtml`.

```xml
	<mvc:view-controller path="/home" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
