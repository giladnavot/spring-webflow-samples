---
title: Introduction to Webflow Showcase
---
Webflow showcase is a project within the Spring Web Flow samples. It's a Maven project, as indicated by the pom.xml file, and it's packaged as a war file. This project is designed to demonstrate the capabilities of Spring Web Flow, a framework for building web applications in Spring. It includes dependencies on various Spring modules, such as spring-webmvc, spring-jdbc, and spring-orm, as well as on Spring Web Flow itself. The project also uses Apache Tiles for layout, Hibernate Validator for JSR 303 validation, and Log4j for logging.

<SwmSnippet path="/webflow-showcase/pom.xml" line="1">

---

# Project Configuration

This is the Maven Project Object Model (POM) for the Webflow showcase. It defines the project structure, dependencies, and build configuration. Key dependencies include Spring Web MVC, Spring JDBC, Spring ORM, and Spring Web Flow. The build section specifies the use of the Maven Compiler Plugin and the Jetty Maven Plugin.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>org.springframework.webflow.samples</groupId>
	<artifactId>webflow-showcase</artifactId>
	<name>Spring Web Flow Showcase</name>
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

# Webflow Showcase Endpoints

Understanding the Webflow Showcase Endpoints

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="15">

---

## Root Endpoint (/)

The root endpoint (/) is mapped directly to the 'home' view without any controller processing. This means when the application is accessed from the root URL, the 'home' view is returned to the client.

```xml
	<mvc:view-controller path="/" view-name="home" />
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="16">

---

## Embedded Flow Container Endpoint (/embeddedFlowContainer)

The /embeddedFlowContainer endpoint is also mapped directly to a view with the same name. This endpoint is used to access the 'embeddedFlowContainer' view.

```xml
	<mvc:view-controller path="/embeddedFlowContainer" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
