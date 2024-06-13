---
title: Introduction to Flows
---
Flows in Spring Web Flow are a sequence of steps that guide a user through a process or some business logic. It's a way to manage and encapsulate sequences of user interactions.

Each flow is defined in an XML file, like the ones in the 'embedded-flow' and 'embedded-flow-in-modal-dialog' directories. These XML files define the states of the flow and the transitions between them.

For example, in the 'embedded-flow' directory, the flow.xml file defines a flow with states 'step1', 'step2', 'success', and 'cancel'. Each state represents a step in the process, and transitions define how to move from one state to another based on user actions.

The 'view-state' elements represent states in which a view is displayed to the user, and the 'end-state' elements represent terminal states of the flow. The 'transition' elements define the navigation rules between states.

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow/flow.xml" line="1">

---

# Flow Definition

This is an example of a flow definition. It defines two view states (`step1` and `step2`), and two end states (`success` and `cancel`). Transitions are defined to move between these states based on user actions.

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

# Flow Views

This is an example of a view associated with a state in a flow. The view is a JSP file that generates the HTML to be displayed to the user when the flow is in the associated state.

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

<SwmSnippet path="/webflow-showcase/src/main/webapp/WEB-INF/flows/embedded-flow-in-modal-dialog/flow.xml" line="1">

---

# Flow Transitions

This is another example of a flow definition, showing how transitions are defined. The `on` attribute of the `transition` element specifies the event that triggers the transition, and the `to` attribute specifies the state to transition to.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<flow xmlns="http://www.springframework.org/schema/webflow"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="
		http://www.springframework.org/schema/webflow 
		https://www.springframework.org/schema/webflow/spring-webflow.xsd">

	<view-state id="step1" view="embeddedFlowInModalDialog/step1">
		<transition on="next" to="step2"/> 
		<transition on="cancel" to="cancel"/>
	</view-state>

	<view-state id="step2" view="embeddedFlowInModalDialog/step2">
		<transition on="previous" to="step1"/>
		<transition on="finish" to="success"/>
		<transition on="cancel" to="cancel"/>
	</view-state>

	<end-state id="success" view="externalRedirect:embeddedFlowInModalDialogContainer?result=success"/>

	<end-state id="cancel" view="externalRedirect:embeddedFlowInModalDialogContainer?result=cancel"/>
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBc3ByaW5nLXdlYmZsb3ctc2FtcGxlcyUzQSUzQWdpbGFkbmF2b3Q=" repo-name="spring-webflow-samples"><sup>Powered by [Swimm](/)</sup></SwmMeta>
