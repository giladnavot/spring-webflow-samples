---
title: Overview of Autocomplete
---
Autocomplete in the spring-webflow-samples repository is a feature implemented in the 'primefaces-showcase' module. It is designed to provide suggestions to the user as they type into a form field. This is achieved through the use of a 'Person' class, which represents the data being inputted, and a 'PersonService' class, which provides the logic for generating the autocomplete suggestions.

<SwmSnippet path="/primefaces-showcase/src/main/java/org/springframework/samples/webflow/autocomplete/Person.java" line="1">

---

# Autocomplete in Person.java

The Person class in the autocomplete package is a part of the Autocomplete implementation. It's a model class that represents a person, which could be used as a part of the data source for the Autocomplete feature.

```java
package org.springframework.samples.webflow.autocomplete;

import java.io.Serializable;

public class Person implements Serializable {
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
