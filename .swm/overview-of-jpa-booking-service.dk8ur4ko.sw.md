---
title: Overview of Jpa Booking Service
---
The JpaBookingService is a JPA-based implementation of the Booking Service. It uses the EntityManager to interact with the database. The service is responsible for handling operations related to bookings, such as finding bookings by username, finding hotels based on search criteria, getting the number of hotels matching a criteria, finding a hotel by its ID, creating a booking, persisting a booking, and cancelling a booking. The service is marked as a Spring Service and Repository, indicating that it's a candidate for Spring's component scanning to detect and automatically configure beans.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="19">

---

# JpaBookingService Class

This is the JpaBookingService class. It is annotated with `@Service` and `@Repository`, indicating that it is a Spring-managed bean that interacts with the database. It implements the BookingService interface and is Serializable.

```java
@Service("bookingService")
@Repository
public class JpaBookingService implements BookingService, Serializable {

	private static final long serialVersionUID = 1L;

	private EntityManager em;

	@PersistenceContext
	public void setEntityManager(EntityManager em) {
		this.em = em;
	}

	@Transactional(readOnly = true)
	@SuppressWarnings("unchecked")
	public List<Booking> findBookings(String username) {
		if (username != null) {
			return em.createQuery("select b from Booking b where b.user.username = :username order by b.checkinDate")
					.setParameter("username", username).getResultList();
		} else {
			return null;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="25">

---

# EntityManager

The EntityManager `em` is used to interact with the database. It is injected by the Spring container using the `@PersistenceContext` annotation.

```java
	private EntityManager em;

	@PersistenceContext
	public void setEntityManager(EntityManager em) {
		this.em = em;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="34">

---

# Booking Methods

These are the methods related to bookings. `findBookings` retrieves bookings for a specific user. `createBooking` creates a new booking. `persistBooking` saves a booking to the database. `cancelBooking` removes a booking from the database.

```java
	public List<Booking> findBookings(String username) {
		if (username != null) {
			return em.createQuery("select b from Booking b where b.user.username = :username order by b.checkinDate")
					.setParameter("username", username).getResultList();
		} else {
			return null;
		}
	}

	@Transactional(readOnly = true)
	@SuppressWarnings("unchecked")
	public List<Hotel> findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {
		String pattern = getSearchPattern(criteria);
		orderBy = (orderBy != null) ? orderBy : "name";
		String orderDirection = (ascending) ? " ASC" : " DESC";
		return em
				.createQuery(
						"select h from Hotel h where lower(h.name) like :pattern or lower(h.city) like :pattern "
								+ "or lower(h.zip) like :pattern or lower(h.address) like :pattern order by h."
								+ orderBy + orderDirection).setParameter("pattern", pattern)
								.setMaxResults(criteria.getPageSize()).setFirstResult(firstResult).getResultList();
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="96">

---

# Helper Methods

`getSearchPattern` and `findUser` are helper methods used within the class. `getSearchPattern` prepares a search string for use in a query. `findUser` retrieves a User entity based on a username.

```java
	private String getSearchPattern(SearchCriteria criteria) {
		if (StringUtils.hasText(criteria.getSearchString())) {
			return "%" + criteria.getSearchString().toLowerCase().replace('*', '%') + "%";
		} else {
			return "%";
		}
	}

	private User findUser(String username) {
		return (User) em.createQuery("select u from User u where u.username = :username")
				.setParameter("username", username).getSingleResult();
	}
```

---

</SwmSnippet>

# JpaBookingService Functions

This section covers the main functions of the JpaBookingService class.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="34">

---

## findBookings

The `findBookings` function is used to find bookings by a given username. It queries the database for bookings where the username matches the provided username.

```java
	public List<Booking> findBookings(String username) {
		if (username != null) {
			return em.createQuery("select b from Booking b where b.user.username = :username order by b.checkinDate")
					.setParameter("username", username).getResultList();
		} else {
			return null;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="45">

---

## findHotels

The `findHotels` function is used to find hotels based on the provided search criteria. It queries the database for hotels where the name, city, zip, or address matches the search pattern.

```java
	public List<Hotel> findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {
		String pattern = getSearchPattern(criteria);
		orderBy = (orderBy != null) ? orderBy : "name";
		String orderDirection = (ascending) ? " ASC" : " DESC";
		return em
				.createQuery(
						"select h from Hotel h where lower(h.name) like :pattern or lower(h.city) like :pattern "
								+ "or lower(h.zip) like :pattern or lower(h.address) like :pattern order by h."
								+ orderBy + orderDirection).setParameter("pattern", pattern)
								.setMaxResults(criteria.getPageSize()).setFirstResult(firstResult).getResultList();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="58">

---

## getNumberOfHotels

The `getNumberOfHotels` function is used to get the number of hotels that match the provided search criteria. It queries the database for the count of hotels where the name, city, zip, or address matches the search pattern.

```java
	public int getNumberOfHotels(SearchCriteria criteria) {
		String pattern = getSearchPattern(criteria);
		Long count = (Long) em
				.createQuery(
						"select count(h.id) from Hotel h where lower(h.name) like :pattern or lower(h.city) like :pattern "
								+ "or lower(h.zip) like :pattern or lower(h.address) like :pattern")
								.setParameter("pattern", pattern).getSingleResult();
		return count.intValue();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="69">

---

## findHotelById

The `findHotelById` function is used to find a hotel by its ID. It queries the database for a hotel where the ID matches the provided ID.

```java
	public Hotel findHotelById(Long id) {
		return em.find(Hotel.class, id);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="74">

---

## createBooking

The `createBooking` function is used to create a new booking. It finds the hotel and user by their IDs and creates a new Booking object.

```java
	public Booking createBooking(Long hotelId, String username) {
		Hotel hotel = em.find(Hotel.class, hotelId);
		User user = findUser(username);
		Booking booking = new Booking(hotel, user);
		return booking;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="82">

---

## persistBooking

The `persistBooking` function is used to persist a booking to the database. It uses the EntityManager to persist the booking.

```java
	public void persistBooking(Booking booking) {
		em.persist(booking);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="87">

---

## cancelBooking

The `cancelBooking` function is used to cancel a booking. It finds the booking by its ID and removes it from the database.

```java
	public void cancelBooking(Booking booking) {
		booking = em.find(Booking.class, booking.getId());
		if (booking != null) {
			em.remove(booking);
		}
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
