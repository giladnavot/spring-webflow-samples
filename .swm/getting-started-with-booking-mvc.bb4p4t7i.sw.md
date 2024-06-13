---
title: Getting Started with Booking MVC
---
Booking MVC is a sub-project within the spring-webflow-samples repository. It's a Spring MVC application that demonstrates a typical booking scenario for a hotel. The application uses Spring Web Flow for the booking process and Spring MVC for search and display of hotel information. It also integrates with Spring Security for authentication and authorization, and Hibernate for persistence.

<SwmSnippet path="/booking-mvc/pom.xml" line="17">

---

# Booking MVC Dependencies

This section of the pom.xml file lists the dependencies required for the Booking MVC application. It includes Spring MVC, Spring JDBC, Spring ORM, Spring Web Flow, and other necessary libraries.

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

# Building Booking MVC

This section of the pom.xml file defines the build configuration for the Booking MVC application. It specifies the final name of the build and the plugins used during the build process.

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
