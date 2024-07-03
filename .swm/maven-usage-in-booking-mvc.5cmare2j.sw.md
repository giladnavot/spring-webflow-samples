---
title: Maven Usage in booking-mvc
---
This document covers the usage of Maven in the context of the `booking-mvc` project within the `spring-webflow-samples` repository.

<SwmSnippet path="/booking-mvc/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts with the declaration of the project's basic information. The `modelVersion` is set to `4.0.0`, which is the latest model version of Maven. The `groupId` is `org.springframework.webflow.samples`, and the `artifactId` is `booking-mvc`, which together uniquely identify the project in the Maven repository. The `packaging` type is set to `war`, indicating that the project will be packaged as a Web Application Archive. The `name` of the project is `Hotel Booking : Spring MVC + Web Flow + JSP`.

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
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/pom.xml" line="11">

---

# Parent Project

The `parent` tag is used to indicate that this Maven project is a child of another Maven project. The parent project is identified by its `groupId`, `artifactId`, and `version`. In this case, the parent project is `spring-webflow-samples`.

```xml
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

The `dependencies` section lists all the libraries that are needed to build and run the project. Each `dependency` is identified by its `groupId`, `artifactId`, and `version`. Some dependencies also have a `scope` which can be `compile`, `provided`, `runtime`, `test`, `system`, or `import`. The `compile` scope is the default scope, used if none is specified.

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

The `build` section defines how the project should be built. The `finalName` is the name of the generated artifact. The `plugins` section lists the Maven plugins that are used during the build process. Each plugin can have its own `configuration`.

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

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="build-tool"><sup>Powered by [Swimm](/)</sup></SwmMeta>
