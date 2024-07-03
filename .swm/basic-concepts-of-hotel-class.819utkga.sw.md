---
title: Basic Concepts of Hotel Class
---
In the spring-webflow-samples repository, 'Hotel' refers to a class that represents a hotel entity in the booking system. It is a part of the domain model in the booking application. The Hotel class contains properties such as id, name, address, city, state, zip, country, and price. These properties represent the details of a hotel where users may book stays. The Hotel class also includes methods to get and set these properties, create a booking for a user, and override the toString method for a string representation of the Hotel object.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Hotel.java" line="14">

---

# Hotel Class Definition

This is the definition of the 'Hotel' class. It includes private fields for storing hotel details, getter and setter methods for accessing and modifying these details, a method for creating a booking, and a toString method for representing the hotel as a string.

```java
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

	@Id
	@GeneratedValue
	public Long getId() {
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="66">

---

# Hotel Usage in Booking Creation

The 'Hotel' class is used here in the 'Booking' class to create a new booking. The 'createBooking' method in the 'Hotel' class is called with a 'User' instance as an argument, creating a new 'Booking' instance associated with the 'Hotel' and 'User'.

```java
	public Booking(Hotel hotel, User user) {
		this();
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="41">

---

# Hotel Usage in Hotel Search

The 'Hotel' class is used here in the 'JpaBookingService' class to find hotels based on search criteria and to create a booking for a specific hotel. The 'findHotels' method returns a list of 'Hotel' instances that match the search criteria, and the 'createBooking' method uses the 'findHotelById' method to retrieve a 'Hotel' instance and create a booking for it.

```java
	@SuppressWarnings("unchecked")
	public List<Hotel> findHotels(SearchCriteria criteria) {
		String pattern = getSearchPattern(criteria);
		int startIndex = criteria.getPage() * criteria.getPageSize();
		return em
				.createQuery(
						"select h from Hotel h where lower(h.name) like :pattern or lower(h.city) like :pattern "
								+ " or lower(h.zip) like :pattern or lower(h.address) like :pattern")
				.setParameter("pattern", pattern).setFirstResult(startIndex).setMaxResults(criteria.getPageSize())
				.getResultList();
	}

	@Transactional(readOnly = true)
	public Hotel findHotelById(Long id) {
		return em.find(Hotel.class, id);
	}

	@Transactional(readOnly = true)
	public Booking createBooking(Long hotelId, String username) {
		Hotel hotel = em.find(Hotel.class, hotelId);
		User user = findUser(username);
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
