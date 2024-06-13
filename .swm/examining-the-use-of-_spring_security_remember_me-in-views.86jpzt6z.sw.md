---
title: Examining the Use of _spring_security_remember_me in Views
---
This document will cover the role and usage of `_spring_security_remember_me` in the Spring Web Flow samples. We'll cover:

1. What is `_spring_security_remember_me`
2. How `_spring_security_remember_me` is used in the codebase
3. The functionality and purpose of `_spring_security_remember_me`

# What is `_spring_security_remember_me`

`_spring_security_remember_me` is an input field in the login form of the application. It is a checkbox that allows users to stay authenticated for a longer period without needing to enter their credentials again.

<SwmSnippet path="/booking-mvc/src/main/webapp/WEB-INF/login.html" line="87">

---

# How `_spring_security_remember_me` is used in the codebase

In the login form, `_spring_security_remember_me` is used as the name of a checkbox input. When this checkbox is selected by the user, it enables the remember-me functionality.

```html
                <input type="checkbox" name="_spring_security_remember_me" id="remember_me" />
                <label for="remember_me">Don't ask for my password for two weeks:</label>
```

---

</SwmSnippet>

# The functionality and purpose of `_spring_security_remember_me`

The `_spring_security_remember_me` checkbox is part of the Spring Security framework's remember-me authentication feature. When a user checks this box during login, the application will remember the user's session and won't ask for credentials again for a certain period, usually two weeks. This is achieved by storing a remember-me cookie in the user's browser.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
