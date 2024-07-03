---
title: Getting Started with Configurations
---
Config in the spring-webflow-samples repository refers to the configuration classes that set up the application's behavior. These classes are annotated with @Configuration and they define beans that are managed by the Spring IoC container. For instance, SecurityConfig sets up the security filter chain, AppConfig sets up the application context, and DataAccessConfig sets up the data access layer. These classes are used to modularize the configuration and make it easier to manage.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/SecurityConfig.java" line="12">

---

# SecurityConfig

The `SecurityConfig` class configures the security aspects of the application. It defines a `SecurityFilterChain` bean that configures form login and logout behavior, and an `InMemoryUserDetailsManager` bean that defines the users for the application.

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http
			.formLogin()
				.loginPage("/spring/login")
				.loginProcessingUrl("/spring/loginProcess")
				.defaultSuccessUrl("/spring/main")
				.failureUrl("/spring/login?login_error=1")
				.and()
			.logout()
				.logoutUrl("/spring/logout")
				.logoutSuccessUrl("/spring/logoutSuccess")
				.and()
			.requestCache()
				.requestCache(new HttpSessionRequestCache());
		return http.build();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/AppConfig.java" line="7">

---

# AppConfig

The `AppConfig` class is the main configuration class for the application. It imports other configuration classes such as `DataAccessConfig`, `WebMvcConfig`, and `WebFlowConfig`.

```java
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

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/DataAccessConfig.java" line="17">

---

# DataAccessConfig

The `DataAccessConfig` class configures the data access aspects of the application. It defines beans for transaction management, entity manager factory, and data source.

```java
@Configuration
@EnableTransactionManagement(proxyTargetClass=true)
public class DataAccessConfig {

	@Bean
	public PlatformTransactionManager transactionManager(EntityManagerFactory emf) {
		JpaTransactionManager txManager = new JpaTransactionManager();
		txManager.setEntityManagerFactory(emf);
		return txManager;
	}

	@Bean
	public LocalContainerEntityManagerFactoryBean entityManagerFactory() {
		LocalContainerEntityManagerFactoryBean emf = new LocalContainerEntityManagerFactoryBean();
		emf.setDataSource(dataSource());
		emf.setJpaVendorAdapter(new HibernateJpaVendorAdapter());
		emf.setJpaPropertyMap(Collections.singletonMap("hibernate.session_factory_name", "mySessionFactory"));
		return emf;
	}

	@Bean
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="12">

---

# WebFlowConfig

The `WebFlowConfig` class configures the web flow aspects of the application. It defines beans for flow executor, flow definition registry, and flow builder services.

```java
@Configuration
public class WebFlowConfig extends AbstractFacesFlowConfiguration {

	@Bean
	public FlowExecutor flowExecutor() {
		return getFlowExecutorBuilder(flowRegistry())
				.addFlowExecutionListener(new FlowFacesContextLifecycleListener())
				.addFlowExecutionListener(new SecurityFlowExecutionListener())
				.build();
	}

	@Bean
	public FlowDefinitionRegistry flowRegistry() {
		return getFlowDefinitionRegistryBuilder(flowBuilderServices())
				.setBasePath("/WEB-INF/flows")
				.addFlowLocationPattern("/**/*-flow.xml")
				.build();
	}

	@Bean
	public FlowBuilderServices flowBuilderServices() {
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="15">

---

# WebMvcConfig

The `WebMvcConfig` class configures the web MVC aspects of the application. It defines beans for flow handler mapping, flow handler adapter, view resolver, and controller handler adapter.

```java
@Configuration
public class WebMvcConfig {

	@Autowired
	private WebFlowConfig webFlowConfig;

	@Bean
	public FlowHandlerMapping flowHandlerMapping() {
		FlowHandlerMapping mapping = new FlowHandlerMapping();
		mapping.setOrder(1);
		mapping.setFlowRegistry(this.webFlowConfig.flowRegistry());
		/* If no flow matches, map the path to a view, e.g. "/intro" maps to a view named "intro" */
		mapping.setDefaultHandler(new UrlFilenameViewController());
		return mapping;
	}

	@Bean
	public FlowHandlerAdapter flowHandlerAdapter() {
		JsfFlowHandlerAdapter adapter = new JsfFlowHandlerAdapter();
		adapter.setFlowExecutor(this.webFlowConfig.flowExecutor());
		return adapter;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
