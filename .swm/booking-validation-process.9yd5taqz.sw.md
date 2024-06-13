---
title: Booking Validation Process
---
This document will cover the process of validating booking details in the Spring Web Flow samples project. The process includes:

1. The function `validateEnterBookingDetails` and its role in the process.
2. The function `today` and how it contributes to the validation process.
3. The function `getTime` and its role in obtaining the current time.

```mermaid
graph TD;
  validateEnterBookingDetails:::mainFlowStyle --> today
  today:::mainFlowStyle --> getTime
  getTime:::mainFlowStyle --> ...

classDef mainFlowStyle color:#000000,fill:#7CB9F4
classDef rootsStyle color:#000000,fill:#00FFF4
classDef Style1 color:#000000,fill:#00FFAA
classDef Style2 color:#000000,fill:#FFFF00
classDef Style3 color:#000000,fill:#AA7CB9
```

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="1" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=">

---

# The function `validateEnterBookingDetails`

The function `validateEnterBookingDetails` is the starting point of the booking validation process. It's responsible for initiating the validation of the entered booking details.

```java
package org.springframework.webflow.samples.booking;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="215" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=">

---

# The function `today`

The function `today` is called within `validateEnterBookingDetails`. It retrieves the current date, subtracts one day from it, and returns the result. This is used in the context of booking validation to ensure that the booking date is not in the past.

```java
	private Date today() {
		Calendar calendar = Calendar.getInstance();
		calendar.add(Calendar.DAY_OF_MONTH, -1);
		return calendar.getTime();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/poller/CurrentTimeBean.java" line="10" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=">

---

# The function `getTime`

The function `getTime` is called within `today`. It simply returns the current date and time. This is used in the `today` function to get the current date before subtracting one day.

```java
	public Date getTime() {
		return new Date();
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://app.swimm.io/)</sup></SwmMeta>
