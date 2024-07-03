---
title: Maven Configuration and Usage in Spring Web Flow Samples
---
This document provides a detailed walkthrough of how Maven is used in the Spring Web Flow Samples project. It focuses on the configuration and usage of Maven as specified in the <SwmPath>[pom.xml](/pom.xml)</SwmPath> file.

<SwmSnippet path="/pom.xml" line="1">

---

# Project Information

The <SwmPath>[pom.xml](/pom.xml)</SwmPath> file starts with the project information. It specifies the model version, group ID, artifact ID, packaging type, name, and version of the project. This information is used by Maven to identify the project.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>org.springframework.webflow</groupId>
	<artifactId>spring-webflow-samples</artifactId>
	<packaging>pom</packaging>
	<name>Spring Web Flow Samples</name>
	<version>1.0.0.BUILD-SNAPSHOT</version>
```

---

</SwmSnippet>

<SwmSnippet path="/pom.xml" line="11">

---

# Modules

The <SwmToken path="/pom.xml" pos="11:2:2" line-data="	&lt;modules&gt;">`modules`</SwmToken> section lists the modules that make up the project. Each module represents a sub-project and has its own <SwmPath>[pom.xml](/pom.xml)</SwmPath> file. Maven builds each module in the order they are listed.

```xml
	<modules>
		<module>booking-mvc</module>
		<module>booking-faces</module>
		<module>primefaces-showcase</module>
		<!--
		<module>webflow-showcase</module>
		-->
	</modules>
```

---

</SwmSnippet>

<SwmSnippet path="/pom.xml" line="20">

---

# Properties

The <SwmToken path="/pom.xml" pos="20:2:2" line-data="	&lt;properties&gt;">`properties`</SwmToken> section defines project-wide properties that can be referenced elsewhere in the <SwmPath>[pom.xml](/pom.xml)</SwmPath>. These properties include versions of dependencies and plugins. For example, the <SwmToken path="/pom.xml" pos="27:2:8" line-data="		&lt;jetty-maven-plugin.version&gt;11.0.11&lt;/jetty-maven-plugin.version&gt;">`jetty-maven-plugin.version`</SwmToken> property is set to <SwmToken path="/pom.xml" pos="27:10:14" line-data="		&lt;jetty-maven-plugin.version&gt;11.0.11&lt;/jetty-maven-plugin.version&gt;">`11.0.11`</SwmToken>.

```xml
	<properties>
		<easymock.version>3.4</easymock.version>
		<cdi-api>4.0.1</cdi-api>
		<hsqldb.version>2.5.1</hsqldb.version>
		<hibernate.version>5.6.15.Final</hibernate.version>
		<hibernate-validator.version>8.0.0.Final</hibernate-validator.version>
		<jaxb.version>2.2.3</jaxb.version>
		<jetty-maven-plugin.version>11.0.11</jetty-maven-plugin.version>
		<jsp-api.version>3.1.0</jsp-api.version>
		<jstl-api>3.0.0</jstl-api>
		<junit.version>4.13.2</junit.version>
		<log4j.version>2.14.0</log4j.version>
		<mojarra.version>4.0.2</mojarra.version>
		<myfaces.version>4.0.0</myfaces.version>
		<primefaces.version>11.0.0</primefaces.version>
		<servlet.version>6.0.0</servlet.version>
		<webflow.version>3.0.0</webflow.version>
		<weld.version>5.0.0.Final</weld.version>
		<maven-surefire-plugin.version>2.22.2</maven-surefire-plugin.version>
	</properties>
```

---

</SwmSnippet>

<SwmSnippet path="/pom.xml" line="41">

---

# Dependency Management

The <SwmToken path="/pom.xml" pos="41:2:2" line-data="	&lt;dependencyManagement&gt;">`dependencyManagement`</SwmToken> section is used to manage the versions of dependencies. Dependencies defined here are not directly included in the project, but their versions are controlled so that all modules will use the same version of a dependency.

```xml
	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework</groupId>
				<artifactId>spring-framework-bom</artifactId>
				<version>6.0.10</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
			<dependency>
				<groupId>org.springframework.security</groupId>
				<artifactId>spring-security-bom</artifactId>
				<type>pom</type>
				<scope>import</scope>
				<version>6.0.2</version>
			</dependency>
			<dependency>
				<groupId>org.slf4j</groupId>
				<artifactId>slf4j-api</artifactId>
				<version>2.0.6</version>
			</dependency>
```

---

</SwmSnippet>

<SwmSnippet path="/pom.xml" line="65">

---

# Repositories

The <SwmToken path="/pom.xml" pos="65:2:2" line-data="	&lt;repositories&gt;">`repositories`</SwmToken> section defines where Maven should look for dependencies that are not in the central Maven repository. In this case, it includes the Spring Snapshot Repository and the Spring Milestone Repository.

```xml
	<repositories>
		<repository>
			<id>spring-snapshot</id>
			<name>Spring Snapshot Repository</name>
			<url>https://repo.spring.io/snapshot</url>
		</repository>
		<repository>
			<id>spring-milestone</id>
			<name>Spring Milestone Repository</name>
			<url>https://repo.spring.io/milestone</url>
		</repository>
	</repositories>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://app.swimm.io/)</sup></SwmMeta>
