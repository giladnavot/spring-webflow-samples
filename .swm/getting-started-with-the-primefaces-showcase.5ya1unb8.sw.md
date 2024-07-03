---
title: Getting Started with the Primefaces Showcase
---
The Primefaces showcase in this repository is a sample project that demonstrates the integration of Spring Web Flow with PrimeFaces, a popular JavaServer Faces (JSF) library. It is structured as a Maven project, as indicated by the `pom.xml` file, which includes dependencies such as PrimeFaces and Spring Web Flow. The project contains Java classes, resources, and web application files organized in the `src/main` directory. One of the key classes is `FacesHelper`, which provides helper methods for JSF views. The `index.html` file in the `webapp` directory redirects users to the home page of the application.

<SwmSnippet path="/primefaces-showcase/pom.xml" line="1">

---

# Project Structure

The `pom.xml` file defines the Maven project and its dependencies. Notice the `primefaces` artifact in the dependencies section, which includes the PrimeFaces library in the project.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>org.springframework.webflow.samples</groupId>
	<artifactId>primefaces-showcase</artifactId>
	<name>Spring Web Flow and PrimeFaces Showcase</name>
	<packaging>war</packaging>
	<version>1.0.0-BUILD-SNAPSHOT</version>

	<parent>
		<groupId>org.springframework.webflow</groupId>
		<artifactId>spring-webflow-samples</artifactId>
		<version>1.0.0.BUILD-SNAPSHOT</version>
	</parent>

	<dependencies>
		<!-- Spring -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/index.html" line="1">

---

# Main Page

The `index.html` file is the entry point of the web application. It uses a meta refresh tag to redirect to the `app/home` URL.

```html
<html>
<head>
	<meta http-equiv="Refresh" content="0; URL=app/home">
</head>
</html>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/jsf/FacesHelper.java" line="7">

---

# FacesHelper Class

The `FacesHelper` class is a Spring component that provides a method `isError` to check if there are any Faces messages to display. This can be used in a Facelets view to conditionally render a box around messages.

```java
@Component
public class FacesHelper {

	/**
	 * This method can be used in a Facelets View to render a box around <h:messages/> conditionally.
	 * Note that this is only necessary with vanilla JSF. With PrimeFaces you can use <p:messages/>
	 * or <p:growl>.
	 * 
	 * @return true if there are messages to display
	 */
	public boolean isError() {
		return FacesContext.getCurrentInstance().getMessages().hasNext();
	}
	
}
```

---

</SwmSnippet>

# Primefaces Showcase Endpoints

Understanding Primefaces Showcase Endpoints

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="16">

---

## /login Endpoint

The '/login' endpoint is mapped to a view controller. This means that when a user navigates to '/login', the application will render the 'login' view without any additional controller logic.

```xml
	<mvc:view-controller path="/login" />
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="18">

---

## /home Endpoint

Similarly, the '/home' endpoint is also mapped to a view controller. When a user navigates to '/home', the 'home' view is rendered.

```xml
	<mvc:view-controller path="/home" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
