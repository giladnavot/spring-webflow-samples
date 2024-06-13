---
title: Overview of Flows
---
Flows in the Spring Web Flow framework are a key abstraction for defining user interface logic. They are responsible for directing the execution of a task, such as filling out a form or navigating through a process. Each flow is defined in an XML file, which outlines the states and transitions that make up the flow.

In the primefaces-showcase application, flows are used to manage various user interactions. For example, there are flows for handling AJAX requests, file uploads, form validation, and more. Each of these flows is defined in its own XML file within the 'flows' directory.

Each flow XML file specifies the parent flow, which is a common flow that provides shared configuration for all the flows in the application. This parent flow is defined in the 'parent-flow.xml' file.

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/flows/ajax-primefaces/flow.xml" line="1">

---

# Flow Definition

This is an example of a flow definition. The flow is defined in an XML file, with the `flow` element as the root. The `view-state` element represents a state in the flow where the user interacts with the application. The `transition` element defines how the flow moves from one state to another based on the 'suggest' event. The `evaluate` element is an action that the flow performs, in this case, creating an email suggestion.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<flow xmlns="http://www.springframework.org/schema/webflow"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/webflow https://www.springframework.org/schema/webflow/spring-webflow-2.0.xsd"
	parent="parent-flow">

	<!--
		Also see ../parent-flow.xml. 
	-->

	<var name="userBean" class="org.springframework.samples.webflow.ajax.UserBean" />

	<view-state id="view">
		<transition on="suggest" >
			<evaluate expression="userBean.createEmailSuggestion(flowRequestContext)"
				result="viewScope.emailSuggestion" />
		</transition>
	</view-state>

</flow>
```

---

</SwmSnippet>

<SwmSnippet path="/primefaces-showcase/src/main/webapp/WEB-INF/flows/top-flow-with-embedded-subflow/flow.xml" line="1">

---

# Subflow Definition

This is an example of a subflow definition. A subflow is a reusable flow that can be called from another flow. In this case, the 'embedded-flow' subflow is called from the 'main' state of the parent flow. The `subflow-state` element represents the state in the parent flow where the subflow is called. The `input` element defines an input parameter that is passed to the subflow.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<flow xmlns="http://www.springframework.org/schema/webflow"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.springframework.org/schema/webflow https://www.springframework.org/schema/webflow/spring-webflow.xsd"
	parent="parent-flow">

	<!--
		Also see ../parent-flow.xml. 
	-->
	
	<view-state id="main">
		<transition on="start" to="embedded-flow"/>
	</view-state>

	<subflow-state id="embedded-flow" subflow="top-flow-with-embedded-subflow/embedded-flow">
		<input name="mode" value="'embedded'"/>
		<transition on="end" to="main"/>
	</subflow-state>
	
</flow>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
