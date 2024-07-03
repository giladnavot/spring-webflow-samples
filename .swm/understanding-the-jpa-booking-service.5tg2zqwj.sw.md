---
title: Understanding the Jpa Booking Service
---
The JpaBookingService is a JPA-based implementation of the Booking Service. It uses the EntityManager to interact with the database, which is provided by the Spring container. The service is responsible for managing bookings, including finding bookings by username, finding hotels based on search criteria, creating bookings, persisting bookings, and cancelling bookings.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="18">

---

# JpaBookingService Class

This is the JpaBookingService class. It is annotated with @Service and @Repository, indicating that it is a service bean and a repository in the context of Spring. It implements the BookingService interface, meaning it provides concrete implementations for the methods defined in the interface.

```java
@Service("bookingService")
@Repository
public class JpaBookingService implements BookingService {

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
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="29">

---

# findBookings Method

The `findBookings` method is used to find bookings for a given username. It uses the EntityManager `em` to create and execute a JPA query.

```java
	@Transactional(readOnly = true)
	@SuppressWarnings("unchecked")
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

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="66">

---

# persistBooking Method

The `persistBooking` method is used to persist a booking object to the database. It uses the EntityManager `em` to persist the booking.

```java
	@Transactional
	public void persistBooking(Booking booking) {
		em.persist(booking);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="71">

---

# cancelBooking Method

The `cancelBooking` method is used to cancel a booking. It does this by finding the booking by its id and then removing it using the EntityManager `em`.

```java
	@Transactional
	public void cancelBooking(Long id) {
		Booking booking = em.find(Booking.class, id);
		if (booking != null) {
			em.remove(booking);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="40">

---

# findHotels Method

The `findHotels` method is used to find hotels based on a SearchCriteria object. It uses the EntityManager `em` to create and execute a JPA query.

```java
	@Transactional(readOnly = true)
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
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="58">

---

# createBooking Method

The `createBooking` method is used to create a new booking. It does this by finding a hotel and a user and then creating a new Booking object.

```java
	@Transactional(readOnly = true)
	public Booking createBooking(Long hotelId, String username) {
		Hotel hotel = em.find(Hotel.class, hotelId);
		User user = findUser(username);
		Booking booking = new Booking(hotel, user);
		return booking;
	}
```

---

</SwmSnippet>

# JpaBookingService Functions

The JpaBookingService class contains several key methods that facilitate the booking process.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="31">

---

## findBookings

The `findBookings` method is used to retrieve a list of bookings for a specific user. It takes a username as a parameter and returns a list of Booking objects associated with that user.

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

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="42">

---

## findHotels

The `findHotels` method is used to search for hotels based on a set of criteria. It takes a SearchCriteria object as a parameter and returns a list of Hotel objects that match the criteria.

```java
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
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="54">

---

## findHotelById

The `findHotelById` method retrieves a specific hotel by its ID. It takes a Long id as a parameter and returns the Hotel object with the matching id.

```java
	public Hotel findHotelById(Long id) {
		return em.find(Hotel.class, id);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="59">

---

## createBooking

The `createBooking` method creates a new booking. It takes a hotelId and a username as parameters, finds the corresponding Hotel and User objects, and returns a new Booking object with these details.

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

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="67">

---

## persistBooking

The `persistBooking` method saves a new booking to the database. It takes a Booking object as a parameter and persists it using the EntityManager.

```java
	public void persistBooking(Booking booking) {
		em.persist(booking);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="72">

---

## cancelBooking

The `cancelBooking` method removes a booking from the database. It takes a booking id as a parameter, finds the corresponding Booking object, and removes it using the EntityManager.

```java
	public void cancelBooking(Long id) {
		Booking booking = em.find(Booking.class, id);
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
