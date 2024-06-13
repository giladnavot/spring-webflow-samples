---
title: Booking Flow Process
---
This document will cover the process of starting a booking flow in the Spring Web Flow project. The process includes:

1. Initiating the booking flow
2. Creating a test booking
3. Setting the ID for the booking.

```mermaid
graph TD;
subgraph booking-faces/src
  testStartBookingFlow:::mainFlowStyle --> createTestBooking
end
subgraph booking-faces/src
  createTestBooking:::mainFlowStyle --> setId
end
  setId:::mainFlowStyle --> ...

classDef mainFlowStyle color:#000000,fill:#7CB9F4
classDef rootsStyle color:#000000,fill:#00FFF4
classDef Style1 color:#000000,fill:#00FFAA
classDef Style2 color:#000000,fill:#FFFF00
classDef Style3 color:#000000,fill:#AA7CB9
```

<SwmSnippet path="/booking-faces/src/test/java/org/springframework/webflow/samples/booking/BookingFlowExecutionTests.java" line="1" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=">

---

# Initiating the Booking Flow

The function `testStartBookingFlow` initiates the booking flow. It's the entry point for the process.

```java
package org.springframework.webflow.samples.booking;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/test/java/org/springframework/webflow/samples/booking/BookingFlowExecutionTests.java" line="74" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=">

---

# Creating a Test Booking

The function `createTestBooking` is called by `testStartBookingFlow`. It creates a new booking instance with a hotel and a user. The hotel ID is set to 1 and the user is predefined.

```java
    private Booking createTestBooking() {
	Hotel hotel = new Hotel();
	hotel.setId(1L);
	hotel.setName("Jameson Inn");
	User user = new User("keith", "pass", "Keith Donald");
	Booking booking = new Booking(hotel, user);
	return booking;
    }
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="92" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=">

---

# Setting the ID for the Booking

The function `setId` is called by `createTestBooking`. It sets the ID for the booking instance.

```java
	public void setId(Long id) {
		this.id = id;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://app.swimm.io/)</sup></SwmMeta>
