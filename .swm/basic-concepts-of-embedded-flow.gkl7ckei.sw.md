---
title: Basic Concepts of Embedded Flow
---
An embedded flow in Spring Web Flow is a sub-flow that is called within the context of a parent flow. It's a reusable module that can be included in multiple parent flows. In the `embedded-flow` directory, the `flow.xml` file defines the flow of the application. It contains view states like `step1` and `step2`, and end states like `success` and `cancel`. Each state represents a step in the flow and defines transitions to other states based on events. The JSP files like `step1.jsp`, `step2.jsp`, `success.jsp`, and `cancel.jsp` are the views associated with these states. The `views.xml` file is a Tiles definitions file that maps logical view names to JSP files.

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/flow.xml" line="1">

---

# Embedded Flow Definition

This is the definition of the embedded flow. It consists of two view states (`step1` and `step2`), and two end states (`success` and `cancel`). Transitions between the states are defined using the 'transition' element.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<flow xmlns="http://www.springframework.org/schema/webflow"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="
		http://www.springframework.org/schema/webflow 
		https://www.springframework.org/schema/webflow/spring-webflow.xsd">

	<view-state id="step1" view="embeddedFlow/step1">
		<transition on="next" to="step2"/> 
		<transition on="cancel" to="cancel"/>
	</view-state>

	<view-state id="step2" view="embeddedFlow/step2">
		<transition on="previous" to="step1"/>
		<transition on="finish" to="success"/>
		<transition on="cancel" to="cancel"/>
	</view-state>

	<end-state id="success" view="embeddedFlow/success"/>

	<end-state id="cancel" view="embeddedFlow/cancel"/>
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/step1.jsp" line="1">

---

# Using the Embedded Flow

This is an example of how the embedded flow is used. The 'step1' view state is rendered using the `step1.jsp` file. The 'next' and 'cancel' events trigger transitions to the 'step2' and 'cancel' states, respectively.

```java server pages
<div id="embeddedFlow">
	<p class="notice">This is step 1 of the embedded flow</p>
	<form id="step1" action="${flowExecutionUrl}" method="POST">
		<input type="hidden" name="${_csrf.parameterName}" value="${_csrf.token}"/>
		<button id="cancel" type="submit" name="_eventId_cancel">Cancel</button>
		<button id="next" type="submit" name="_eventId_next">Next &gt;&gt;</button>
		<script type="text/javascript">
			Spring.addDecoration(new Spring.AjaxEventDecoration({elementId:'next',event:'onclick',formId:'step1',params:{fragments:"body"}}));
			Spring.addDecoration(new Spring.AjaxEventDecoration({elementId:'cancel',event:'onclick',formId:'step1',params:{fragments:"body"}}));
		</script>
	</form>
</div>
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/step2.jsp" line="1">

---

Similarly, the 'step2' view state is rendered using the `step2.jsp` file. The 'previous', 'finish', and 'cancel' events trigger transitions to the 'step1', 'success', and 'cancel' states, respectively.

```java server pages
<div id="embeddedFlow">
	<p class="notice">This is step 2 of the embedded flow</p>
	<form id="step2" action="${flowExecutionUrl}" method="POST">
		<input type="hidden" name="${_csrf.parameterName}" value="${_csrf.token}"/>
		<button id="cancel" type="submit" name="_eventId_cancel">Cancel</button>
		<button id="previous" type="submit" name="_eventId_previous">&lt;&lt; Previous</button>
		<button id="finish" type="submit" name="_eventId_finish">Finish &gt;&gt;</button>
		<script type="text/javascript">
			Spring.addDecoration(new Spring.AjaxEventDecoration({elementId:'finish',event:'onclick',formId:'step2',params:{fragments:"body"}}));
			Spring.addDecoration(new Spring.AjaxEventDecoration({elementId:'previous',event:'onclick',formId:'step2',params:{fragments:"body"}}));
			Spring.addDecoration(new Spring.AjaxEventDecoration({elementId:'cancel',event:'onclick',formId:'step2',params:{fragments:"body"}}));
		</script>
	</form>
</div>
```

---

</SwmSnippet>

# Embedded Flow Functions

The Embedded flow consists of several view-states and end-states that guide the user through a process. The flow is defined in the flow.xml file and each state is associated with a specific view.

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/flow.xml" line="8">

---

## View-State

The view-state represents a stage in the flow where a view is displayed to the user. In the Embedded flow, there are two view-states: 'step1' and 'step2'. Each view-state is associated with a specific view (e.g., 'embeddedFlow/step1' and 'embeddedFlow/step2') and defines transitions to other states based on user actions.

```xml
	<view-state id="step1" view="embeddedFlow/step1">
		<transition on="next" to="step2"/> 
		<transition on="cancel" to="cancel"/>
	</view-state>

	<view-state id="step2" view="embeddedFlow/step2">
		<transition on="previous" to="step1"/>
		<transition on="finish" to="success"/>
```

---

</SwmSnippet>

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/flow.xml" line="19">

---

## End-State

The end-state represents the end of the flow. In the Embedded flow, there are two end-states: 'success' and 'cancel'. Each end-state is associated with a specific view (e.g., 'embeddedFlow/success' and 'embeddedFlow/cancel').

```xml
	<end-state id="success" view="embeddedFlow/success"/>

	<end-state id="cancel" view="embeddedFlow/cancel"/>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
