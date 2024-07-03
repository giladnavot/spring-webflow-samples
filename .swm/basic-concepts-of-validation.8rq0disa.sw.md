---
title: Basic Concepts of Validation
---
Validation in the spring-webflow-samples repository refers to the process of checking the correctness of data. It is used to ensure that the data entered by the user or received from another source meets the specified criteria and is free from errors. For instance, in the `Account` class, the `@NotEmpty` annotation is used to validate that the `firstName` and `lastName` fields are not empty. Similarly, in the `Reservation` class, the `validate` and `validateEdit` methods are used to check if the `startDate` is before the `endDate`. If the validation fails, an error message is added to the `MessageContext`.

# Validation in Account Class

In the Account class, the @NotEmpty annotation is used to ensure that the firstName and lastName fields are not empty. The @Past and @NotNull annotations are used to ensure that the dateOfBirth field is not null and contains a date in the past.

# Validation in Reservation Class

In the Reservation class, the validateEdit and validate methods are used to check if the startDate is before the endDate. If the startDate is after the endDate, an error message is added to the messageContext.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
