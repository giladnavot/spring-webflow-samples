---
title: Understanding the Role of WEB-INF in Web Applications
---
The `WEB-INF` directory in a web application is a location that provides a secure place to store resources such as classes, libraries, and configuration files that are used by the application. It is not accessible directly from the web and is typically used to store resources that are not intended to be served directly to a user.

In the `booking-mvc` application, the `WEB-INF` directory contains HTML files that define the views of the application. These files are used by the Spring MVC framework to generate the user interface of the application. The `layouts` directory contains a standard layout that is used by multiple views, and the `hotels` directory contains views specific to the hotel booking functionality.

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/reviewBooking.html" line="1">

---

# Thymeleaf Templates

This is an example of a Thymeleaf template used to generate the HTML for the review booking page. It uses Thymeleaf syntax to bind data from the model to the view.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 
      xmlns:th="http://www.thymeleaf.org"
      lang="en">

<head th:replace="layouts/standard.html :: //head">

    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
    <!-- This <head> section is only used for static prototyping purposes.             -->
    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/messages.properties" line="1">

---

# Messages Properties Files

This is an example of a messages properties file used to display messages in the web application. It contains key-value pairs, where the key is a message code and the value is the message text.

```ini
booking.checkinDate.NotNull=The check in date is required
booking.checkinDate.Future=The check in date must be in the future
booking.checkinDate.beforeToday=The check in date must be a future date
booking.checkinDate.typeMismatch=The check in date must be in the format mm-dd-yyyy

booking.checkoutDate.Future=The check out date must be in the future
booking.checkoutDate.NotNull=The check out date is required
booking.checkoutDate.typeMismatch=The check out date must be in the format mm-dd-yyyy
booking.BookingDateRange=The check out date must be later than the check in date

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/booking-flow.xml" line="1">

---

# Spring Web Flow Configuration Files

This is an example of a Spring Web Flow configuration file. It defines the flow of the web application, including the states, transitions, and actions.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<flow xmlns="http://www.springframework.org/schema/webflow"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="
      	http://www.springframework.org/schema/webflow
      	https://www.springframework.org/schema/webflow/spring-webflow-2.0.xsd">

	<secured attributes="ROLE_USER" />

	<input name="hotelId" required="true" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
