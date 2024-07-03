---
title: spring-webflow-samples overview
---
The <SwmToken path="/pom.xml" pos="6:4:8" line-data="	&lt;artifactId&gt;spring-webflow-samples&lt;/artifactId&gt;">`spring-webflow-samples`</SwmToken> repository is an official collection of sample projects for the Spring Web Flow project. It provides various examples that demonstrate different aspects of the Spring Web Flow. These samples can be run on a server or built into a war file for further use. The repository contains different directories, each representing a different sample project. For instance, there are directories for <SwmToken path="/pom.xml" pos="16:4:6" line-data="		&lt;module&gt;webflow-showcase&lt;/module&gt;">`webflow-showcase`</SwmToken>, <SwmToken path="/pom.xml" pos="14:4:6" line-data="		&lt;module&gt;primefaces-showcase&lt;/module&gt;">`primefaces-showcase`</SwmToken>, <SwmToken path="/pom.xml" pos="13:4:6" line-data="		&lt;module&gt;booking-faces&lt;/module&gt;">`booking-faces`</SwmToken>, and <SwmToken path="/pom.xml" pos="12:4:6" line-data="		&lt;module&gt;booking-mvc&lt;/module&gt;">`booking-mvc`</SwmToken>, each containing code related to different aspects of Spring Web Flow.

## Modules

### Booking faces

Booking faces is a module that provides a sample implementation of a booking system using Spring Web Flow. It includes classes and interfaces that define the structure and behavior of bookings, such as the <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" pos="31:4:4" line-data="public class Booking implements Serializable {">`Booking`</SwmToken> class and the <SwmToken path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/BookingService.java" pos="9:4:4" line-data="public interface BookingService {">`BookingService`</SwmToken> interface. The <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/Booking.java" pos="31:4:4" line-data="public class Booking implements Serializable {">`Booking`</SwmToken> class represents a booking made by a user for a hotel, and includes methods for getting and setting booking details. The <SwmToken path="/booking-mvc/src/main/java/org/springframework/webflow/samples/booking/BookingService.java" pos="9:4:4" line-data="public interface BookingService {">`BookingService`</SwmToken> interface defines the operations that can be performed on bookings, such as finding bookings by username, finding hotels by criteria, creating bookings, persisting bookings, and cancelling bookings. The module also includes CSS styles for the booking system's web interface.

- <SwmLink doc-title="Overview of Booking Faces">[Overview of Booking Faces](/.swm/overview-of-booking-faces.4gvj1fgi.sw.md)</SwmLink>
- <SwmLink doc-title="Maven Configuration in booking-faces">[Maven Configuration in booking-faces](/.swm/maven-configuration-in-booking-faces.su2hqfpo.sw.md)</SwmLink>
- <SwmLink doc-title="BookingService Interface Overview">[BookingService Interface Overview](/.swm/bookingservice-interface-overview.nubs1.sw.md)</SwmLink>
- <SwmLink doc-title="User Interaction Flow in Booking-Faces">[User Interaction Flow in Booking-Faces](/.swm/user-interaction-flow-in-booking-faces.gupz31se.sw.md)</SwmLink>
- <SwmLink doc-title="Role of JSF and Spring MVC in booking process">[Role of JSF and Spring MVC in booking process](/.swm/role-of-jsf-and-spring-mvc-in-booking-process.sd8bqjxf.sw.md)</SwmLink>
- <SwmLink doc-title="Error Handling in Booking-Faces">[Error Handling in Booking-Faces](/.swm/error-handling-in-booking-faces.ika3f4j8.sw.md)</SwmLink>
- <SwmLink doc-title="Overview of Jpa Booking Service">[Overview of Jpa Booking Service](/.swm/overview-of-jpa-booking-service.dk8ur4ko.sw.md)</SwmLink>
- <SwmLink doc-title="Understanding the Hotel Lazy Data Model">[Understanding the Hotel Lazy Data Model](/.swm/understanding-the-hotel-lazy-data-model.mmvv20pa.sw.md)</SwmLink>
- <SwmLink doc-title="Exploring the Hotel Class">[Exploring the Hotel Class](/.swm/exploring-the-hotel-class.4w7xmhk4.sw.md)</SwmLink>
- <SwmLink doc-title="Exploring the Booking Class">[Exploring the Booking Class](/.swm/exploring-the-booking-class.664zfrz5.sw.md)</SwmLink>
- <SwmLink doc-title="Getting Started with Configurations">[Getting Started with Configurations](/.swm/getting-started-with-configurations.5izas3o2.sw.md)</SwmLink>
- <SwmLink doc-title="Booking Flow Process">[Booking Flow Process](/.swm/booking-flow-process.ufa0pqqh.sw.md)</SwmLink>
- <SwmLink doc-title="Booking Validation Process">[Booking Validation Process](/.swm/booking-validation-process.9yd5taqz.sw.md)</SwmLink>
- <SwmLink doc-title="Hotel Data Loading Process">[Hotel Data Loading Process](/.swm/hotel-data-loading-process.vu9gv43v.sw.md)</SwmLink>

### Booking mvc

The 'Booking mvc' module is a part of the Spring Web Flow samples that demonstrates a booking system. It includes classes and methods for creating, persisting, and cancelling bookings. The module also includes a user interface for managing bookings.

- <SwmLink doc-title="Basic Concepts of Booking MVC">[Basic Concepts of Booking MVC](/.swm/basic-concepts-of-booking-mvc.rpni0zeg.sw.md)</SwmLink>
- <SwmLink doc-title="Maven Usage in booking-mvc">[Maven Usage in booking-mvc](/.swm/maven-usage-in-booking-mvc.5cmare2j.sw.md)</SwmLink>
- <SwmLink doc-title="BookingService Interface Overview">[BookingService Interface Overview](/.swm/bookingservice-interface-overview.qrb3a.sw.md)</SwmLink>
- <SwmLink doc-title="Understanding the Jpa Booking Service">[Understanding the Jpa Booking Service](/.swm/understanding-the-jpa-booking-service.5tg2zqwj.sw.md)</SwmLink>
- <SwmLink doc-title="Basic Concepts of Hotel Class">[Basic Concepts of Hotel Class](/.swm/basic-concepts-of-hotel-class.819utkga.sw.md)</SwmLink>
- <SwmLink doc-title="Exploring the Booking Entity">[Exploring the Booking Entity](/.swm/exploring-the-booking-entity.pq1lhgck.sw.md)</SwmLink>
- **Config**
  - <SwmLink doc-title="Basic Concepts of Configuration">[Basic Concepts of Configuration](/.swm/basic-concepts-of-configuration.hsn1nzrr.sw.md)</SwmLink>
  - <SwmLink doc-title="Understanding the Web MVC Configuration">[Understanding the Web MVC Configuration](/.swm/understanding-the-web-mvc-configuration.7q7byr4k.sw.md)</SwmLink>
  - <SwmLink doc-title="Basic Concepts of Web Flow Config">[Basic Concepts of Web Flow Config](/.swm/basic-concepts-of-web-flow-config.8hk4l57a.sw.md)</SwmLink>

### Primefaces showcase

The Primefaces showcase is a demonstration of how to use the Primefaces library in conjunction with Spring Web Flow. It is structured as a Maven project, with its dependencies defined in the <SwmPath>[pom.xml](/pom.xml)</SwmPath> file. The project includes a <SwmToken path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/jsf/FacesHelper.java" pos="8:4:4" line-data="public class FacesHelper {">`FacesHelper`</SwmToken> class, which provides a method <SwmToken path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/jsf/FacesHelper.java" pos="17:5:5" line-data="	public boolean isError() {">`isError`</SwmToken> that can be used in a Facelets View to conditionally render a box around messages. This is particularly useful when using PrimeFaces, as it allows for the use of `<p:messages/>` or `<p:growl>`. The project's main entry point is the <SwmPath>[booking-faces/src/main/webapp/index.html](/booking-faces/src/main/webapp/index.html)</SwmPath> file, which redirects the user to the `app/home` URL.

- <SwmLink doc-title="Getting Started with the Primefaces Showcase">[Getting Started with the Primefaces Showcase](/.swm/getting-started-with-the-primefaces-showcase.5ya1unb8.sw.md)</SwmLink>
- <SwmLink doc-title="Maven Configuration in PrimeFaces Showcase">[Maven Configuration in PrimeFaces Showcase](/.swm/maven-configuration-in-primefaces-showcase.0ge3nzv2.sw.md)</SwmLink>
- <SwmLink doc-title="Overview of Autocomplete">[Overview of Autocomplete](/.swm/overview-of-autocomplete.qf7uwm5r.sw.md)</SwmLink>
- **Validation**
  - <SwmLink doc-title="Basic Concepts of Validation">[Basic Concepts of Validation](/.swm/basic-concepts-of-validation.8rq0disa.sw.md)</SwmLink>
  - <SwmLink doc-title="Handling Exceptions When Validation Fails">[Handling Exceptions When Validation Fails](/.swm/handling-exceptions-when-validation-fails.j62175jt.sw.md)</SwmLink>

## Build Tools

- <SwmLink doc-title="Maven Configuration and Usage in Spring Web Flow Samples">[Maven Configuration and Usage in Spring Web Flow Samples](/.swm/maven-configuration-and-usage-in-spring-web-flow-samples.a2xw4jq2.sw.md)</SwmLink>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://app.swimm.io/)</sup></SwmMeta>
