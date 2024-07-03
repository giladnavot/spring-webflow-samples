---
title: Basic Concepts of Web Flow Config
---
Web flow config in the Spring Web Flow framework refers to the configuration of the web flow within an application. It is typically defined in a class annotated with `@Configuration` that extends `AbstractFlowConfiguration`. This class defines beans for `FlowExecutor`, `FlowDefinitionRegistry`, and `FlowBuilderServices` which are essential components of the web flow system. `FlowExecutor` is responsible for executing flow definitions, `FlowDefinitionRegistry` is a registry of flow definitions, and `FlowBuilderServices` is a configuration holder for resources needed to build flow definitions. The `WebFlowConfig` class also defines the base path and pattern for locating flow definitions in the application.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="16">

---

# WebFlowConfig Class

This is the WebFlowConfig class. It extends the AbstractFlowConfiguration class and is annotated with @Configuration, indicating that it is a configuration class. It contains several methods annotated with @Bean, each of which defines a specific component of the web flow configuration.

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

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="22">

---

# FlowExecutor Bean

This is the flowExecutor bean. It is responsible for executing web flows. It is configured with a flow registry and a security flow execution listener.

```java
	@Bean
	public FlowExecutor flowExecutor() {
		return getFlowExecutorBuilder(flowRegistry())
				.addFlowExecutionListener(new SecurityFlowExecutionListener(), "*")
				.build();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="29">

---

# FlowDefinitionRegistry Bean

This is the flowRegistry bean. It is responsible for storing the flow definitions. It is configured with a base path and a flow location pattern, which are used to locate the flow definition files.

```java
	@Bean
	public FlowDefinitionRegistry flowRegistry() {
		return getFlowDefinitionRegistryBuilder(flowBuilderServices())
				.setBasePath("/WEB-INF")
				.addFlowLocationPattern("/**/*-flow.xml").build();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="36">

---

# FlowBuilderServices Bean

This is the flowBuilderServices bean. It is responsible for building the flow definitions. It is configured with a view factory creator and a validator, and is set to development mode.

```java
	@Bean
	public FlowBuilderServices flowBuilderServices() {
		return getFlowBuilderServicesBuilder()
				.setViewFactoryCreator(mvcViewFactoryCreator())
				.setValidator(validator())
				.setDevelopmentMode(true)
				.build();
	}
```

---

</SwmSnippet>

# Web Flow Configuration Functions

The WebFlowConfig class contains several important methods that are used to configure the Spring Web Flow.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="23">

---

## FlowExecutor

The `flowExecutor` method is responsible for creating a FlowExecutor instance. This instance is responsible for executing flow definitions. The method adds a SecurityFlowExecutionListener to the executor, which is used to integrate Spring Security into the flow execution.

```java
	public FlowExecutor flowExecutor() {
		return getFlowExecutorBuilder(flowRegistry())
				.addFlowExecutionListener(new SecurityFlowExecutionListener(), "*")
				.build();
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="30">

---

## FlowDefinitionRegistry

The `flowRegistry` method is responsible for creating a FlowDefinitionRegistry instance. This registry contains all the flow definitions in the application. The method sets the base path for the flows and adds a pattern for locating the flow definitions.

```java
	public FlowDefinitionRegistry flowRegistry() {
		return getFlowDefinitionRegistryBuilder(flowBuilderServices())
				.setBasePath("/WEB-INF")
				.addFlowLocationPattern("/**/*-flow.xml").build();
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="37">

---

## FlowBuilderServices

The `flowBuilderServices` method is responsible for creating a FlowBuilderServices instance. This instance is used to configure the services that will be used by the flow builders. The method sets the view factory creator, the validator, and enables the development mode.

```java
	public FlowBuilderServices flowBuilderServices() {
		return getFlowBuilderServicesBuilder()
				.setViewFactoryCreator(mvcViewFactoryCreator())
				.setValidator(validator())
				.setDevelopmentMode(true)
				.build();
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="46">

---

## MvcViewFactoryCreator

The `mvcViewFactoryCreator` method is responsible for creating a MvcViewFactoryCreator instance. This instance is used to create views for the MVC framework. The method sets the view resolvers and enables the use of Spring bean binding.

```java
	public MvcViewFactoryCreator mvcViewFactoryCreator() {
		MvcViewFactoryCreator factoryCreator = new MvcViewFactoryCreator();
		factoryCreator.setViewResolvers(Collections.singletonList(this.webMvcConfig.thymeleafViewResolver()));
		factoryCreator.setUseSpringBeanBinding(true);
		return factoryCreator;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebFlowConfig.java" line="54">

---

## Validator

The `validator` method is responsible for creating a LocalValidatorFactoryBean instance. This instance is used to validate the data in the application.

```java
	public LocalValidatorFactoryBean validator() {
		return new LocalValidatorFactoryBean();
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
