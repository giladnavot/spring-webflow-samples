---
title: Communication between JSF Components and the Server Side
---
This document will cover the process of how JSF components communicate with the server side in the Spring Web Flow application. The topics covered include:

1. The role of JSF components in the application
2. How JSF components interact with the server side
3. The flow of data between JSF components and the server.

<SwmSnippet path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/jsf/FacesHelper.java" line="7">

---

# Role of JSF components

The `FacesHelper` class is a JSF component that is used to interact with the server side. It has a method `isError` which checks if there are any messages to display. This is an example of how JSF components can communicate with the server side.

```java
@Component
public class FacesHelper {

	/**
	 * This method can be used in a Facelets View to render a box around <h:messages/> conditionally.
	 * Note that this is only necessary with vanilla JSF. With PrimeFaces you can use <p:messages/>
	 * or <p:growl>.
	 * 
	 * @return true if there are messages to display
	 */
	public boolean isError() {
		return FacesContext.getCurrentInstance().getMessages().hasNext();
	}
	
}
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/ajax/UserBean.java" line="1">

---

# Interaction with the server side

The `UserBean` class is another example of a JSF component. It has a method `createEmailSuggestion` which interacts with the server side to create an email suggestion based on the user's first and last name.

```java
package org.springframework.samples.webflow.ajax;

import java.io.Serializable;

import org.springframework.binding.message.MessageBuilder;
import org.springframework.util.StringUtils;
import org.springframework.webflow.execution.RequestContext;

public class UserBean implements Serializable {

	private static final long serialVersionUID = 1L;

	private String firstName;

	private String lastName;

	public String createEmailSuggestion(RequestContext context) {

		boolean haveFirst = StringUtils.hasText(firstName);
		boolean haveLast = StringUtils.hasLength(lastName);

```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/DispatcherServletInitializer.java" line="33">

---

# Data flow between JSF components and the server

The `onStartup` method in the `DispatcherServletInitializer` class sets up the JSF environment. It sets various parameters for the JSF context, such as the default suffix for JSF view templates and the refresh period for Facelets. This is an example of how data flows from the server side to the JSF components.

```java
	@Override
	public void onStartup(ServletContext servletContext) throws ServletException {

		// Use JSF view templates saved as *.xhtml, for use with Facelets
		servletContext.setInitParameter("jakarta.faces.DEFAULT_SUFFIX", ".xhtml");
		// Enable special Facelets debug output during development
		servletContext.setInitParameter("jakarta.faces.PROJECT_STAGE", "Development");
		// Causes Facelets to refresh templates during development
		servletContext.setInitParameter("jakarta.faces.FACELETS_REFRESH_PERIOD", "1");
		// Declare Spring Security Facelets tag library
		servletContext.setInitParameter("jakarta.faces.FACELETS_LIBRARIES", "/WEB-INF/springsecurity.taglib.xml");

		// Comment out if not using Mojarra
		servletContext.addListener(com.sun.faces.config.ConfigureListener.class);

		// Let the DispatcherServlet be registered
		super.onStartup(servletContext);
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
