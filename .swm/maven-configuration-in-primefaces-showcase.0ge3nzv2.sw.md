---
title: Maven Configuration in PrimeFaces Showcase
---
This document provides a detailed walkthrough of how Maven is used in the `primefaces-showcase` project. It focuses on the configuration and dependencies defined in the `pom.xml` file.

<SwmSnippet path="/primefaces-showcase/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts by defining the project information. The `modelVersion` is set to `4.0.0`, which is the version of the Project Object Model (POM) that this file is using. The `groupId`, `artifactId`, and `version` form the project's coordinates. In this case, the `artifactId` is `primefaces-showcase`, indicating that this is the configuration for the `primefaces-showcase` project. The `packaging` is set to `war`, meaning that the project will be packaged as a Web Application Archive (WAR) file.

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

The `parent` element is used to indicate that this project is a module of a larger project. The parent project is identified by its coordinates (`groupId`, `artifactId`, and `version`). Here, the parent project is `spring-webflow-samples`.

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

The `dependencies` section is where the project's dependencies are declared. Each `dependency` element specifies a library that the project needs to build and run. For example, the project depends on `spring-webmvc`, `spring-binding`, `spring-webflow`, and `spring-faces` from the `org.springframework` group, among others.

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

The `build` section is where the build configuration is specified. The `finalName` is set to `primefaces-showcase`, which will be the name of the generated artifact. The `plugins` section specifies plugins that provide additional build functionality. Here, the `maven-compiler-plugin` is configured to compile the project's sources with Java 1.8, and the `jetty-maven-plugin` is used to run the application on Jetty server.

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

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="build-tool"><sup>Powered by [Swimm](/)</sup></SwmMeta>
