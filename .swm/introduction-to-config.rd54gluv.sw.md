---
title: Introduction to Config
---
The 'Config' in the booking-mvc application refers to the configuration classes that set up the application's behavior. These classes are used to configure various aspects of the application such as security, data access, web MVC, and web flow. They are typically annotated with @Configuration and contain methods annotated with @Bean to provide instances of various objects required for the application.

For instance, the SecurityConfig class configures the security aspects of the application, such as form login and logout settings. The DataAccessConfig class sets up the data source and transaction management for the application. The WebMvcConfig and WebFlowConfig classes configure the MVC and Web Flow aspects of the application respectively.

These configuration classes are used in the DispatcherServletInitializer class, which sets up the DispatcherServlet for the application. The getRootConfigClasses method returns the configuration classes that should be loaded for the application.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="29">

---

# WebMvcConfig

The `WebMvcConfig` class configures the MVC settings for the application. It sets up resource handlers, default servlet handling, view controllers, and beans for handling web flows and views.

```java
@EnableWebMvc
@Configuration
public class WebMvcConfig implements WebMvcConfigurer, ServletContextAware {

	@Autowired
	private WebFlowConfig webFlowConfig;

	private ServletContext servletContext;

	@Override
	public void setServletContext(ServletContext servletContext) {
		this.servletContext = servletContext;
	}

	@Override
	public void addResourceHandlers(ResourceHandlerRegistry registry) {
		registry.addResourceHandler("/resources/**").addResourceLocations("/", "classpath:/META-INF/web-resources/");
	}

	@Override
	public void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer) {
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="1">

---

# WebFlowConfig

The `WebFlowConfig` class configures the web flow settings for the application. It sets up the flow executor, flow registry, flow builder services, view factory creator, and validator.

```java
package org.springframework.webflow.samples.booking.config;

import java.util.Collections;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.validation.beanvalidation.LocalValidatorFactoryBean;
import org.springframework.webflow.config.AbstractFlowConfiguration;
import org.springframework.webflow.definition.registry.FlowDefinitionRegistry;
import org.springframework.webflow.engine.builder.support.FlowBuilderServices;
import org.springframework.webflow.executor.FlowExecutor;
import org.springframework.webflow.mvc.builder.MvcViewFactoryCreator;
import org.springframework.webflow.security.SecurityFlowExecutionListener;

@Configuration
public class WebFlowConfig extends AbstractFlowConfiguration {

	@Autowired
	private WebMvcConfig webMvcConfig;

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/SecurityConfig.java" line="1">

---

# SecurityConfig

The `SecurityConfig` class configures the security settings for the application. It sets up the security filter chain and user details service.

```java
package org.springframework.webflow.samples.booking.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.provisioning.InMemoryUserDetailsManager;
import org.springframework.security.web.SecurityFilterChain;
import org.springframework.security.web.util.matcher.AntPathRequestMatcher;

@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http
			.formLogin()
				.loginPage("/login")
				.loginProcessingUrl("/loginProcess")
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/DataAccessConfig.java" line="1">

---

# DataAccessConfig

The `DataAccessConfig` class configures the data access settings for the application. It sets up the transaction manager, entity manager factory, and data source.

```java
package org.springframework.webflow.samples.booking.config;

import java.util.Collections;

import jakarta.persistence.EntityManagerFactory;
import javax.sql.DataSource;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.ComponentScan;
import org.springframework.context.annotation.Configuration;
import org.springframework.jdbc.datasource.DriverManagerDataSource;
import org.springframework.orm.jpa.JpaTransactionManager;
import org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean;
import org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter;
import org.springframework.transaction.PlatformTransactionManager;
import org.springframework.transaction.annotation.EnableTransactionManagement;

@Configuration
@EnableTransactionManagement
@ComponentScan(basePackages="org.springframework.webflow.samples.booking")
public class DataAccessConfig {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
