---
title: Maven Configuration in booking-mvc
---
This document provides a detailed walkthrough of how Maven is used in the `booking-mvc` module of the Spring Web Flow samples repository.

<SwmSnippet path="/booking-mvc/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts by defining the project information. It specifies the model version, group ID, artifact ID, packaging type, name, and version of the project. It also defines the parent project, which is `spring-webflow-samples`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>org.springframework.webflow.samples</groupId>
	<artifactId>booking-mvc</artifactId>
	<packaging>war</packaging>
	<name>Hotel Booking : Spring MVC + Web Flow + JSP</name>
	<version>1.0.0.BUILD-SNAPSHOT</version>

	<parent>
		<groupId>org.springframework.webflow</groupId>
		<artifactId>spring-webflow-samples</artifactId>
		<version>1.0.0.BUILD-SNAPSHOT</version>
	</parent>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/pom.xml" line="17">

---

# Dependencies

This section of the `pom.xml` file lists all the dependencies required for the `booking-mvc` module. These dependencies include various Spring modules, Servlet API, JSP API, Thymeleaf, Hibernate, Joda Time, Logging, and Testing libraries.

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
			<artifactId>spring-webflow</artifactId>
			<version>${webflow.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.webflow</groupId>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/pom.xml" line="176">

---

# Build Configuration

The build configuration section specifies the final name of the build output and the plugins used during the build process. The plugins include the Maven WAR plugin, the Maven Compiler plugin, the Maven Surefire plugin, and the Jetty Maven plugin.

```xml
	<build>
		<finalName>booking-mvc</finalName>
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
				<version>3.10.1</version>
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
