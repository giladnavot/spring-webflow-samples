---
title: Basic Concepts of Booking MVC
---
Booking MVC is a module in the Spring Web Flow samples repository. It is designed to demonstrate a typical booking system using the Model-View-Controller (MVC) pattern. The module includes classes for handling bookings, such as the `Booking` class, which represents a booking made by a user for a hotel, and the `BookingService` interface, which defines the operations that can be performed on bookings. The `HotelsController` class uses the `BookingService` to manage bookings, including creating, retrieving, and deleting bookings. The module also includes configuration and styling files.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="56">

---

# Model in Booking MVC

The `Booking` class represents the model in the MVC pattern. It encapsulates the data and the business logic for booking a hotel. For example, it has fields for `hotel` and `user`, and methods to manipulate these fields.

```java
	private Set<Amenity> amenities;

	public Booking() {
		Calendar calendar = Calendar.getInstance();
		calendar.add(Calendar.DAY_OF_MONTH, 1);
		setCheckinDate(calendar.getTime());
		calendar.add(Calendar.DAY_OF_MONTH, 1);
		setCheckoutDate(calendar.getTime());
	}

	public Booking(Hotel hotel, User user) {
		this();
		this.hotel = hotel;
		this.user = user;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="76">

---

# Controller in Booking MVC

The `BookingFlowHandler()` method in the `WebMvcConfig` class represents the controller in the MVC pattern. It handles the flow of the booking process, coordinating the model and the view.

```java
	@Bean(name="hotels/booking")
	public BookingFlowHandler BookingFlowHandler() {
		return new BookingFlowHandler();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/reviewBooking.html" line="1">

---

# View in Booking MVC

The `reviewBooking.html` file represents the view in the MVC pattern. It presents the model data to the user and accepts user input.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 
      xmlns:th="http://www.thymeleaf.org"
      lang="en">

<head th:replace="layouts/standard.html :: //head">

    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
    <!-- This <head> section is only used for static prototyping purposes.             -->
    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
```

---

</SwmSnippet>

# Booking MVC Endpoints

Booking MVC Endpoints

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="55">

---

## Root Endpoint (/)

The root endpoint (/) is mapped to the 'intro' view. This is typically the landing page of the application.

```java
		registry.addViewController("/").setViewName("intro");
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="56">

---

## Login Endpoint (/login)

The /login endpoint is used for user authentication. It is mapped to the 'login' view.

```java
		registry.addViewController("/login");
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/config/WebMvcConfig.java" line="57">

---

## Logout Success Endpoint (/logoutSuccess)

The /logoutSuccess endpoint is displayed to the user after they have successfully logged out. It is mapped to the 'logoutSuccess' view.

```java
		registry.addViewController("/logoutSuccess");
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
