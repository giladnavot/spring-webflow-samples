---
title: Introduction to Flows
---
Flows in the Spring Web Flow framework, such as those found in the `booking-faces/src/main/webapp/WEB-INF/flows` directory, are a key concept that define a series of steps leading to a business goal. They encapsulate sequences of user interactions, preserving session state across requests. Each flow is defined in an XML file, like `main-flow.xml` or `booking-flow.xml`, and consists of states and transitions. For instance, the `bookHotel` subflow state in `main-flow.xml` represents a part of the user journey where a hotel booking is made.

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/flows/booking/booking-flow.xml" line="16">

---

# Booking Flow

The `enterBookingDetails` state is the starting point of the booking flow. From here, the user can either proceed to the `reviewBooking` state or cancel the booking, which leads to the `bookingCancelled` state.

```xml
	<view-state id="enterBookingDetails" model="booking">
		<transition on="proceed" to="reviewBooking" />
		<transition on="cancel" to="bookingCancelled" bind="false" />
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/flows/booking/booking-flow.xml" line="21">

---

In the `reviewBooking` state, the user can confirm the booking. On confirmation, the booking is persisted and the flow transitions to the `bookingConfirmed` state.

```xml
	<view-state id="reviewBooking">
		<transition on="confirm" to="bookingConfirmed">
			<evaluate expression="bookingService.persistBooking(booking)" />
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/flows/booking/booking-flow.xml" line="29">

---

The `bookingConfirmed` and `bookingCancelled` states are end states, signifying the completion of the flow.

```xml
	<end-state id="bookingConfirmed" />

	<end-state id="bookingCancelled" />
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/flows/main/main-flow.xml" line="37">

---

# Main Flow

The `bookHotel` state in the main flow is a subflow state, which calls the booking flow. The input to the booking flow is the hotel id, and on completion, the main flow transitions to the `finish` state.

```xml
	<subflow-state id="bookHotel" subflow="booking">
		<input name="hotelId" value="hotel.id" />
		<transition on="bookingConfirmed" to="finish" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
