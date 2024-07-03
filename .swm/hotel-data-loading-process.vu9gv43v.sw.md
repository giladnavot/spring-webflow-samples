---
title: Hotel Data Loading Process
---
This document will cover the process of loading hotel data in the Spring Web Flow samples project. The process includes the following steps:

1. Invoking the <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" pos="41:8:8" line-data="	public List&lt;Hotel&gt; load(int first, int pageSize, Map&lt;String, SortMeta&gt; sortBy, Map&lt;String, FilterMeta&gt; filterBy) {">`load`</SwmToken> function in <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java](/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java)</SwmPath>
2. Calling the <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="45:8:8" line-data="	public List&lt;Hotel&gt; findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {">`findHotels`</SwmToken> function in <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java](/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java)</SwmPath>
3. Retrieving the search pattern via <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="46:7:7" line-data="		String pattern = getSearchPattern(criteria);">`getSearchPattern`</SwmToken> function
4. Getting the search string from <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking/SearchCriteria.java](/booking-faces/src/main/java/org/springframework/webflow/samples/booking/SearchCriteria.java)</SwmPath>.

```mermaid
graph TD;
subgraph booking-faces/src/main/java/org/springframework/webflow/samples/booking
  load:::mainFlowStyle --> findHotels
end
subgraph booking-faces/src/main/java/org/springframework/webflow/samples/booking
  findHotels:::mainFlowStyle --> getSearchPattern
end
subgraph booking-faces/src/main/java/org/springframework/webflow/samples/booking
  getSearchPattern:::mainFlowStyle --> getSearchString
end
  getSearchString:::mainFlowStyle --> ...

classDef mainFlowStyle color:#000000,fill:#7CB9F4
classDef rootsStyle color:#000000,fill:#00FFF4
classDef Style1 color:#000000,fill:#00FFAA
classDef Style2 color:#000000,fill:#FFFF00
classDef Style3 color:#000000,fill:#AA7CB9

%% Swimm:
%% graph TD;
%% subgraph <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking//](/booking-faces/src/main/java/org/springframework/webflow/samples/booking//)</SwmPath>
%%   load:::mainFlowStyle --> <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="45:8:8" line-data="	public List&lt;Hotel&gt; findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {">`findHotels`</SwmToken>
%% end
%% subgraph <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking//](/booking-faces/src/main/java/org/springframework/webflow/samples/booking//)</SwmPath>
%%   findHotels:::mainFlowStyle --> <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="46:7:7" line-data="		String pattern = getSearchPattern(criteria);">`getSearchPattern`</SwmToken>
%% end
%% subgraph <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking//](/booking-faces/src/main/java/org/springframework/webflow/samples/booking//)</SwmPath>
%%   getSearchPattern:::mainFlowStyle --> <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="97:10:10" line-data="		if (StringUtils.hasText(criteria.getSearchString())) {">`getSearchString`</SwmToken>
%% end
%%   getSearchString:::mainFlowStyle --> ...
%% 
%% classDef mainFlowStyle color:#000000,fill:#7CB9F4
%% classDef rootsStyle color:#000000,fill:#00FFF4
%% classDef Style1 color:#000000,fill:#00FFAA
%% classDef Style2 color:#000000,fill:#FFFF00
%% classDef Style3 color:#000000,fill:#AA7CB9
```

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="1">

---

# Invoking the <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" pos="41:8:8" line-data="	public List&lt;Hotel&gt; load(int first, int pageSize, Map&lt;String, SortMeta&gt; sortBy, Map&lt;String, FilterMeta&gt; filterBy) {">`load`</SwmToken> function

The <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" pos="41:8:8" line-data="	public List&lt;Hotel&gt; load(int first, int pageSize, Map&lt;String, SortMeta&gt; sortBy, Map&lt;String, FilterMeta&gt; filterBy) {">`load`</SwmToken> function in <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java](/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java)</SwmPath> is the entry point for this flow. It is responsible for loading hotel data.

```java
package org.springframework.webflow.samples.booking;
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="43">

---

# Calling the <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="45:8:8" line-data="	public List&lt;Hotel&gt; findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {">`findHotels`</SwmToken> function

The <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="45:8:8" line-data="	public List&lt;Hotel&gt; findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {">`findHotels`</SwmToken> function is called by <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" pos="41:8:8" line-data="	public List&lt;Hotel&gt; load(int first, int pageSize, Map&lt;String, SortMeta&gt; sortBy, Map&lt;String, FilterMeta&gt; filterBy) {">`load`</SwmToken>. It takes a <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="45:10:10" line-data="	public List&lt;Hotel&gt; findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {">`SearchCriteria`</SwmToken> object, and other parameters to find and return a list of hotels that match the criteria.

```java
	@Transactional(readOnly = true)
	@SuppressWarnings("unchecked")
	public List<Hotel> findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {
		String pattern = getSearchPattern(criteria);
		orderBy = (orderBy != null) ? orderBy : "name";
		String orderDirection = (ascending) ? " ASC" : " DESC";
		return em
				.createQuery(
						"select h from Hotel h where lower(h.name) like :pattern or lower(h.city) like :pattern "
								+ "or lower(h.zip) like :pattern or lower(h.address) like :pattern order by h."
								+ orderBy + orderDirection).setParameter("pattern", pattern)
								.setMaxResults(criteria.getPageSize()).setFirstResult(firstResult).getResultList();
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" line="94">

---

# Retrieving the search pattern

<SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="96:5:5" line-data="	private String getSearchPattern(SearchCriteria criteria) {">`getSearchPattern`</SwmToken> is a helper function used by <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="45:8:8" line-data="	public List&lt;Hotel&gt; findHotels(SearchCriteria criteria, int firstResult, String orderBy, boolean ascending) {">`findHotels`</SwmToken> to generate a search pattern from the <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="96:7:7" line-data="	private String getSearchPattern(SearchCriteria criteria) {">`SearchCriteria`</SwmToken> object.

```java
	// helpers

	private String getSearchPattern(SearchCriteria criteria) {
		if (StringUtils.hasText(criteria.getSearchString())) {
			return "%" + criteria.getSearchString().toLowerCase().replace('*', '%') + "%";
		} else {
			return "%";
		}
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/SearchCriteria.java" line="28">

---

# Getting the search string

<SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/SearchCriteria.java" pos="28:5:5" line-data="	public String getSearchString() {">`getSearchString`</SwmToken> is a method in <SwmPath>[booking-faces/src/main/java/org/springframework/webflow/samples/booking/SearchCriteria.java](/booking-faces/src/main/java/org/springframework/webflow/samples/booking/SearchCriteria.java)</SwmPath> that returns the search string. This string is used by <SwmToken path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/JpaBookingService.java" pos="46:7:7" line-data="		String pattern = getSearchPattern(criteria);">`getSearchPattern`</SwmToken> to generate the search pattern.

```java
	public String getSearchString() {
		return searchString;
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](https://app.swimm.io/)</sup></SwmMeta>
