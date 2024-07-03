---
title: Understanding the Hotel Lazy Data Model
---
The HotelLazyDataModel is a class that extends the LazyDataModel from PrimeFaces. It is designed to handle the loading of hotel data in a lazy manner, meaning it only loads the data that is needed for the current view, improving performance for large datasets. It uses a SearchCriteria object to filter and sort the data, and a BookingService to retrieve the data from the database. The class also provides methods for counting the total number of hotels, loading a specific page of hotel data, and getting the row data for a specific hotel.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="13">

---

# HotelLazyDataModel Class

This is the HotelLazyDataModel class. It extends the LazyDataModel class from PrimeFaces and overrides several methods to provide custom behavior for loading and managing Hotel data. It also contains additional properties and methods for managing the selected Hotel and the current page.

```java
public class HotelLazyDataModel extends LazyDataModel<Hotel> {

	private static final long serialVersionUID = -8832831134966938627L;

	private SearchCriteria searchCriteria;

	private BookingService bookingService;

	private List<Hotel> hotels;

	private Hotel selected;


	@Autowired
	public void setBookingService(BookingService bookingService) {
		this.bookingService = bookingService;
	}

	public void setSearchCriteria(SearchCriteria searchCriteria) {
		this.searchCriteria = searchCriteria;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/webapp/WEB-INF/flows/main/reviewHotels.xhtml" line="10">

---

# HotelLazyDataModel Usage

Here is an example of how the HotelLazyDataModel is used. It is set as the data model for the PrimeFaces data table component in the reviewHotels view.

```html
		This page uses the PrimeFaces data table backed by a lazily loaded DataModel (see <strong>HotelLazyDataModel.java</strong>).
		Page navigation is Ajax-based and uses JSF 2 partial rendering.
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="41">

---

# HotelLazyDataModel Data Loading

This is the load method of the HotelLazyDataModel. It is responsible for loading the Hotel data on demand. It uses the BookingService to find the Hotels based on the current page, sort field, and sort order.

```java
	public List<Hotel> load(int first, int pageSize, Map<String, SortMeta> sortBy, Map<String, FilterMeta> filterBy) {
		this.searchCriteria.setCurrentPage(first / pageSize + 1);
		String sortField = null;
		SortOrder sortOrder = SortOrder.ASCENDING;
		if (!sortBy.isEmpty()) {
			SortMeta sortMeta = sortBy.values().iterator().next();
			sortField = sortMeta.getField();
			sortOrder = sortMeta.getOrder();
		}
		this.hotels = bookingService.findHotels(searchCriteria, first, sortField, !sortOrder.equals(SortOrder.DESCENDING));
		return hotels;
	}
```

---

</SwmSnippet>

# HotelLazyDataModel Functions

The HotelLazyDataModel class contains several important methods that manage the data related to hotels.

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="26">

---

## setBookingService

The `setBookingService` method is used to set the booking service. This service is used in other methods of this class to interact with the database.

```java
	@Autowired
	public void setBookingService(BookingService bookingService) {
		this.bookingService = bookingService;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="31">

---

## setSearchCriteria

The `setSearchCriteria` method is used to set the search criteria. This criteria is used when fetching hotels from the database.

```java
	public void setSearchCriteria(SearchCriteria searchCriteria) {
		this.searchCriteria = searchCriteria;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="35">

---

## count

The `count` method is used to get the number of hotels that match the search criteria. This is used for pagination in the user interface.

```java
	@Override
	public int count(Map<String, FilterMeta> filterBy) {
		return bookingService.getNumberOfHotels(this.searchCriteria);
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="40">

---

## load

The `load` method is used to fetch a specific page of hotels from the database. It uses the search criteria, sorting, and pagination parameters to construct the database query.

```java
	@Override
	public List<Hotel> load(int first, int pageSize, Map<String, SortMeta> sortBy, Map<String, FilterMeta> filterBy) {
		this.searchCriteria.setCurrentPage(first / pageSize + 1);
		String sortField = null;
		SortOrder sortOrder = SortOrder.ASCENDING;
		if (!sortBy.isEmpty()) {
			SortMeta sortMeta = sortBy.values().iterator().next();
			sortField = sortMeta.getField();
			sortOrder = sortMeta.getOrder();
		}
		this.hotels = bookingService.findHotels(searchCriteria, first, sortField, !sortOrder.equals(SortOrder.DESCENDING));
		return hotels;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="54">

---

## getRowData

The `getRowData` method is used to get the hotel that corresponds to a specific row key. This is used in the user interface to display the details of a selected hotel.

```java
	@Override
	public Hotel getRowData(String rowKey) {
		for (Hotel hotel : this.hotels){
			if (hotel.getId().equals(Long.valueOf(rowKey))) {
				return hotel;
			}
 		}
		return null;
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="64">

---

## getRowKey

The `getRowKey` method is used to get the row key that corresponds to a specific hotel. This is used in the user interface to identify the selected hotel.

```java
	@Override
	public String getRowKey(Hotel hotel) {
		return String.valueOf(hotel.getId());
	}
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/main/java/org/springframework/webflow/samples/booking/HotelLazyDataModel.java" line="69">

---

## getRowCount

The `getRowCount` method is used to get the total number of rows, which is the total number of hotels that match the search criteria. This is used for pagination in the user interface.

```java
	@Override
	public int getRowCount() {
		return bookingService.getNumberOfHotels(searchCriteria);
	}
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples" doc-type="overview"><sup>Powered by [Swimm](/)</sup></SwmMeta>
