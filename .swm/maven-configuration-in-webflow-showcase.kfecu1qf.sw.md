---
title: Maven Configuration in webflow-showcase
---
This document provides a detailed walkthrough of how Maven is used in the webflow-showcase project.

<SwmSnippet path="/webflow-showcase/pom.xml" line="1">

---

# Project Information

The `pom.xml` file starts by defining the project's basic information. The `modelVersion` is set to `4.0.0`, which is the standard for Maven 2 and later. The `groupId`, `artifactId`, and `version` together form the project's fully qualified artifact name. In this case, the artifact produced by this project will be `webflow-showcase-1.0.0-BUILD-SNAPSHOT.war`.

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
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/pom.xml" line="11">

---

# Parent Project

The `parent` element is used to indicate this project's parent project. The parent project is `spring-webflow-samples`, and it's used to inherit common configurations.

```xml
	<parent>
		<groupId>org.springframework.webflow</groupId>
		<artifactId>spring-webflow-samples</artifactId>
		<version>1.0.0.BUILD-SNAPSHOT</version>
	</parent>
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/pom.xml" line="17">

---

# Dependencies

The `dependencies` section is where the project's dependencies are defined. These dependencies will be included in the classpath during compilation and can also be packaged with the application.

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

<SwmSnippet path="/webflow-showcase/pom.xml" line="94">

---

# Build Configuration

The `build` section defines project-specific build settings. Here, two plugins are configured: `maven-compiler-plugin` for compiling sources and `jetty-maven-plugin` for running the application on Jetty server.

```xml
	<build>
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
			</plugin>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
