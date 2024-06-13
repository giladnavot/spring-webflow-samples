---
title: Exploring Entities in the Booking-Faces Module
---
Entities in the spring-webflow-samples repository, specifically in the booking-faces module, are classes that represent the main objects or concepts in the application. They are typically annotated with @Entity, indicating that they are JPA entities and will be mapped to a database table. For instance, the User class represents a user who can book hotels, and the Hotel class represents a hotel where users may book stays. These entities are used throughout the application, in service classes, controllers, and views.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/User.java" line="1">

---

# User Entity

The User entity represents a user of the application. It has fields for username, password, and name. It is annotated with @Entity, indicating that it is a JPA entity and should be mapped to a database table.

```java
package org.springframework.webflow.samples.booking;

import java.io.Serializable;

import jakarta.persistence.Entity;
import jakarta.persistence.Id;
import jakarta.persistence.Table;

/**
 * A user who can book hotels.
 */
@Entity
@Table(name = "Customer")
public class User implements Serializable {

	private static final long serialVersionUID = -3652559447682574722L;

	private String username;

	private String password;

```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Hotel.java" line="1">

---

# Hotel Entity

The Hotel entity represents a hotel in the application. It has fields for id, name, address, city, state, zip, country, and price. It is also annotated with @Entity.

```java
package org.springframework.webflow.samples.booking;

import java.io.Serializable;
import java.math.BigDecimal;

import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.Id;

/**
 * A hotel where users may book stays.
 */
@Entity
public class Hotel implements Serializable {

	private static final long serialVersionUID = 4011346719502656269L;

	private Long id;

	private String name;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" line="1">

---

# Booking Entity

The Booking entity represents a booking made by a user for a hotel. It has fields for id, user, hotel, checkinDate, checkoutDate, creditCard, creditCardName, creditCardExpiryMonth, creditCardExpiryYear, smoking, beds, and amenities. It is also annotated with @Entity.

```java
package org.springframework.webflow.samples.booking;

import java.io.Serializable;
import java.math.BigDecimal;
import java.text.DateFormat;
import java.util.Calendar;
import java.util.Date;

import jakarta.persistence.Basic;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.ManyToOne;
import jakarta.persistence.Temporal;
import jakarta.persistence.TemporalType;
import jakarta.persistence.Transient;
import jakarta.validation.constraints.Future;
import jakarta.validation.constraints.NotNull;
import jakarta.validation.constraints.Pattern;

```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
