---
title: Understanding the Web MVC Configuration
---
Web MVC Config in the context of this repository refers to the configuration class `WebMvcConfig` that is responsible for setting up the MVC infrastructure for the Spring Web Flow application. It is annotated with `@EnableWebMvc` and `@Configuration`, indicating that it is a configuration class that enables Spring's MVC support. This class implements `WebMvcConfigurer` and `ServletContextAware`, allowing it to customize the provided default configurations and access the `ServletContext`.

The `WebMvcConfig` class is responsible for defining several beans and configurations. For instance, it defines a `FlowHandlerMapping` bean that maps requests to flows, a `FlowHandlerAdapter` bean that adapts flow handling methods to the DispatcherServlet's handler method contracts, and a `BookingFlowHandler` bean that handles booking flows. It also configures resource handlers, view controllers, and the default servlet handling.

Moreover, `WebMvcConfig` sets up Thymeleaf as the template engine for the application. It defines a `SpringTemplateEngine` bean and a `WebApplicationTemplateResolver` bean. The template resolver is configured to resolve templates located in the `/WEB-INF/` directory with a `.html` suffix and HTML5 template mode.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="29">

---

# WebMvcConfig Class

This is the WebMvcConfig class. It implements WebMvcConfigurer and ServletContextAware, allowing it to configure Spring MVC and access the ServletContext. It defines several beans such as FlowHandlerMapping, FlowHandlerAdapter, and AjaxThymeleafViewResolver, which are necessary for the application to function.

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

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="44">

---

# Resource Handlers

This method configures resource handlers for serving static resources. It maps '/resources/\*\*' to the root of the classpath and the '/META-INF/web-resources/' directory in the classpath.

```java
	public void addResourceHandlers(ResourceHandlerRegistry registry) {
		registry.addResourceHandler("/resources/**").addResourceLocations("/", "classpath:/META-INF/web-resources/");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="54">

---

# View Controllers

This method adds view controllers to the registry. It maps the root URL ('/') to the 'intro' view, and also maps '/login' and '/logoutSuccess' to their respective views.

```java
	public void addViewControllers(ViewControllerRegistry registry) {
		registry.addViewController("/").setViewName("intro");
		registry.addViewController("/login");
		registry.addViewController("/logoutSuccess");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="60">

---

# FlowHandlerMapping Bean

This method defines a FlowHandlerMapping bean. It sets the order of the handler mapping and sets the flow registry to the one defined in WebFlowConfig.

```java
	@Bean
	public FlowHandlerMapping flowHandlerMapping() {
		FlowHandlerMapping handlerMapping = new FlowHandlerMapping();
		handlerMapping.setOrder(-1);
		handlerMapping.setFlowRegistry(this.webFlowConfig.flowRegistry());
		return handlerMapping;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="68">

---

# FlowHandlerAdapter Bean

This method defines a FlowHandlerAdapter bean. It sets the flow executor to the one defined in WebFlowConfig and enables saving output to flash scope on redirect.

```java
	@Bean
	public FlowHandlerAdapter flowHandlerAdapter() {
		FlowHandlerAdapter handlerAdapter = new FlowHandlerAdapter();
		handlerAdapter.setFlowExecutor(this.webFlowConfig.flowExecutor());
		handlerAdapter.setSaveOutputToFlashScopeOnRedirect(true);
		return handlerAdapter;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="81">

---

# AjaxThymeleafViewResolver Bean

This method defines an AjaxThymeleafViewResolver bean. It sets the view class to FlowAjaxThymeleafView and sets the template engine to the one defined in this class.

```java
	@Bean
	public AjaxThymeleafViewResolver thymeleafViewResolver() {
		AjaxThymeleafViewResolver viewResolver = new AjaxThymeleafViewResolver();
		viewResolver.setViewClass(FlowAjaxThymeleafView.class);
		viewResolver.setTemplateEngine(templateEngine());
		return viewResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="89">

---

# SpringTemplateEngine Bean

This method defines a SpringTemplateEngine bean. It adds the SpringSecurityDialect to the set of dialects and sets the template resolver to the one defined in this class.

```java
	@Bean
	public SpringTemplateEngine templateEngine(){

		Set<IDialect> dialects = new LinkedHashSet<>();
		dialects.add(new SpringSecurityDialect());

		SpringTemplateEngine templateEngine = new SpringTemplateEngine();
		templateEngine.setTemplateResolver(templateResolver());
		templateEngine.setAdditionalDialects(dialects);
		return templateEngine;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="101">

---

# WebApplicationTemplateResolver Bean

This method defines a WebApplicationTemplateResolver bean. It sets the prefix, suffix, and template mode of the resolver.

```java
	@Bean
	public WebApplicationTemplateResolver templateResolver() {
		IWebApplication application = JakartaServletWebApplication.buildApplication(this.servletContext);
		WebApplicationTemplateResolver resolver = new WebApplicationTemplateResolver(application);
		resolver.setPrefix("/WEB-INF/");
		resolver.setSuffix(".html");
		resolver.setTemplateMode("HTML5");
		return resolver;
	}
```

---

</SwmSnippet>

# WebMvcConfig Functions

This section provides an overview of the main functions in the WebMvcConfig class.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="38">

---

## setServletContext

The `setServletContext` function is used to set the ServletContext that this object runs in. This is invoked after population of normal bean properties but before an init callback.

```java
	@Override
	public void setServletContext(ServletContext servletContext) {
		this.servletContext = servletContext;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="43">

---

## addResourceHandlers

The `addResourceHandlers` function is used to add resource handlers for serving static resources.

```java
	@Override
	public void addResourceHandlers(ResourceHandlerRegistry registry) {
		registry.addResourceHandler("/resources/**").addResourceLocations("/", "classpath:/META-INF/web-resources/");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="48">

---

## configureDefaultServletHandling

The `configureDefaultServletHandling` function is used to configure a handler to delegate unhandled requests by forwarding to the Servlet container's default Servlet.

```java
	@Override
	public void configureDefaultServletHandling(DefaultServletHandlerConfigurer configurer) {
		configurer.enable();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="53">

---

## addViewControllers

The `addViewControllers` function is used to add simple automated controllers pre-configured with the response status code and/or a view to render the response body.

```java
	@Override
	public void addViewControllers(ViewControllerRegistry registry) {
		registry.addViewController("/").setViewName("intro");
		registry.addViewController("/login");
		registry.addViewController("/logoutSuccess");
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="60">

---

## flowHandlerMapping

The `flowHandlerMapping` function is used to create a FlowHandlerMapping bean. This bean maps requests to flows in the web application.

```java
	@Bean
	public FlowHandlerMapping flowHandlerMapping() {
		FlowHandlerMapping handlerMapping = new FlowHandlerMapping();
		handlerMapping.setOrder(-1);
		handlerMapping.setFlowRegistry(this.webFlowConfig.flowRegistry());
		return handlerMapping;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="68">

---

## flowHandlerAdapter

The `flowHandlerAdapter` function is used to create a FlowHandlerAdapter bean. This bean adapts requests mapped to a flow to the FlowExecutor for execution.

```java
	@Bean
	public FlowHandlerAdapter flowHandlerAdapter() {
		FlowHandlerAdapter handlerAdapter = new FlowHandlerAdapter();
		handlerAdapter.setFlowExecutor(this.webFlowConfig.flowExecutor());
		handlerAdapter.setSaveOutputToFlashScopeOnRedirect(true);
		return handlerAdapter;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="76">

---

## BookingFlowHandler

The `BookingFlowHandler` function is used to create a BookingFlowHandler bean. This bean is a custom flow handler for the booking flow.

```java
	@Bean(name="hotels/booking")
	public BookingFlowHandler BookingFlowHandler() {
		return new BookingFlowHandler();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="81">

---

## thymeleafViewResolver

The `thymeleafViewResolver` function is used to create a Thymeleaf view resolver bean. This bean resolves views selected for rendering by @Controllers to Thymeleaf templates.

```java
	@Bean
	public AjaxThymeleafViewResolver thymeleafViewResolver() {
		AjaxThymeleafViewResolver viewResolver = new AjaxThymeleafViewResolver();
		viewResolver.setViewClass(FlowAjaxThymeleafView.class);
		viewResolver.setTemplateEngine(templateEngine());
		return viewResolver;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="89">

---

## templateEngine

The `templateEngine` function is used to create a Thymeleaf template engine bean. This bean processes the Thymeleaf templates and produces the output that can be served to the client.

```java
	@Bean
	public SpringTemplateEngine templateEngine(){

		Set<IDialect> dialects = new LinkedHashSet<>();
		dialects.add(new SpringSecurityDialect());

		SpringTemplateEngine templateEngine = new SpringTemplateEngine();
		templateEngine.setTemplateResolver(templateResolver());
		templateEngine.setAdditionalDialects(dialects);
		return templateEngine;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="101">

---

## templateResolver

The `templateResolver` function is used to create a Thymeleaf template resolver bean. This bean resolves Thymeleaf templates in the application.

```java
	@Bean
	public WebApplicationTemplateResolver templateResolver() {
		IWebApplication application = JakartaServletWebApplication.buildApplication(this.servletContext);
		WebApplicationTemplateResolver resolver = new WebApplicationTemplateResolver(application);
		resolver.setPrefix("/WEB-INF/");
		resolver.setSuffix(".html");
		resolver.setTemplateMode("HTML5");
		return resolver;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
