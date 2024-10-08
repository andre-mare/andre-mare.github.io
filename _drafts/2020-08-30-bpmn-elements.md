---
layout: post
title: "BPMN 2.0 Elements"
author: andre
categories: [ bpmn ]
tags: [bpmn, bpmn 2.0, bpmn elements]
image: /assets/images/feature-images/feature-image-bpmn-fundamentals.jpg
description: "This article describes the BPMN elements as they are defined within the BPMN 2.0 specification."
comments: true
related_posts:
- bpmn/_posts/2020-01-01-bpmn-ultimate-reference.md
- bpmn/_posts/2020-08-29-bpmn-diagrams.md
---

- Table of Contents
{:toc .large-only}


This article describes the BPMN elements as they are defined within the BPMN 2.0 specification. It furthermore serves as
a reference that describes each of the BPMN elements together with the associated notation. 

The basic BPMN modelling elements are very similar to flow diagrams. These elements are grouped into five basic 
categories namely: 
* [Flow Objects](#flow-objects) - Flow object elements defines the behavior of a business process.
* [Data](#data) - Data elements represent the data activities and processes need in order to execute.
* [Connecting Objects](#connecting-objects) Connecting object elements indicate the flow and associations within a process.
* [Swimlanes](#swimlanes) - Swimlane elements are used to group processes according to participants.
* [Artifacts](#artifacts) - Artifact elements provide additional information about the Process.

## Flow Objects
Flow Objects are the main graphical elements to define the behavior of a business process. There are three Flow Objects: 

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Activity](#activity) | An Activity is a generic term for work that company performs in a Process. An Activity can be atomic or non-atomic (compound). The types of Activities that are a part of a Process Model are: Call Activity, Subprocess and Task, which are rounded rectangles. | <iconify-icon height=48px data-icon="bpmn:task"></iconify-icon> |
| [Gateway](#gateway) | A Gateway is used to control the divergence and convergence of Sequence Flows in a Process. Thus, it will determine branching, forking, merging, and joining of paths. Internal markers will indicate the type of behavior control. | <iconify-icon height=48px data-icon="bpmn:gateway"></iconify-icon> |
| [Event](#event) | An Event is something that “happens” during the course of a Process. These Events affect the flow of the model and usually have a cause (trigger) or an impact (result). There are three types of Events, based on when they affect the flow: Start, Intermediate, and End. | <iconify-icon height=48px data-icon="bpmn:start-event"></iconify-icon> | 
{:.stretch-table}


### Activity
An Activity is a unit of work that is performed within a Business Process. An Activity can be atomic or non-atomic
(compound). 

The three types of activities are:
* [Task](#tasks) - A Task is an atomic activity since it has no internal sub parts. 
* [Subprocess](#subprocess) - A subprocess is non-atomic (compound), since it has subparts that can be expressed as a process flow. 
* [Call Activity](#call-activity) - A Call Activity identifies a point in the Process where a global Process or a Global Task is used.   

#### Tasks
A Task is an atomic Activity within a Process flow. A Task is used when the work in the Process cannot be broken down to
a finer level of detail. Generally, an end-user and/or applications are used to perform the Task when it is executed.

There are different types of Tasks identified within BPMN.

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Service Task](/bpmn-service-task) | A Service Task is a Task that uses some sort of service, which could be a Web service or an automated application. | <iconify-icon height=48px data-icon="bpmn:service-task"></iconify-icon> |
| [Send Task](/bpmn-send-task) | A Send Task is a simple Task that is designed to send a Message to an external Participant (relative to the Process). Once the Message has been sent, the Task is completed. | <iconify-icon height=48px data-icon="bpmn:send-task"></iconify-icon> |
| [Receive Task](/bpmn-receive-task) | A Receive Task is a simple Task that is designed to wait for a Message to arrive from an external Participant (relative to the Process). Once the Message has been received, the Task is completed. | <iconify-icon height=48px data-icon="bpmn:receive-task"></iconify-icon> |
| [User Task](/bpmn-user-task) | A User Task is a typical “workflow” Task where a human performer performs the Task with the assistance of a software application and is scheduled through a task list manager of some sort. | <iconify-icon height=48px data-icon="bpmn:user-task"></iconify-icon> |
| [Manual Task](/bpmn-manual-task) | A Manual Task is a Task that is expected to be performed without the aid of any business process execution engine or any application. An example of this could be a telephone technician installing a telephone at a customer location. | <iconify-icon height=48px data-icon="bpmn:manual-task"></iconify-icon> |
| [Business Rule Task](/bpmn-business-rule-task) | A Business Rule Task provides a mechanism for the Process to provide input to a Business Rules Engine and to get the output of calculations that the Business Rules Engine might provide.  | <iconify-icon height=48px data-icon="bpmn:business-rule-task"></iconify-icon> |
| [Script Task](/bpmn-script-task) | A Script Task is executed by a business process engine. The modeler or implementer defines a script in a language that the engine can interpret. When the Task is ready to start, the engine will execute the script. When the script is completed, the Task will also be completed. | <iconify-icon height=48px data-icon="bpmn:script-task"></iconify-icon> |
{:.stretch-table}


**Task Markers**

BPMN specifies three types of markers for Task: a Loop marker or a Multi-Instance marker and a Compensation marker. A
Task MAY have one or two of these markers.

| Task Marker | Description | Notation |
|-------------|-------------|:--------:|
| [Loop](/bpmn-task-marker) |  The marker for a Task that is a standard loop MUST be a small line with an arrowhead that curls back upon itself.  | <iconify-icon height=48px data-icon="bpmn:loop-marker"></iconify-icon> |
| [Multi-Instance](/bpmn-task-marker) | The marker for a Task that is a multi-instance MUST be a set of three vertical lines. | <span class="iconify" height=48px data-icon="bpmn:sequential-mi-marker" data-inline="false"></span> <span class="iconify" height=48px data-icon="bpmn:parallel-mi-marker" data-inline="false"></span>
| [Compensation](/bpmn-task-marker) | The marker for a Task that is used for compensation MUST be a pair of left facing triangles | <iconify-icon height=48px data-icon="bpmn:compensation-marker"></iconify-icon> |
{:.stretch-table}


#### Subprocess
A Subprocess is an Activity whose internal details have been modeled using Activities, Gateways, Events, and Sequence Flows. A Subprocess is a graphical object within a Process, but it also can be “opened up” to show a lower-level Process. Subprocesses define a contextual scope that can be used for attribute visibility, transactional scope, for the handling of exceptions, of Events, or for compensation.

The Subprocess can be in a collapsed view that hides its details or a Subprocess can be in an
expanded view that shows its details within the view of the Process in which it is contained. In the
collapsed form, the Subprocess object uses a marker to distinguish it as a Subprocess, rather than a Task.

There are different types of Subprocesses.

| Subprocess Type | Description | Notation |
|------------------|-------------|:--------:|
| [Embedded Subprocess](/bpmn-embedded-subprocess) | A Subprocess is an Activity whose internal details have been modeled using Activities, Gateways, Events, and Sequence Flows.  | <iconify-icon height=48px data-icon="bpmn:subprocess-expanded"></iconify-icon> |
| [Event Subprocess](/bpmn-event-subprocess) | An Event Subprocess is a specialized Subprocess that is used within a Process (or Subprocess). An Event Subprocess is not part of the normal flow of its parent Process—there are no incoming or outgoing Sequence Flows. | <iconify-icon height=48px data-icon="bpmn:event-subprocess-expanded"></iconify-icon> |
| [Transaction Subprocess](/bpmn-transaction-subprocess) | A Transaction is a specialized type of Subprocess that will have a special behavior that is controlled through a transaction protocol. There are three basic outcomes of a Transaction: Successful completion, Failed completion & Hazard. | <iconify-icon height=48px data-icon="bpmn:transaction"></iconify-icon> |
{:.stretch-table}

**Subprocess Markers**

BPMN specifies five types of standard markers for Subprocesses. The (Collapsed) Subprocess marker can be combined with four other markers: a loop marker or a multi-instance marker, a Compensation marker, and an Ad-Hoc marker. A collapsed Subprocess MAY have one to three of these other markers, in all combinations except that loop and multi-instance cannot be shown at the same time.

| Task Marker | Description | Notation |
|-------------|-------------|:--------:|
| [Loop](/bpmn-subprocess-marker) | The marker for a Subprocess that loops MUST be a small line with an arrowhead that curls back upon itself. | <iconify-icon height=48px data-icon="bpmn:loop-marker"></iconify-icon> |
| [Multi-Instance](/bpmn-subprocess-marker) | The marker for a Subprocess that has multiple instances MUST be a set of three vertical lines in parallel. |  <span class="iconify" height=48px data-icon="bpmn:sequential-mi-marker" data-inline="false"></span> <span class="iconify" height=48px data-icon="bpmn:parallel-mi-marker" data-inline="false"></span>
| [Compensation](/bpmn-subprocess-marker) | The marker for a Subprocess that is used for compensation MUST be a pair of left facing triangles. | <iconify-icon height=48px data-icon="bpmn:compensation-marker"></iconify-icon> |
| [Ad-Hoc](/bpmn-subprocess-marker) |  The marker for an ad-hoc Subprocess MUST be a “tilde” symbol. | <iconify-icon height=48px data-icon="bpmn:ad-hoc-marker"></iconify-icon> |
{:.stretch-table}

#### Call Activity
A Call Activity executes another process that may be external to the process definition.

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Call Activity](/bpmn-call-activity) | A Call Activity identifies a point in the Process where a global Process or a Global Task is used. The Call Activity acts as a ‘wrapper’ for the invocation of a global Process or Global Task within the execution. The activation of a call Activity results in the transfer of control to the called global Process or Global Task. | <iconify-icon height=48px data-icon="bpmn:call-activity"></iconify-icon> |
{:.stretch-table}


### Gateway
Gateways are used to control how Sequence Flows interact as they converge and diverge within a Process. If the
flow does not need to be controlled, then a Gateway is not needed. The term “Gateway” implies that there is a gating
mechanism that either allows or disallows passage through the Gateway. As tokens arrive at a Gateway they can be
merged together on input and/or split apart on output as the Gateway mechanisms are invoked.

Gateways, like Activities, are capable of consuming or generating additional tokens, effectively controlling
the execution semantics of a given Process.

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Exclusive Gateway](/bpmn-exclusive-gateway) | A diverging Exclusive Gateway (Decision) is used to create alternative paths within a Process flow. This is basically the “diversion point in the road” for a Process. For a given instance of the Process, only one of the paths can be taken. | <iconify-icon height=48px data-icon="bpmn:gateway-xor"></iconify-icon> |
| [Inclusive Gateway](/bpmn-inclusive-gateway) | A diverging Inclusive Gateway (Inclusive Decision) can be used to create alternative but also parallel paths within a Process flow. Unlike the Exclusive Gateway, all condition Expressions are evaluated. The true evaluation of one condition Expression does not exclude the evaluation of other condition Expressions. All Sequence Flows with a true evaluation will be traversed by a token. Since each path is considered to be independent, all combinations of the paths MAY be taken, from zero to all. However, it should be designed so that at least one path is taken. | <iconify-icon height=48px data-icon="bpmn:gateway-or"></iconify-icon> |
| [Parallel Gateway](/bpmn-parallel-gateway) | A Parallel Gateway is used to synchronize (combine) parallel flows and to create parallel flows. | <iconify-icon height=48px data-icon="bpmn:gateway-parallel"></iconify-icon> |
| [Complex Gateway](/bpmn-complex-gateway) | The Complex Gateway can be used to model complex synchronization behavior. An Expression activationCondition is used to describe the precise behavior. For example, this Expression could specify that tokens on three out of five incoming Sequence Flows are needed to activate the Gateway. | <iconify-icon height=48px data-icon="bpmn:gateway-complex"></iconify-icon> |
| [Event-based Gateway](/bpmn-event-based-gateway) | The Event-Based Gateway represents a branching point in the Process where the alternative paths that follow the Gateway are based on Events that occur, rather than the evaluation of Expressions using Process data (as with an Exclusive or Inclusive Gateway). A specific Event, usually the receipt of a Message, determines the path that will be taken. Basically, the decision is made by another Participant, based on data that is not visible to Process, thus, requiring the use of the Event-Based Gateway. | <iconify-icon height=48px data-icon="bpmn:gateway-eventbased"></iconify-icon> |
{:.stretch-table}

### Event
An Event is something that "happens" during the course of a Process. These Events affect the flow of the Process and usually have a cause or an impact and in general require or allow for a reaction. The term "event" is general enough to cover many things in a Process. The start of an Activity, the end of an Activity, the change of state of a document, a Message that arrives, etc., all could be considered Events.

Events allow for the description of event-driven processes. In these processes, there are three main types of Events:
* Start Events which indicate where a Process will start
* End Events which indicate where a path of a Process will end
* Intermediate Event

Within these three types, events come in two flavors:
* Events that catch a trigger. All Start Events and some Intermediate Events are catching Events.
* Events that throw a Result. All End Events and some Intermediate Events are throwing Events that MAY eventually be caught by another Event.

<table class="stretch-table" style="text-align: center;" border="1">
<tr><td rowspan="3"></td><td colspan="6" align="center">Catching Events</td><td colspan="2">Throwing Events</td></tr>
<tr><td colspan="3" align="center">Start Event</td><td colspan="4">Intermediate Event</td><td>End Event</td></tr>
<tr><td><SPAN STYLE="writing-mode: vertical-lr;-ms-writing-mode: tb-lr; transform: rotate(180deg);">Standard</SPAN></td><td><SPAN STYLE="writing-mode: vertical-rl;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Event Subprocess <br> Interrupting</SPAN></td><td><SPAN STYLE="writing-mode: vertical-rl;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Event Subprocess <br> Non-Interrupting</SPAN></td><td><SPAN STYLE="writing-mode: vertical-lr;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Catching</SPAN></td><td><SPAN STYLE="writing-mode: vertical-rl;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Boundary <br> Interrupting</SPAN></td><td><SPAN STYLE="writing-mode: vertical-rl;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Boundary Non-<br> Interrupting</SPAN></td><td><SPAN STYLE="writing-mode: vertical-lr;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Throwing</SPAN></td><td><SPAN STYLE="writing-mode: vertical-lr;-ms-writing-mode: tb-rl; transform: rotate(180deg);">Standard</SPAN></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-none-event">None Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-none"></iconify-icon></td><td></td><td></td><td></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-none"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:end-event-none"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-message-event">Message Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-message"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:end-event-message"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-timer-event">Timer Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-timer"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-timer"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-timer"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-timer"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-timer"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-timer"></iconify-icon></td><td></td><td></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-escalation-event">Escalation Event</a></td><td></td><td><iconify-icon height=48px data-icon="bpmn:start-event-escalation"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-escalation"></iconify-icon></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-escalation"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-escalation"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-escalation"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:end-event-escalation"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-conditional-event">Conditional Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-condition"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-condition"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-condition"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-condition"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-condition"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-condition"></iconify-icon></td><td></td><td></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-link-event">Link Event</a></td><td></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-link"></iconify-icon></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-link"></iconify-icon></td><td></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-error-event">Error Event</a></td><td></td><td><iconify-icon height=48px data-icon="bpmn:start-event-error"></iconify-icon></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-error"></iconify-icon></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:end-event-error"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-cancel-event">Cancel Event</a></td><td></td><td></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-cancel"></iconify-icon></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:end-event-cancel"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-compensation-event">Compensation Event</a></td><td></td><td><iconify-icon height=48px data-icon="bpmn:start-event-compensation"></iconify-icon></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-compensation"></iconify-icon></td><td></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-compensation"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:end-event-compensation"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-signal-event">Signal Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-signal"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:end-event-signal"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-multiple-event">Multiple Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-throw-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:end-event-multiple"></iconify-icon></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-parallel-multiple-event">Parallel Multiple Event</a></td><td><iconify-icon height=48px data-icon="bpmn:start-event-parallel-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-parallel-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:start-event-non-interrupting-parallel-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-parallel-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-parallel-multiple"></iconify-icon></td><td><iconify-icon height=48px data-icon="bpmn:intermediate-event-catch-non-interrupting-parallel-multiple"></iconify-icon></td><td></td><td></td></tr>
<tr><td style="text-align: left;"><a href="/bpmn-terminate-event">Terminate Event</a></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td><iconify-icon height=48px data-icon="bpmn:end-event-terminate"></iconify-icon></td></tr>
</table>


## Data
Activities and processes often need data in order to execute. Data is represented with the four elements: 

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Data Object](/bpmn-data-object) | Data Objects provide information about what Activities require to be performed and/or what they produce, Data Objects can represent a singular object or a collection of objects. | <iconify-icon height=48px data-icon="bpmn:data-object"></iconify-icon> |
| [Data Inputs](/bpmn-data-input) | Data requirements are captured as Data Inputs. | <iconify-icon height=48px data-icon="bpmn:data-input"></iconify-icon> |
| [Data Outputs](/bpmn-data-output) | Data that is produced is captured using Data Outputs. | <iconify-icon height=48px data-icon="bpmn:data-output"></iconify-icon> |
| [Data Stores](/bpmn-data-store) | A Data Store provides a mechanism for Activities to retrieve or update stored information that will persist beyond the scope of the Process. | <iconify-icon height=48px data-icon="bpmn:data-store"></iconify-icon> |
{:.stretch-table}

## Connecting Objects
There are multiple ways of connecting the Flow Objects to each other or other information. 

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Sequence Flow](#sequence-flow) | A Sequence Flow is used to show the order that Activities will be performed in a Process. | <iconify-icon height=48px data-icon="bpmn:connection"></iconify-icon> |
| [Message Flow](/bpmn-message-flow) | A Message Flow is used to show the flow of Messages between two Participants that are prepared to send and receive them. |  |
| [Association](/bpmn-association) | An Association is used to link information and Artifacts with BPMN graphical elements. Text Annotations and other Artifacts can be Associated with the graphical elements. The same as an association except, an arrowhead on the Association indicates a direction of flow (e.g., data), when appropriate. |  |
{:.stretch-table}

### Sequence Flow
A Sequence Flow is used to show the order that Activities will be performed in a Process and in a Choreography.

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Normal Flow](/bpmn-sequence-flow) | Normal flow refers to paths of Sequence Flow that do not start from an Intermediate Event attached to the boundary of an Activity. | <iconify-icon height=48px data-icon="bpmn:connection"></iconify-icon> |
| [Uncontrolled Flow](/bpmn-sequence-flow) | Uncontrolled flow refers to flow that is not affected by any conditions or does not pass through a Gateway. The simplest example of this is a single Sequence Flow connecting two Activities.  | <iconify-icon height=48px data-icon="bpmn:connection"></iconify-icon> |
| [Conditional Flow](/bpmn-sequence-flow) | A Sequence Flow can have a condition Expression that are evaluated at runtime to determine whether or not the Sequence Flow will be used.  | <iconify-icon height=48px data-icon="bpmn:conditional-flow"></iconify-icon> |
| [Default Flow](/bpmn-sequence-flow) | For Data-Based Exclusive Gateways or Inclusive Gateways, one type of flow is the default condition flow. This flow will be used only if all the other outgoing conditional flow is not true at runtime.  | <iconify-icon height=48px data-icon="bpmn:default-flow"></iconify-icon> |
{:.stretch-table}

## Swimlanes
There are two ways of grouping the primary modeling elements through Swimlanes: 

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Pool](/bpmn-pool) | A Pool is the graphical representation of a Participant in a Collaboration. It also acts as a “swimlane” and a graphical container for partitioning a set of Activities from other Pools. A Pool MAY have internal details, in the form of the Process that will be executed. Or a Pool MAY have no internal details, i.e., it can be a "black box." | <iconify-icon height=48px data-icon="bpmn:participant"></iconify-icon> |
| [Lane](/bpmn-lane) | A Lane is a sub-partition within a Process, sometimes within a Pool, and will extend the entire length of the Process, either vertically or horizontally. Lanes are used to organize and categorize Activities. | <iconify-icon height=48px data-icon="bpmn:lane-divide-two"></iconify-icon> |
{:.stretch-table}

## Artifacts
Artifacts are used to provide additional information about the Process. The current set of Artifacts includes:

| Element | Description | Notation |
|---------|-------------|:--------:|
| [Group](/bpmn-group) | A Group is a grouping of graphical elements that are within the same Category. This type of grouping does not affect the Sequence Flows within the Group. The Category name appears on the diagram as the group label. | <iconify-icon height=48px data-icon="bpmn:group"></iconify-icon> |
| [Text Annotation](/bpmn-text-annotation) | Text Annotations are a mechanism for a modeler to provide additional text information for the reader of a BPMN Diagram. | <iconify-icon height=48px data-icon="bpmn:text-annotation"></iconify-icon> |
{:.stretch-table}

## Summary
Congratulations! You have finished the post about BPMN 2.0 Elements. Follow me on any of the different social media platforms and feel free to leave comments.

[1]:https://www.omg.org/spec/BPMN/2.0/PDF