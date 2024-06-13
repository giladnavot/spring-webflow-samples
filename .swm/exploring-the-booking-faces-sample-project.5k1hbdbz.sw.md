---
title: Exploring the Booking Faces Sample Project
---
Booking Faces is a sample project in the Spring Web Flow samples repository. It is a web application that demonstrates the use of Spring Web Flow with JavaServer Faces (JSF). The application is a hotel booking system, where users can book rooms in hotels. The application uses various Spring technologies such as Spring MVC, Spring JDBC, and Spring ORM. It also uses other technologies such as Hibernate for ORM, Jakarta Servlet API, and PrimeFaces, a JSF component library.

<SwmSnippet path="/booking-faces/pom.xml" line="1">

---

# Maven Configuration for 'booking-faces'

This is the Maven configuration file for the 'booking-faces' module. It defines the module's dependencies, build configuration, and other project-specific settings. For instance, it specifies dependencies on various Spring modules, JSF implementation, database and JPA libraries, logging, and testing frameworks.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>org.springframework.webflow.samples</groupId>
	<artifactId>booking-faces</artifactId>
	<packaging>war</packaging>
	<name>Hotel Booking : Spring Web Flow with JSF</name>
	<version>1.0.0.BUILD-SNAPSHOT</version>

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

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
