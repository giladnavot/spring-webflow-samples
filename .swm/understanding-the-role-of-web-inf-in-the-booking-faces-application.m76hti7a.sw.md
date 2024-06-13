---
title: Understanding the Role of WEB-INF in the Booking-Faces Application
---
The `WEB-INF` directory in the `booking-faces` application is a special directory that contains resources related to the application that aren't directly served to the client. It includes configuration files, libraries, and class files.

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/beans.xml" line="1">

---

`beans.xml` is a configuration file used by the CDI (Contexts and Dependency Injection) container to discover beans. In this case, it's set to discover all beans.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="https://jakarta.ee/xml/ns/jakartaee"
	   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	   xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee https://jakarta.ee/xml/ns/jakartaee/beans_3_0.xsd"
	   version="3.0"
	   bean-discovery-mode="all">

</beans>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/faces-config.xml" line="1">

---

`faces-config.xml` is a configuration file for JavaServer Faces (JSF) applications. It defines application-wide settings like the message bundle for localization.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<faces-config xmlns="http://java.sun.com/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee https://java.sun.com/xml/ns/javaee/web-facesconfig_2_0.xsd"
        version="2.0">

	<application>
		<message-bundle>JsfMessageResources</message-bundle>
	</application>
	    
</faces-config>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/intro.xhtml" line="1">

---

`intro.xhtml` is a JSF page that uses Facelets as its templating system. It's a standalone page that provides information about the application and links to start the main flow.

```html
<!DOCTYPE composition PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<ui:composition xmlns="http://www.w3.org/1999/xhtml"
	    		xmlns:ui="http://java.sun.com/jsf/facelets"
	  			xmlns:h="http://java.sun.com/jsf/html"
	  			xmlns:f="http://java.sun.com/jsf/core"
                xmlns:sf="http://www.springframework.org/tags/faces"
				template="layouts/standard.xhtml">

<ui:define name="notes">
	<p>
		This is a simple standalone JSF page. 
	</p>
	<p>
		Clicking the "Start" link below will launch the main to search for hotels (see <strong>main-flow.xml</strong>).
		The main flow in turn launches the booking sub-flow to book the hotel (see <strong>booking-flow.xml</strong>).
	</p>
	<p>
		The main flow is accessible without logging in while the booking flow requires authentication.
	</p>
</ui:define>

```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/faces-config.xml" line="1">

---

# Configuration Files

The faces-config.xml file is a configuration file for JSF applications. It defines application-wide settings.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<faces-config xmlns="http://java.sun.com/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee https://java.sun.com/xml/ns/javaee/web-facesconfig_2_0.xsd"
        version="2.0">

	<application>
		<message-bundle>JsfMessageResources</message-bundle>
	</application>
	    
</faces-config>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/beans.xml" line="1">

---

The beans.xml file is used for configuring beans in the application.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="https://jakarta.ee/xml/ns/jakartaee"
	   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	   xsi:schemaLocation="https://jakarta.ee/xml/ns/jakartaee https://jakarta.ee/xml/ns/jakartaee/beans_3_0.xsd"
	   version="3.0"
	   bean-discovery-mode="all">

</beans>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/flows/booking/booking-flow.xml" line="1">

---

# Flow Definitions

The booking-flow.xml file is an example of a flow definition file. It defines the steps involved in the booking process.

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
