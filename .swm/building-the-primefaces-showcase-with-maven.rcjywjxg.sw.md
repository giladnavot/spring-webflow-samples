---
title: Building the PrimeFaces Showcase with Maven
---
This document provides a detailed walkthrough of how Maven is used in the PrimeFaces Showcase project, focusing on the configuration and dependencies defined in the `pom.xml` file.

<SwmSnippet path="/primefaces-showcase/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts with the project information. The `modelVersion` is set to `4.0.0`, which is the standard for Maven 2 and later. The `groupId` is `org.springframework.webflow.samples`, and the `artifactId` is `primefaces-showcase`. The `packaging` type is `war`, indicating that the project will be packaged as a Web Application Archive (WAR) file.

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
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/pom.xml" line="11">

---

# Parent Project

The `parent` element specifies the parent project from which this project inherits. The parent project is `spring-webflow-samples` from the `org.springframework.webflow` group.

```xml
	<parent>
		<groupId>org.springframework.webflow</groupId>
		<artifactId>spring-webflow-samples</artifactId>
		<version>1.0.0.BUILD-SNAPSHOT</version>
	</parent>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/pom.xml" line="17">

---

# Dependencies

The `dependencies` section lists all the dependencies required by the project. These include various Spring, Servlet, JSF, PrimeFaces, and logging libraries. Each dependency is specified with a `groupId`, `artifactId`, and `version`.

```xml
	<dependencies>
		<!-- Spring -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.webflow</groupId>
			<artifactId>spring-binding</artifactId>
			<version>${webflow.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.webflow</groupId>
			<artifactId>spring-webflow</artifactId>
			<version>${webflow.version}</version>
		</dependency>
		<dependency>
			<groupId>org.springframework.webflow</groupId>
			<artifactId>spring-faces</artifactId>
			<version>${webflow.version}</version>
		</dependency>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/pom.xml" line="125">

---

# Build Configuration

The `build` section configures aspects related to the build process. The `finalName` is set to `primefaces-showcase`, which will be the name of the generated WAR file. The `plugins` section includes the `maven-compiler-plugin` for compiling the source code and the `jetty-maven-plugin` for running the application on Jetty server.

```xml
	<build>
		<finalName>primefaces-showcase</finalName>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.7.0</version>
				<configuration>
					<source>1.8</source>
					<target>1.8</target>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.eclipse.jetty</groupId>
				<artifactId>jetty-maven-plugin</artifactId>
				<version>${jetty-maven-plugin.version}</version>
				<configuration>
					<webApp>
						<contextPath>/${project.artifactId}</contextPath>
					</webApp>
				</configuration>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
