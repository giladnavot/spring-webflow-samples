---
title: Overview of the Primefaces Showcase
---
Primefaces showcase is a project within the Spring Web Flow samples. It demonstrates the integration of Spring Web Flow with PrimeFaces, a popular JavaServer Faces (JSF) library. The project is packaged as a war file, indicating it's a web application that can be deployed on any Java-based server. The PrimeFaces library is included as a dependency in the project's Maven configuration, allowing the project to use PrimeFaces' rich set of UI components.

<SwmSnippet path="/primefaces-showcase/pom.xml" line="1">

---

# Primefaces Showcase Project Structure

The `pom.xml` file defines the project structure, dependencies, and build configuration. It specifies that this is a Maven project, with a group ID of `org.springframework.webflow.samples` and an artifact ID of `primefaces-showcase`. The project is packaged as a war, and is versioned as `1.0.0-BUILD-SNAPSHOT`.

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

<SwmSnippet path="/primefaces-showcase/pom.xml" line="84">

---

# Primefaces Dependency

The Primefaces library is included as a dependency in the project. The version of Primefaces used is specified by the `primefaces.version` property.

```xml
		<dependency>
			<groupId>org.primefaces</groupId>
			<artifactId>primefaces</artifactId>
			<version>${primefaces.version}</version>
			<classifier>jakarta</classifier>
		</dependency>
```

---

</SwmSnippet>

<SwmSnippet path="/pom.xml" line="34">

---

# Primefaces Version

The `primefaces.version` property is defined in the parent `pom.xml` file. In this case, the version of Primefaces being used is `11.0.0`.

```xml
		<primefaces.version>11.0.0</primefaces.version>
```

---

</SwmSnippet>

# Primefaces Showcase Endpoints

Understanding Primefaces Showcase Endpoints

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="16">

---

## /login Endpoint

The '/login' endpoint is defined in the controllers.xml file. This endpoint is mapped to a view without any controller logic, meaning that when a user navigates to '/login', they are presented with the 'login' view.

```xml
	<mvc:view-controller path="/login" />

```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="18">

---

## /home Endpoint

Similarly, the '/home' endpoint is also defined in the controllers.xml file. This endpoint is mapped to the 'home' view, which is displayed when a user navigates to '/home'.

```xml
	<mvc:view-controller path="/home" />

```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
