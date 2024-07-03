---
title: Exploring the Booking Entity
---
Booking refers to a hotel reservation made by a user. It is represented as an entity in the codebase, with various attributes such as the user making the booking, the hotel being booked, check-in and check-out dates, credit card information, and preferences like smoking and number of beds. The Booking class also includes methods to calculate the total cost and the number of nights for the booking.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="30">

---

# Booking Class Structure

The 'Booking' class includes fields for all the necessary details of a booking. It also includes a set of amenities, which could be additional services or features that the user has opted for during their stay.

```java
public class Booking implements Serializable {

	private Long id;

	private User user;

	private Hotel hotel;

	@DateTimeFormat(pattern = "MM-dd-yyyy")
	private Date checkinDate;

	@DateTimeFormat(pattern = "MM-dd-yyyy")
	private Date checkoutDate;

	private String creditCard;

	private String creditCardName;

	private int creditCardExpiryMonth;

	private int creditCardExpiryYear;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="58">

---

# Booking Class Constructors

The 'Booking' class provides two constructors. The default constructor initializes the check-in and check-out dates to the next two days. The second constructor allows a 'Hotel' and 'User' object to be passed in, setting the hotel and user for the booking.

```java
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

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="72">

---

# Calculating Total Cost and Nights

The 'Booking' class provides methods to calculate the total cost of the booking and the number of nights for the stay. The total cost is calculated by multiplying the price of the hotel by the number of nights. The number of nights is calculated by subtracting the check-in date from the check-out date.

```java
	@Transient
	public BigDecimal getTotal() {
		return hotel.getPrice().multiply(new BigDecimal(getNights()));
	}

	@Transient
	public int getNights() {
		if (checkinDate == null || checkoutDate == null) {
			return 0;
		} else {
			return (int) ((checkoutDate.getTime() - checkinDate.getTime()) / 1000 / 60 / 60 / 24);
		}
	}
```

---

</SwmSnippet>

# Booking Class Functions

The Booking class contains several methods that manage the details of a hotel booking.

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="72">

---

## getTotal

The `getTotal` method calculates the total cost of the booking. It multiplies the price of the hotel per night by the number of nights of the stay.

```java
	@Transient
	public BigDecimal getTotal() {
		return hotel.getPrice().multiply(new BigDecimal(getNights()));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="77">

---

## getNights

The `getNights` method calculates the number of nights of the stay. It subtracts the check-in date from the check-out date.

```java
	@Transient
	public int getNights() {
		if (checkinDate == null || checkoutDate == null) {
			return 0;
		} else {
			return (int) ((checkoutDate.getTime() - checkinDate.getTime()) / 1000 / 60 / 60 / 24);
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="147">

---

## getDescription

The `getDescription` method provides a description of the booking. It includes the name of the hotel and the dates of the stay.

```java
	@Transient
	public String getDescription() {
		DateFormat df = DateFormat.getDateInstance(DateFormat.MEDIUM);
		return hotel == null ? null : hotel.getName() + ", " + df.format(getCheckinDate()) + " to "
				+ df.format(getCheckoutDate());
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
