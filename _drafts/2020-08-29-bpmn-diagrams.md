---
layout: post
title: "BPMN 2.0 Diagrams"
author: andre
categories: [ bpmn ]
tags: [bpmn, bpmn 2.0, bpmn fundamentals]
image: /assets/images/feature-images/feature-image-bpmn-fundamentals.jpg
description: "The fundamentals of BPMN 2.0 is all about the different types of diagrams and also about the set of elements used during the process modelling."
comments: true
related_posts:
- bpmn/_posts/2020-01-01-bpmn-ultimate-reference.md
- bpmn/_posts/2020-08-30-bpmn-elements.md
---

- Table of Contents
{:toc .large-only}

The BPMN 2.0 Diagram contains information about the different types of BPMN diagrams together with the set of
elements used during the modelling process.

## What is BPMN?
> "Business Process Model and Notation has become the de-facto standard for business processes diagrams. It is intended
> to be used directly by the stakeholders who design, manage and realize business processes, but at the same time be
> precise enough to allow BPMN diagrams to be translated into software process components. BPMN has an easy-to-use
> flowchart-like notation that is independent of any particular implementation environment." ~ [BPMN Specification](https://www.omg.org/spec/BPMN/2.0.2/)

## BPMN 2.0 Diagrams
The BPMN 2.0.2 aims to cover three basic models of Processes: private Processes, public Processes, and Choreographies. Within and between these three BPMN sub-models, many types of diagrams can be created.

### Process Diagram
#### Private (Internal) Business Process
Private Business Processes are those internal to a specific organization. There are two types of private Processes: executable and non-executable. 

An executable Process is a Process that has been modeled for the purpose of being executed. Information needed for execution, such as formal condition Expressions are included in an executable Process.

A non-executable Process is a private Process that has been modeled for the purpose of documenting Process behavior at a modeler-defined level of detail. Thus, information needed for execution, such as formal condition Expressions are typically not included in a non-executable Process.

<img alt="BPMN Activity" src="/assets/images/posts/bpmn-fundamentals/private_business_process.png" width="100%"/>

#### Public Process
A public Process represents the interactions between a private Business Process and another Process or Participant. Only those Activities that are used to communicate to the other Participant(s) are included in the public Process. All other “internal” Activities of the private Business Process are not shown in the public Process. Thus, the public Process shows to the outside world the Message Flows and the order of those Message Flows that are needed to interact with that Process.

<img alt="BPMN Activity" src="/assets/images/posts/bpmn-fundamentals/public_process.png" width="100%"/>

### Collaboration Diagram
A Collaboration depicts the interactions between two or more business entities. A Collaboration usually contains two or more Pools, representing the Participants in the Collaboration. The Message exchange between the Participants is shown by a Message Flow that connects two Pools (or the objects within the Pools). The Messages associated with the Message Flows can also be shown. 

<img alt="BPMN Activity" src="/assets/images/posts/bpmn-fundamentals/collaborative_process.png" width="100%"/>

### Conversation Diagram
A self-contained Choreography (no Pools or Orchestration) is a definition of the expected behavior, basically a procedural contract, between interacting Participants. While a normal Process exists within a Pool, a Choreography exists between Pools (or Participants).

<img alt="BPMN Activity" src="/assets/images/posts/bpmn-fundamentals/conversation.png" width="100%"/>

### Choreography Diagram
A self-contained Choreography is a definition of the expected behavior, basically a procedural contract, between interacting Participants. While a normal Process exists within a Pool, a Choreography exists between Pools (or Participants). The Choreography looks similar to a private Business Process since it consists of a network of Activities, Events, and Gateways. However, a Choreography is different in that the Activities are interactions that represent a set (1 or more) of Message exchanges, which involves two or more Participants. In addition, unlike a normal Process, there is no central controller, responsible entity or observer of the Process.

<img alt="BPMN Activity" src="/assets/images/posts/bpmn-fundamentals/choregraphy.png" width="100%"/>

## Summary
Congratulations! You have finished the post about BPMN Element Categories. Follow me on any of the different social media platforms and feel free to leave comments.

[1]:https://www.omg.org/spec/BPMN/2.0/PDF