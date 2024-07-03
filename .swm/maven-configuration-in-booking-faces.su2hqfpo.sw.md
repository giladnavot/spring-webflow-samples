---
title: Maven Configuration in booking-faces
---
This document provides a detailed walkthrough of how Maven is used in the `booking-faces` module of the Spring Web Flow samples project.

<SwmSnippet path="/booking-faces/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts with the declaration of the project's basic information. The `modelVersion` is set to `4.0.0`, which is the latest model version for Maven. The `groupId` is `org.springframework.webflow.samples`, which is typically the project's domain name reversed. The `artifactId` is `booking-faces`, which is the name of the jar without version. The `packaging` type is `war`, indicating that the project will be packaged as a Web Application Resource (WAR). The `name` is a human-readable name for the project.

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
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/pom.xml" line="11">

---

# Parent Project

The `parent` tag is used to indicate the parent project from which this project inherits. The `groupId`, `artifactId`, and `version` of the parent project are specified. This allows the child project to inherit the dependencies and plugins defined in the parent project.

```xml
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

The `dependencies` section is where the dependencies required by the project are declared. Each `dependency` tag includes the `groupId`, `artifactId`, and `version` of the dependency. Some dependencies also have a `scope` tag, which is used to limit the dependency's scope. For example, a `scope` of `test` means the dependency is only required for compiling and running tests.

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

The `build` section is where the build configuration is specified. The `finalName` tag is used to set the name of the packaged artifact. The `plugins` section is where Maven plugins are configured. Each `plugin` tag includes the `groupId` and `artifactId` of the plugin, as well as a `configuration` section where plugin-specific configuration can be specified.

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

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="build-tool"><sup>Powered by [Swimm](/)</sup></SwmMeta>
