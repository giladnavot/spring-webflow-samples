---
title: Basic Concepts of Hotels in Booking-MVC
---
Hotels in the booking-mvc application refer to the entities that users can search for and book. They are represented in various forms across the application, such as in search results, booking details, and booking reviews.

The 'hotelResults' id in the 'list.html' file is used to display a list of hotels that match the user's search criteria. This list is dynamically populated based on the user's input.

Each hotel has associated details that can be viewed and booked by the user. These details are managed through various files in the 'hotels' directory, such as 'show.html' for displaying hotel details, and 'bookingsTable.html' for managing hotel bookings.

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/search.html" line="1">

---

# Hotel Search

The 'search.html' file provides the user interface for searching hotels. It includes a form for entering search criteria and a section for displaying the search results.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 
      xmlns:th="http://www.thymeleaf.org"
      lang="en">

<head th:replace="layouts/standard.html :: //head">

    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
    <!-- This <head> section is only used for static prototyping purposes.             -->
    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->

    <title>Spring Travel: Spring MVC and Web Flow Reference Application</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    
    <link rel="stylesheet" type="text/css" media="screen, projection" 
          href="../../styles/blueprint/screen.css" />
    
    <link rel="stylesheet" type="text/css" media="print" 
          href="../../styles/blueprint/print.css" />
    
    <!--[if lt IE 8]>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/show.html" line="1">

---

# Hotel Details

The 'show.html' file displays the details of a selected hotel. It includes the hotel's name, address, and nightly rate, and provides an option to book the hotel.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 
      xmlns:th="http://www.thymeleaf.org"
      xmlns:tiles="http://www.thymeleaf.org"
      xmlns:sec="http://www.thymeleaf.org"
      lang="en">

<head th:replace="layouts/standard.html :: //head">

    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
    <!-- This <head> section is only used for static prototyping purposes.             -->
    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->

    <title>Spring Travel: Spring MVC and Web Flow Reference Application</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />

    <link rel="stylesheet" type="text/css" media="screen, projection"
          href="../../styles/blueprint/screen.css" />

    <link rel="stylesheet" type="text/css" media="print"
          href="../../styles/blueprint/print.css" />
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/booking-flow.xml" line="16">

---

# Hotel Booking

The 'booking-flow.xml' file defines the flow of the hotel booking process. It specifies the sequence of pages, starting from entering booking details to reviewing the booking.

```xml
	<view-state id="enterBookingDetails" model="booking" view="/hotels/booking/enterBookingDetails.html">
		<binder>
			<binding property="checkinDate" />
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/bookingsTable.html" line="1">

---

# Hotel Bookings Review

The 'bookingsTable.html' file displays a table of the current hotel bookings. It includes details such as the hotel name, address, check-in and check-out dates, and a cancellation option.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 
      xmlns:th="http://www.thymeleaf.org"
      xmlns:sec="http://www.thymeleaf.org"
      lang="en">

<head th:replace="layouts/standard.html :: //head">

    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->
    <!-- This <head> section is only used for static prototyping purposes.             -->
    <!-- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -->

    <title>Spring Travel: Spring MVC and Web Flow Reference Application</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    
    <link rel="stylesheet" type="text/css" media="screen, projection" 
          href="../../styles/blueprint/screen.css" />
    
    <link rel="stylesheet" type="text/css" media="print" 
          href="../../styles/blueprint/print.css" />
    
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
