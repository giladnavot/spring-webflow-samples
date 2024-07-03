---
title: Basic Concepts of Configuration
---
Config, short for configuration, in this repository refers to the setup and settings of various components of the application. It is represented by classes annotated with @Configuration, which indicate that the class can be used by the Spring IoC container as a source of bean definitions.

For instance, the SecurityConfig class is a configuration class that sets up the security filter chain and user details service. It defines the login and logout behaviors of the application.

Similarly, DataAccessConfig is a configuration class that sets up the transaction manager and entity manager factory for data access. It also configures the data source for the application.

WebFlowConfig is another configuration class that sets up the flow executor, flow registry, and flow builder services for the web flow of the application.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/SecurityConfig.java" line="12">

---

# SecurityConfig

The `SecurityConfig` class is used to configure the security settings of the application. It defines a `SecurityFilterChain` bean that sets up form login and logout settings. It also defines an `InMemoryUserDetailsManager` bean that sets up the users of the application.

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
		http
			.formLogin()
				.loginPage("/login")
				.loginProcessingUrl("/loginProcess")
				.defaultSuccessUrl("/hotels/search")
				.failureUrl("/login?login_error=1")
				.and()
			.logout()
				.logoutRequestMatcher(new AntPathRequestMatcher("/logout", "GET"))
				.logoutSuccessUrl("/logoutSuccess");
		return http.build();
	}

	@Bean
	public InMemoryUserDetailsManager userDetailsService() {
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/DataAccessConfig.java" line="18">

---

# DataAccessConfig

The `DataAccessConfig` class is used to configure the data access settings of the application. It defines beans for transaction management, entity manager factory, and data source.

```java
@Configuration
@EnableTransactionManagement
@ComponentScan(basePackages="org.springframework.webflow.samples.booking")
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

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="16">

---

# WebFlowConfig

The `WebFlowConfig` class is used to configure the web flow settings of the application. It defines beans for flow executor, flow definition registry, flow builder services, view factory creator, and validator.

```java
@Configuration
public class WebFlowConfig extends AbstractFlowConfiguration {

	@Autowired
	private WebMvcConfig webMvcConfig;

	@Bean
	public FlowExecutor flowExecutor() {
		return getFlowExecutorBuilder(flowRegistry())
				.addFlowExecutionListener(new SecurityFlowExecutionListener(), "*")
				.build();
	}

	@Bean
	public FlowDefinitionRegistry flowRegistry() {
		return getFlowDefinitionRegistryBuilder(flowBuilderServices())
				.setBasePath("/WEB-INF")
				.addFlowLocationPattern("/**/*-flow.xml").build();
	}

	@Bean
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
