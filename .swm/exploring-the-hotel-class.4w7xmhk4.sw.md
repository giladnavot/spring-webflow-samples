---
title: Exploring the Hotel Class
---
Hotel is a class in the repository that represents a hotel where users may book stays. It is a Serializable entity with properties such as id, name, address, city, state, zip, country, and price. The class also includes getter and setter methods for these properties. The Hotel class also has a method to create a booking for a user. The Hotel class is used in various parts of the application such as in the Booking class, HotelLazyDataModel class, JpaBookingService class, and in the database queries.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Hotel.java" line="15">

---

# Hotel Class Structure

The 'Hotel' class is a simple Java class marked with the '@Entity' annotation, indicating that it is a JPA entity. It has fields to store the hotel's id, name, address, city, state, zip, country, and price. Each field has corresponding getter and setter methods. The 'createBooking' method creates a new 'Booking' instance for a given user.

```java
public class Hotel implements Serializable {

	private static final long serialVersionUID = 4011346719502656269L;

	private Long id;

	private String name;

	private String address;

	private String city;

	private String state;

	private String zip;

	private String country;

	private BigDecimal price;

	@Id
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="39">

---

# Hotel Class Usage

The 'Hotel' class is used in the 'Booking' class. A 'Booking' has a reference to a 'Hotel', indicating that a booking is associated with a specific hotel. The 'Hotel' object is passed to the 'Booking' constructor when creating a new booking.

```java
	private Hotel hotel;

	private Date checkinDate;

	private Date checkoutDate;

	private String creditCard;

	private String creditCardName;

	private int creditCardExpiryMonth;

	private int creditCardExpiryYear;

	private boolean smoking;

	private int beds;

	private Amenity[] amenities;

	public Booking() {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
