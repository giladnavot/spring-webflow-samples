---
title: Role of JSF and Spring MVC in booking process
---
This document will cover the role of JSF and Spring MVC in the booking process within the spring-webflow-samples repository. We'll cover:

1. The BookingService interface and its implementations
2. The role of the HotelsController in Spring MVC
3. The configuration of JSF in the booking process

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/BookingService.java" line="1">

---

# The BookingService Interface

The BookingService interface defines the contract for a service that manages hotel bookings. It includes methods for finding bookings, finding hotels, creating bookings, persisting bookings, and cancelling bookings.

```java
package org.springframework.webflow.samples.booking;

import java.util.List;

/**
 * A service interface for retrieving hotels and bookings from a backing repository. Also supports the ability to cancel
 * a booking.
 */
public interface BookingService {

    /**
     * Find bookings made by the given user
     * @param username the user's name
     * @return their bookings
     */
    List<Booking> findBookings(String username);

    /**
     * Find hotels available for booking by some criteria.
     * @param criteria the search criteria
     * @return a list of hotels meeting the criteria
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="1">

---

# Implementations of the BookingService Interface

The JpaBookingService class is a JPA-based implementation of the BookingService interface. It uses the EntityManager to interact with the database. The EntityManager reference is provided by the Spring container.

```java
package org.springframework.webflow.samples.booking;

import java.util.List;

import jakarta.persistence.EntityManager;
import jakarta.persistence.PersistenceContext;

import org.springframework.stereotype.Repository;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;
import org.springframework.util.StringUtils;

/**
 * A JPA-based implementation of the Booking Service. Delegates to a JPA entity manager to issue data access calls
 * against the backing repository. The EntityManager reference is provided by the managing container (Spring)
 * automatically.
 */
@Service("bookingService")
@Repository
public class JpaBookingService implements BookingService {

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/HotelsController.java" line="1">

---

# The Role of the HotelsController in Spring MVC

The HotelsController is a Spring MVC controller that handles HTTP requests related to hotels. It uses the BookingService to perform operations related to hotel bookings.

```java
package org.springframework.webflow.samples.booking;

import java.security.Principal;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;

@Controller
public class HotelsController {

	private BookingService bookingService;

	@Autowired
	public HotelsController(BookingService bookingService) {
		this.bookingService = bookingService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="1">

---

# Configuration of JSF in the Booking Process

The WebMvcConfig class configures the JSF FlowHandlerAdapter and the UrlBasedViewResolver for JSF views. This configuration is necessary for integrating JSF with Spring MVC in the booking process.

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

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="follow-up"><sup>Powered by [Swimm](/)</sup></SwmMeta>
