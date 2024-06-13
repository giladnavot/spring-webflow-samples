---
title: Understanding Entities in the Booking MVC Module
---
Entities in the booking-mvc module of the spring-webflow-samples project refer to the data objects that are persisted in the database. They are annotated with the @Entity annotation, which marks the class as a JPA entity. Examples of entities in this project include the User, Hotel, and Booking classes. The User entity represents a user who can book hotels, the Hotel entity represents a hotel where users may book stays, and the Booking entity represents a hotel booking made by a user. These entities are used throughout the application, for example, in the JpaBookingService class for creating bookings, and in the SecurityConfig class for setting up in-memory user details for authentication.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/User.java" line="10">

---

# User Entity

The User entity represents a user of the application. It has properties for username, password, and name. It is annotated with @Entity, indicating that it is a JPA entity and should be mapped to a database table.

```java
 * A user who can book hotels.
 */
@Entity
@Table(name = "Customer")
public class User implements Serializable {
	private String username;

	private String password;

	private String name;

	public User() {
	}

	public User(String username, String password, String name) {
		this.username = username;
		this.password = password;
		this.name = name;
	}

	@Id
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Hotel.java" line="11">

---

# Hotel Entity

The Hotel entity represents a hotel. It has properties for id, name, address, city, state, zip, country, and price. It is also annotated with @Entity.

```java
/**
 * A hotel where users may book stays.
 */
@Entity
public class Hotel implements Serializable {
	private Long id;

	private String name;

	private String address;

	private String city;

	private String state;

	private String zip;

	private String country;

	private BigDecimal price;

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="25">

---

# Booking Entity

The Booking entity represents a booking made by a user for a hotel. It has properties for id, user, hotel, checkinDate, checkoutDate, creditCard, creditCardName, creditCardExpiryMonth, creditCardExpiryYear, smoking, beds, and amenities. It is also annotated with @Entity.

```java
/**
 * A Hotel Booking made by a User.
 */
@Entity
@BookingDateRange
public class Booking implements Serializable {

	private Long id;

	private User user;

	private Hotel hotel;

	@DateTimeFormat(pattern = "MM-dd-yyyy")
	private Date checkinDate;

	@DateTimeFormat(pattern = "MM-dd-yyyy")
	private Date checkoutDate;

	private String creditCard;

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/BookingService.java" line="1">

---

# Booking Service

The BookingService interface defines the operations that can be performed on bookings. It includes methods to find bookings, find hotels, create bookings, persist bookings, and cancel bookings.

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

# JPA Booking Service

The JpaBookingService class is a JPA-based implementation of the BookingService interface. It uses an EntityManager to perform the operations on the entities.

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

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
