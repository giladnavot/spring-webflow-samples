---
title: Interactions between Layout Files and the JSF Lifecycle
---
This document will cover the interaction of layout files with the JSF lifecycle in the context of the Spring Web Flow samples repository. The main points of discussion are:

1. The role of layout files in JSF applications
2. The configuration of JSF in the Spring Web Flow samples
3. The interaction of layout files with the JSF lifecycle.

# Role of Layout Files in JSF Applications

In JSF applications, layout files, typically XHTML files, define the structure of the user interface. They contain JSF tags that are processed during the JSF lifecycle. The layout files in the Spring Web Flow samples are located in the `WEB-INF/layouts` directory of each project.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/DispatcherServletInitializer.java" line="33">

---

# Configuration of JSF in Spring Web Flow Samples

The `onStartup` method configures the JSF environment. It sets various initialization parameters for JSF and Facelets. For example, it sets the default suffix for JSF view templates to `.xhtml`, enabling the use of Facelets. It also sets the Facelets refresh period to 1, causing Facelets to refresh templates during development.

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

# Interaction of Layout Files with the JSF Lifecycle

During the JSF lifecycle, the JSF implementation processes the tags in the layout files. This includes converting component data, validating user input, and updating the model. The layout files in the Spring Web Flow samples, such as `standard.xhtml`, are processed in this way.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
