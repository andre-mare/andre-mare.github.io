---
layout: post
title: "Camunda Tutorials, Guides & Examples"
author: andre
categories: [ camunda ]
tags: [camunda, rest-engine, api]
image: /assets/images/feature-images/feature-image-camunda.png
description: This page serves as the landing page for all topics related about Camunda. The page contains links to tutorials, guides and important links about Camunda and BPMN across the World Wide Web.
comments: true
related_posts:
  - camunda/_posts/2020-07-15-how-to-create-a-camunda-bpm-spring-boot-application.md
  - camunda/_posts/2020-07-25-how-to-model-a-simple-bpmn-flow-using-camunda-modeler.md
---

- Table of Contents
{:toc .large-only}

### What is Camunda?
> “Camunda BPM is an open-source workflow and decision automation platform. Camunda BPM ships with tools for creating workflow and decision models, operating deployed models in production, and allowing users to execute workflow tasks assigned to them.” ~ [Wikipedia][1]

---
### Install Camunda
There are a number of ways that you can install the Camunda Modeller and the Camunda BPMN platform on your local machine. 
* [How to Install Camunda Modeler on macOS using Homebrew][Install_Camunda_Modeler]
* [Docker commands for Camunda BPM Platform][Docker_Commands]

---
### Camunda Modeler: BPMN & DMN 
The Camunda Modeller is an application used to model BPMN processes and DMN decisions. The following articles explain how to use the Camunda Modeller to model processes and DMN.  
* [Camunda Modeler Plugins][camunda_modeler_plugin]
* [How to Model a Simple BPMN Flow using Camunda Modeler][bpmn_flow_user_task]

---
### Camunda Tutorials with Spring Boot
Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can just run. It is possible to run the Camunda BPM Platform within a Spring Boot Application.
* [How to create a spring boot application containing the Camunda BPM Engine][camunda_spring_boot]

**BPMN Tasks**
* [Implement a BPMN Service Task in Camunda][camunda_service_task]
* [Implement a BPMN Manual Task in Camunda][camunda_manual_task]

**BPMN Gateways**
* [Implement a BPMN Exclusive Gateway in Camunda][camunda_exclusive_gateway]
* [Implement a BPMN Parallel Gateway in Camunda][camunda_parallel_gateway]
* [Implement a BPMN Inclusive Gateway in Camunda][camunda_inclusive_gateway]
* [Implement a BPMN Event-based Gateway in Camunda][camunda_event_based_gateway]

**BPMN Events**
* [Implement a BPMN Timer Event in Camunda][camunda_timer_event]



---
### Camunda REST Interfaces
Camunda BPM provides a REST API to allow other applications to communicate with it and perform a number of functions.

**Admin Functions**
* [How the use the User REST Interface of the Camunda Platform][rest_user]
* [How the use the Group REST Interface of the Camunda Platform][rest_group]
* [How the use the Tenant REST Interface of the Camunda Platform][rest_tenant]

---
### Official Specifications
Business Process Model and Notation has become the de-facto standard for business processes diagrams.
* BPMN 2.0 Specification: [https://www.omg.org/spec/BPMN](https://www.omg.org/spec/BPMN)
* CMNN 1.1 Specification: [https://www.omg.org/spec/CMMN](https://www.omg.org/spec/CMMN)
* DMN 1.3 Specification: [https://www.omg.org/spec/DMN](https://www.omg.org/spec/DMN)

---
### Camunda Important Links
There are many important and interesting information about Camunda. Here are some of the links: 
* Camunda BPM Documentation (Latest): [https://docs.camunda.org/manual/latest/](https://docs.camunda.org/manual/latest/)
* Camunda Whitepapers: [https://camunda.com/learn/whitepapers/](https://camunda.com/learn/whitepapers/)
* Camunda Forum: [https://forum.camunda.org/](https://forum.camunda.org/)
* Camunda Webinars: [https://camunda.com/learn/webinars/](https://camunda.com/learn/webinars/)
* Camunda Blog: [https://blog.camunda.com/](https://blog.camunda.com/)
* Camunda Events: [https://camunda.com/events/](https://camunda.com/events/)
* Camunda Source Code: [https://github.com/camunda](https://github.com/camunda)

**Posters & Cheat Sheet**
* BPMN 2.0 Poster: [http://www.bpmb.de/images/BPMN2_0_Poster_EN.pdf](http://www.bpmb.de/images/BPMN2_0_Poster_EN.pdf)

---
### Camunda Examples
There are many official Camunda examples that can help you learn the Camunda Platform.

**Camunda Invoice Example**
This is the invoice demo application which is shipped with the full distributions.
* Invoice Example: [https://github.com/camunda](https://github.com/camunda/camunda-bpm-platform/tree/master/examples/invoice)
* BPMN Invoice V1: [invoice.v1.bpmn](https://github.com/camunda/camunda-bpm-platform/blob/master/examples/invoice/src/main/resources/invoice.v1.bpmn) 
* BPMN Invoice V2: [invoice.v1.bpmn](https://github.com/camunda/camunda-bpm-platform/blob/master/examples/invoice/src/main/resources/invoice.v2.bpmn)
* BPMN Review Invoice: [reviewInvoice.bpmn](https://github.com/camunda/camunda-bpm-platform/blob/master/examples/invoice/src/main/resources/reviewInvoice.bpmn)
* DMN Business Decision: [invoiceBusinessDecisions.dmn](https://github.com/camunda/camunda-bpm-platform/blob/master/examples/invoice/src/main/resources/invoiceBusinessDecisions.dmn)

**Camunda Other Examples**
* Camunda BPM Examples: [github.com/camunda/camunda-bpm-examples](https://github.com/camunda/camunda-bpm-examples)

[1]:https://en.wikipedia.org/wiki/Camunda

[Install_Camunda_Modeler]:/how-to-install-camunda-modeler-on-macos-using-homebrew
[Docker_Commands]:/docker-commands-camunda-bpm-platform

[camunda_modeler_plugin]:/plugins-for-camunda-modeler/
[bpmn_flow_user_task]:/how-to-model-a-simple-bpmn-flow-using-camunda-modeler/

[rest_user]:/using-the-user-rest-interface-of-the-camunda-platform/
[rest_group]:/using-the-group-rest-interface-of-the-camunda-platform/
[rest_tenant]:/using-the-tenant-rest-interface-of-the-camunda-platform/

[camunda_spring_boot]:/how-to-create-a-camunda-bpm-spring-boot-application/
[camunda_exclusive_gateway]:/implement-bpmn-exclusive-gateway-in-camunda/
[camunda_parallel_gateway]:/implement-bpmn-parallel-gateway-in-camunda/
[camunda_inclusive_gateway]:/implement-bpmn-inclusive-gateway-in-camunda/
[camunda_event_based_gateway]:/implement-bpmn-event-based-gateway-in-camunda/
[camunda_manual_task]:/implement-bpmn-manual-task-in-camunda/
[camunda_service_task]:/implement-bpmn-service-task-in-camunda/