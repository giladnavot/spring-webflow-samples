---
title: Maven Configuration in booking-faces
---
This document provides a detailed walkthrough of how Maven is used in the `booking-faces` module of the Spring Web Flow samples repository.

<SwmSnippet path="/booking-faces/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts by defining the project information. It specifies the model version, group ID, artifact ID, packaging type, name, and version of the project. It also defines the parent project, which is `spring-webflow-samples`.

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
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/pom.xml" line="17">

---

# Dependencies

This section lists all the dependencies required by the `booking-faces` module. It includes dependencies for Spring, Servlet, JSF implementation, Database, JPA, JSR 303 with Hibernate Validator, JAXB2, Logging, and Testing. Each dependency is defined by its group ID, artifact ID, and version. Some dependencies also specify the scope.

```xml
	<dependencies>
		<!-- Spring -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-jdbc</artifactId>
		</dependency>				
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-orm</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.webflow</groupId>
			<artifactId>spring-binding</artifactId>
			<version>${webflow.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.webflow</groupId>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/pom.xml" line="162">

---

# Build Configuration

The build configuration section specifies the final name of the project and the plugins used. The plugins include the `maven-war-plugin`, `maven-compiler-plugin`, `maven-surefire-plugin`, and `jetty-maven-plugin`. Each plugin is defined by its group ID, artifact ID, version, and configuration.

```xml
	<build>
		<finalName>booking-faces</finalName>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>
				<version>3.1.0</version>
				<configuration>
					<failOnMissingWebXml>false</failOnMissingWebXml>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.7.0</version>
				<configuration>
					<source>17</source>
					<target>17</target>
				</configuration>
			</plugin>
			<plugin>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
