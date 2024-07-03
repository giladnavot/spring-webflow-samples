---
title: Overview of Booking Faces
---
Booking faces is a sub-project within the Spring Web Flow Samples repository. It is a web application that demonstrates the use of Spring Web Flow with JSF (JavaServer Faces). The application allows users to search for hotels and make bookings. The `Booking` class represents a hotel booking made by a user. It contains information such as the hotel, check-in and check-out dates, and the user who made the booking. The `BookingService` interface defines the operations that can be performed on bookings, such as finding bookings by username, creating a booking, persisting a booking to the database, and cancelling a booking. The `BookingService` is implemented by the `JpaBookingService` class, which uses the Java Persistence API (JPA) to interact with the database.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="33">

---

## Booking Class

The Booking class represents a booking made by a user. It contains fields such as `user`, `hotel`, and `amenities`. It also provides a default constructor and a constructor that takes a `Hotel` and `User` as parameters.

```java
	private static final long serialVersionUID = 1171567558348174963L;

	private Long id;

	private User user;

	private Hotel hotel;

	private Date checkinDate;

	private Date checkoutDate;

	private String creditCard;

	private String creditCardName;

	private int creditCardExpiryMonth;

	private int creditCardExpiryYear;

	private boolean smoking;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/BookingService.java" line="5">

---

## BookingService Interface

The BookingService interface defines the operations that can be performed on bookings. These include finding bookings by username, finding hotels by criteria, creating a booking, persisting a booking, and cancelling a booking.

```java
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
     * @param firstResult the index of the first result to return
     * @param sortBy the field to sort by
     * @param ascending true if the sorting should be in ascending order, false for descending
     * @return a list of hotels meeting the criteria
     */
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/index.html" line="1">

---

## Web Pages and Resources

The web pages and resources provide the user interface for the booking process. For example, the `index.html` file redirects the user to the `spring/intro` URL.

```html
<html>
<head>
  <meta http-equiv="Refresh" content="0; URL=spring/intro">
</head>
</html>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
