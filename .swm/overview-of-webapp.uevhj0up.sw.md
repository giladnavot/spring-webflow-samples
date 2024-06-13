---
title: Overview of Webapp
---
Webapp in the booking-mvc project refers to the web application's resources. It contains all the necessary files for the web application to function properly. This includes HTML files for the user interface, CSS files for styling, images for visual elements, and configuration files in the WEB-INF directory.

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/enterBookingDetails.html" line="57">

---

## HTML Files

This is an example of an HTML file in the Webapp directory. It contains a form for entering booking details.

```html
        <form id="booking" action="#" th:object="${booking}" th:action="${flowExecutionUrl}" method="post">

            <div class="error" th:if="${#fields.hasErrors('*')}">
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/styles/booking.css" line="1">

---

## CSS Stylesheets

This is an example of a CSS stylesheet in the Webapp directory. It defines the styles for various elements in the web application.

```css

a,a:visited,a:link,a:active {
	color: #59924B;
	background-color: transparent;
	text-decoration: none;
	font-weight: bold;
}

a:hover {
	color: white;
	background-color: #65a242;
	text-decoration: none;
	font-weight: bold;
}

button {
	color: #fff;
	background: #fff url(../images/btn.bg.gif) 0 0 repeat-x;
	border-style: none;
}

```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/booking-flow.xml" line="4">

---

## Configuration Files

This is an example of a configuration file in the Webapp directory. It defines the flow of the booking process in the web application.

```xml
      xsi:schemaLocation="
      	http://www.springframework.org/schema/webflow
      	https://www.springframework.org/schema/webflow/spring-webflow-2.0.xsd">

	<secured attributes="ROLE_USER" />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://staging.swimm.cloud/)</sup></SwmMeta>
