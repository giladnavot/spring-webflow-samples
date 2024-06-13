---
title: Understanding Spring in the Primefaces-Showcase Project
---
Spring in the primefaces-showcase project refers to the Spring Framework, a powerful Java framework used for building enterprise-grade applications. It provides a comprehensive programming and configuration model.

In the servlet-context.xml file, Spring is used to enable the Spring MVC @Controller programming model and to serve classpath resources. This allows for the creation of web applications with less configuration and easy resource management.

In the webflow.xml file, Spring is used to execute flows, which is the central entry point into the Spring Web Flow system. It also configures the Spring Web Flow JSF integration and applies Spring Security authorities. This allows for the creation of complex user interfaces in a web application.

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="1">

---

# Spring Configuration Files

This is the Spring configuration file for controllers. It defines URL mappings for views and scans for components in the specified package.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:mvc="http://www.springframework.org/schema/mvc"
	xmlns:context="http://www.springframework.org/schema/context"
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd
		http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd">

	<!-- 
		URL mappings for views without controller logic.
		Example: 
			Incoming path '/home' is mapped maps to the view name 'home'
			UrlBasedViewResolver in servlet-context resolves 'home' to /WEB-INF/views/home.xhtml 
	-->
	<mvc:view-controller path="/login" />

	<mvc:view-controller path="/home" />

	<bean name="mvcHandlerMappingIntrospector"
		  class="org.springframework.web.servlet.handler.HandlerMappingIntrospector"/>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/security-config.xml" line="1">

---

# Spring Security Configuration

This is the Spring Security configuration file. It defines security constraints for different URL patterns and user roles.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<b:beans xmlns="http://www.springframework.org/schema/security"
		 xmlns:b="http://www.springframework.org/schema/beans"
		 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
						http://www.springframework.org/schema/security https://www.springframework.org/schema/security/spring-security.xsd">

	<b:bean id="expressionHandler"
			class="org.springframework.security.web.access.expression.DefaultWebSecurityExpressionHandler" />

	<http auto-config="true">
		<form-login login-page="/app/login" login-processing-url="/app/loginProcess"
			default-target-url="/app/home" authentication-failure-url="/app/login?login_error=1" />
		<logout logout-url="/app/logout" logout-success-url="/app/home" />
		<intercept-url pattern="/secured/appleUser" method="POST" access="hasRole('ROLE_APPLE_USER')" />
		<intercept-url pattern="/secured/androidUser" method="POST" access="hasRole('ROLE_ANDROID_USER')" />
		<intercept-url pattern="/**" access="permitAll"/>
		<csrf disabled="true" />
	</http>

	<user-service>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/webflow.xml" line="1">

---

# Spring Web Flow Configuration

This is the Spring Web Flow configuration file. It defines the flow executor and registry, and configures the Spring Web Flow JSF integration.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans:beans xmlns="http://www.springframework.org/schema/webflow-config"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:beans="http://www.springframework.org/schema/beans"
	xmlns:faces="http://www.springframework.org/schema/faces"
	xsi:schemaLocation="http://www.springframework.org/schema/webflow-config https://www.springframework.org/schema/webflow-config/spring-webflow-config.xsd
		http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/faces https://www.springframework.org/schema/faces/spring-faces.xsd">

	<!-- Executes flows: the central entry point into the Spring Web Flow system -->
	<flow-executor id="flowExecutor">
		<flow-execution-listeners>
			<listener ref="facesContextListener"/>
			<listener ref="securityListener"/>
		</flow-execution-listeners>
	</flow-executor>

	<!-- The registry of executable flow definitions -->
	<flow-registry id="flowRegistry" flow-builder-services="flowBuilderServices" base-path="/WEB-INF/flows">
		<flow-location-pattern value="/**/flow.xml" />
		<flow-location id="parent-flow" path="parent-flow.xml"/>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/servlet-context.xml" line="1">

---

# Spring Servlet Context Configuration

This is the Spring Servlet Context configuration file. It defines the DispatcherServlet's request-processing infrastructure, imports user-defined @Controller beans, and enables the Spring MVC @Controller programming model.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns:mvc="http://www.springframework.org/schema/mvc"
	xmlns:faces="http://www.springframework.org/schema/faces"
	xmlns:context="http://www.springframework.org/schema/context"
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
		http://www.springframework.org/schema/context https://www.springframework.org/schema/context/spring-context.xsd
		http://www.springframework.org/schema/faces https://www.springframework.org/schema/faces/spring-faces.xsd
		http://www.springframework.org/schema/mvc https://www.springframework.org/schema/mvc/spring-mvc.xsd">

	<!--
		DispatcherServlet Context: defines this servlet's request-processing infrastructure
	-->

	<!-- Imports user-defined @Controller beans that process client requests -->
	<import resource="controllers.xml" />
	<import resource="webflow.xml" />

	<!-- Scan for Spring beans declared via annotations. -->
	<context:component-scan base-package="org.springframework.samples.webflow"/>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/root-context.xml" line="1">

---

# Spring Root Context Configuration

This is the Spring Root Context configuration file. It defines shared resources visible to all other web components.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd">
	
	<!-- Root Context: defines shared resources visible to all other web components -->
	<import resource="security-config.xml"/>
	<import resource="servlet-context.xml"/>
	
</beans>
```

---

</SwmSnippet>

# Spring Endpoints

Spring Framework Endpoints

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="16">

---

## /login Endpoint

The `/login` endpoint is defined here. It is mapped to a view-controller, which means that when this endpoint is accessed, Spring will direct the user to the corresponding view without any additional controller logic.

```xml
	<mvc:view-controller path="/login" />
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/spring/controllers.xml" line="18">

---

## /home Endpoint

The `/home` endpoint is defined here. Similar to the `/login` endpoint, it is mapped to a view-controller. When this endpoint is accessed, the user is directed to the corresponding view.

```xml
	<mvc:view-controller path="/home" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
