---
title: Handling Exceptions When Validation Fails
---
This document will cover the process of handling exceptions when validation fails in the Spring Web Flow samples repository. We'll cover:

1. How validation messages are defined
2. How these messages are displayed when a validation error occurs

<SwmSnippet path="/primefaces-showcase/src/main/resources/ValidationMessages.properties" line="2">

---

# Defining Validation Messages

Validation messages are defined in the `ValidationMessages.properties` file. For example, the `@NotNull` constraint message is overridden here to display 'must be provided' when a null value is encountered.

```ini
# Overrides the default message for the @NotNull constraint.
#
jakarta.validation.constraints.NotNull.message=must be provided
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/messages.html" line="34">

---

# Displaying Validation Error Messages

When a validation error occurs, the error messages are displayed in the `messages.html` file. The `#fields.hasErrors('*')` checks if there are any errors, and if so, each error is displayed in a list item.

```html
    <ul th:if="${#fields.hasErrors('*')}" class="errors">
        <li th:each="err : ${#fields.errors('*')}" th:text="${err}">Input is incorrect</li>
    </ul>
```

---

</SwmSnippet>

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/hotels/booking/enterBookingDetails.html" line="59">

---

Similarly, in the `enterBookingDetails.html` file, if there are any validation errors, they are displayed in a span element.

```html
            <div class="error" th:if="${#fields.hasErrors('*')}">
                <span th:each="err : ${#fields.errors('*')}">
                  <span th:text="${err}">Input is incorrect</span><br />
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="follow-up"><sup>Powered by [Swimm](/)</sup></SwmMeta>
