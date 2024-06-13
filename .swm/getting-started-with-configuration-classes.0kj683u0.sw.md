---
title: Getting Started with Configuration Classes
---
The 'Config' in the booking-faces application refers to the configuration classes that set up the application's behavior. These classes are located in the 'config' package and include classes like 'DispatcherServletInitializer', 'SecurityConfig', 'AppConfig', and others. Each of these classes serves a specific purpose. For instance, 'DispatcherServletInitializer' sets up the DispatcherServlet, 'SecurityConfig' sets up the security aspects of the application, and 'AppConfig' is the main configuration class that imports other configuration classes.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/AppConfig.java" line="1">

---

## AppConfig

The `AppConfig` class is the central configuration class that imports other configuration classes. It uses the '@Import' annotation to include `DataAccessConfig`, `WebMvcConfig`, and `WebFlowConfig`.

```java
package org.springframework.webflow.samples.booking.config;

import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Import;

@Configuration
@ComponentScan(basePackages="org.springframework.webflow.samples.booking")
@Import(value={
		DataAccessConfig.class,
		WebMvcConfig.class,
		WebFlowConfig.class
	})
public class AppConfig {

}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="1">

---

## WebMvcConfig

The `WebMvcConfig` class configures the Spring MVC and integrates it with JSF and Spring Web Flow. It defines beans such as `FlowHandlerMapping`, `FlowHandlerAdapter`, and `UrlBasedViewResolver`.

```java
package org.springframework.webflow.samples.booking.config;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.faces.mvc.JsfView;
import org.springframework.faces.webflow.JsfFlowHandlerAdapter;
import org.springframework.web.servlet.mvc.SimpleControllerHandlerAdapter;
import org.springframework.web.servlet.mvc.UrlFilenameViewController;
import org.springframework.web.servlet.view.UrlBasedViewResolver;
import org.springframework.webflow.mvc.servlet.FlowHandlerAdapter;
import org.springframework.webflow.mvc.servlet.FlowHandlerMapping;


@Configuration
public class WebMvcConfig {

	@Autowired
	private WebFlowConfig webFlowConfig;

	@Bean
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="1">

---

## WebFlowConfig

The `WebFlowConfig` class configures the Spring Web Flow. It defines beans such as `FlowExecutor`, `FlowDefinitionRegistry`, and `FlowBuilderServices`.

```java
package org.springframework.webflow.samples.booking.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.faces.config.AbstractFacesFlowConfiguration;
import org.springframework.faces.webflow.FlowFacesContextLifecycleListener;
import org.springframework.webflow.definition.registry.FlowDefinitionRegistry;
import org.springframework.webflow.engine.builder.support.FlowBuilderServices;
import org.springframework.webflow.executor.FlowExecutor;
import org.springframework.webflow.security.SecurityFlowExecutionListener;

@Configuration
public class WebFlowConfig extends AbstractFacesFlowConfiguration {

	@Bean
	public FlowExecutor flowExecutor() {
		return getFlowExecutorBuilder(flowRegistry())
				.addFlowExecutionListener(new FlowFacesContextLifecycleListener())
				.addFlowExecutionListener(new SecurityFlowExecutionListener())
				.build();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/DataAccessConfig.java" line="1">

---

## DataAccessConfig

The `DataAccessConfig` class configures the data access layer of the application. It defines beans such as `PlatformTransactionManager`, `LocalContainerEntityManagerFactoryBean`, and `DataSource`.

```java
package org.springframework.webflow.samples.booking.config;

import java.util.Collections;

import jakarta.persistence.EntityManagerFactory;
import javax.sql.DataSource;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.jdbc.datasource.DriverManagerDataSource;
import org.springframework.orm.jpa.JpaTransactionManager;
import org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean;
import org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter;
import org.springframework.transaction.PlatformTransactionManager;
import org.springframework.transaction.annotation.EnableTransactionManagement;

@Configuration
@EnableTransactionManagement(proxyTargetClass=true)
public class DataAccessConfig {

	@Bean
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/SecurityConfig.java" line="1">

---

## SecurityConfig

The `SecurityConfig` class configures the security settings of the application. It defines beans such as `SecurityFilterChain` and `InMemoryUserDetailsManager`.

```java
package org.springframework.webflow.samples.booking.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.provisioning.InMemoryUserDetailsManager;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.savedrequest.HttpSessionRequestCache;

@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http
			.formLogin()
				.loginPage("/spring/login")
				.loginProcessingUrl("/spring/loginProcess")
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
