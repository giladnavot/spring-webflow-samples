---
title: Exploring the Booking Class
---
Booking in this repository refers to a hotel reservation made by a user. It is represented as a class in the codebase, with properties such as the user who made the booking, the hotel that was booked, check-in and check-out dates, and payment details. The Booking class also includes methods for calculating the total cost of the booking and the number of nights, as well as validation for the booking details.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="31">

---

# Booking Class Structure

The Booking class includes fields for each piece of information about a booking. This includes basic information like the user who made the booking and the hotel that was booked, as well as details about the booking like the check-in and check-out dates, the number of beds, and whether the user is a smoker.

```java
public class Booking implements Serializable {

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
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="62">

---

# Creating a Booking

The Booking class provides a constructor that takes a Hotel and a User object. This constructor is used to create a new booking. It sets the check-in date to the current date and the check-out date to the next day.

```java
	public Booking(Hotel hotel, User user) {
		this.hotel = hotel;
		this.user = user;
		Calendar calendar = Calendar.getInstance();
		calendar.add(Calendar.DAY_OF_MONTH, 1);
		setCheckinDate(calendar.getTime());
		calendar.add(Calendar.DAY_OF_MONTH, 1);
		setCheckoutDate(calendar.getTime());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="72">

---

# Calculating the Total Cost and Number of Nights

The Booking class includes methods to calculate the total cost of the booking and the number of nights for the stay. The total cost is calculated by multiplying the price of the hotel by the number of nights. The number of nights is calculated by subtracting the check-in date from the check-out date.

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
			return (int) (checkoutDate.getTime() - checkinDate.getTime()) / 1000 / 60 / 60 / 24;
		}
	}
```

---

</SwmSnippet>

# Booking Class Functions

Let's delve into the key functions of the Booking class.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="72">

---

## getTotal Function

The `getTotal` function calculates the total cost of the booking. It multiplies the hotel's price by the number of nights.

```java
	@Transient
	public BigDecimal getTotal() {
		return hotel.getPrice().multiply(new BigDecimal(getNights()));
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="77">

---

## getNights Function

The `getNights` function calculates the number of nights for the booking. It subtracts the check-in date from the check-out date.

```java
	@Transient
	public int getNights() {
		if (checkinDate == null || checkoutDate == null) {
			return 0;
		} else {
			return (int) (checkoutDate.getTime() - checkinDate.getTime()) / 1000 / 60 / 60 / 24;
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="204">

---

## validateEnterBookingDetails Function

The `validateEnterBookingDetails` function validates the booking details. It checks if the check-in date is before the current date and if the check-out date is before the check-in date, and adds error messages if these conditions are not met.

```java
	public void validateEnterBookingDetails(ValidationContext context) {
		MessageContext messages = context.getMessageContext();
		if (checkinDate.before(today())) {
			messages.addMessage(new MessageBuilder().error().source("checkinDate")
					.code("booking.checkinDate.beforeToday").build());
		} else if (checkoutDate.before(checkinDate)) {
			messages.addMessage(new MessageBuilder().error().source("checkoutDate")
					.code("booking.checkoutDate.beforeCheckinDate").build());
		}
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
