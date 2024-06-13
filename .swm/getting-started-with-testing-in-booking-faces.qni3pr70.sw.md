---
title: Getting Started with Testing in Booking-Faces
---
In the 'booking-faces' project, 'Test' refers to the unit tests written to verify the functionality of the application. These tests are located in the 'src/test' directory. They are written using the JUnit framework and the EasyMock library for creating mock objects. The tests cover various aspects of the application such as the booking flow, main flow, and the services used in these flows.

<SwmSnippet path="/booking-faces/src/test/java/org/springframework/webflow/samples/booking/BookingFlowExecutionTests.java" line="13">

---

# BookingFlowExecutionTests

This class contains tests for the booking flow of the application. It extends `AbstractXmlFlowExecutionTests` which provides a framework for testing a flow execution. The `setUp` method is used to initialize the `BookingService` mock. The `getResource` method specifies the flow definition file to be used for the tests. The `configureFlowBuilderContext` method is used to register beans and services required for the tests. The `testStartBookingFlow` method is an example of a test case where a booking flow is started and the expected state and response are asserted.

```java
public class BookingFlowExecutionTests extends AbstractXmlFlowExecutionTests {

    private BookingService bookingService;

    protected void setUp() {
	bookingService = EasyMock.createMock(BookingService.class);
    }

    @Override
    protected FlowDefinitionResource getResource(FlowDefinitionResourceFactory resourceFactory) {
	return resourceFactory.createFileResource("src/main/webapp/WEB-INF/flows/booking/booking-flow.xml");
    }

    @Override
    protected void configureFlowBuilderContext(MockFlowBuilderContext builderContext) {
	builderContext.registerBean("bookingService", bookingService);
	builderContext.getFlowBuilderServices().setConversionService(new FacesConversionService());
    }

    public void testStartBookingFlow() {
	Booking booking = createTestBooking();
```

---

</SwmSnippet>

<SwmSnippet path="/booking-faces/src/test/java/org/springframework/webflow/samples/booking/MainFlowExecutionTests.java" line="21">

---

# MainFlowExecutionTests

This class contains tests for the main flow of the application. Similar to `BookingFlowExecutionTests`, it extends `AbstractXmlFlowExecutionTests` and overrides the same methods for setup and configuration. It contains test cases like `testStartMainFlow`, `testSearchHotels`, `testSelectHotel`, and `testBookHotel` which test different parts of the main flow.

```java
public class MainFlowExecutionTests extends AbstractXmlFlowExecutionTests {

    private BookingService bookingService;

    protected void setUp() {
	bookingService = EasyMock.createMock(BookingService.class);
    }

    @Override
    protected FlowDefinitionResource getResource(FlowDefinitionResourceFactory resourceFactory) {
	return resourceFactory.createFileResource("src/main/webapp/WEB-INF/flows/main/main-flow.xml");
    }

    @Override
    protected void configureFlowBuilderContext(MockFlowBuilderContext builderContext) {
	builderContext.registerBean("bookingService", bookingService);
	builderContext.getFlowBuilderServices().setConversionService(new FacesConversionService());
    }

    public void testStartMainFlow() {
	List<Booking> bookings = new ArrayList<Booking>();
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
