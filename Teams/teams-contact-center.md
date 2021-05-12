---
title: Teams Contact Center
author: cazawideh
ms.author: czawideh
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.reviewer: anblak
localization_priority: Normal
f1.keywords:
- NOCSH
description: An overview of the integrated contact center as a service (CCaaS) solution for Microsoft Teams
appliesto: 
  - Microsoft Teams
---




# Contact center integrations for Microsoft Teams

If you're a contact center solution provider or an organization with support call center environments like sales, customer service, or technical support, you can leverage Teams Calling capabilities and integrate your contact center solution with Microsoft Teams. This article provides an overview of how contact center solutions can be integrated with Microsoft Teams and the solution providers participating in the Microsoft Teams Connected Contact Center Certification Program.

## What is contact center integration for Microsoft Teams?

Today’s contact centers provide much more than support – they act as one of the main vehicles for interaction and unfiltered feedback on a customer’s experience with a brand. Due to the breadth of channels that today’s customers prefer to engage across – phone, email, text, social – and the expanded volume of touch points associated with present day purchase processes, many organizations have realized two additional realities:

1. Every member of the organization has the potential to be involved in engaging a customer directly and therefore needs to be equipped with the appropriate tools.

2. This expanded scope of customer interactions requires tools that can help drive consistency, constant improvement, and scale.

Microsoft Teams supports customer interaction work streams by acting as the hub for internal and external customer connection across its modes of communication including chat, video meetings and calling. For some companies, Microsoft Teams’ [cloud voice capabilities](./cloud-voice-landing-page.md), including [auto attendant](./what-are-phone-system-auto-attendants.md) and [call queues](./create-a-phone-system-call-queue.md), provide the features and configuration to meet their needs.

For others who desire integrated solutions with business tools and workflows to drive the customer journey, Microsoft Teams also integrates with some of the industry’s leading Contact Center as a Service (CCaaS) solution providers.

## Connected Contact Center for Microsoft Teams certification program

The Connected Contact Center for Microsoft Teams certification program provides customers with the assurance that each participating provider’s solution has been tested and verified to provide the quality, compatibility, and reliability they expect from Microsoft solutions.

For a list of solution certified providers as well as providers in the process of certification, see [Connected Contact Center solutions](#connected-contact-center-solutions).

If you are a vendor seeking to join the certification program, please email <Teamscategorypartner@microsoft.com>.

## Choose an integration model

There are three solution models to choose from to integrate your Connected Contact Center into Teams:

- If you want to use certified SBCs and Direct Routing to connect a contact center solution to Teams, see the [Connect model](#the-connect-model).

- If you want to use Azure bots and the Microsoft Graph Communication APIs to enable solution providers to create Teams apps, see the [Extend model](#the-extend-model).

- If you want to use a SDK that enables solution providers to imbed native Teams experiences in their App, see the [Power model](#the-power-model). Power solutions will be possible when the SDK is available, towards the end of 2021.

### Comparing connected contact center integration models

Review the table below for an overview of the integration models that Microsoft Teams supports.

<table>
<thead>
<tr class="header">
<th></th>
<th>Teams voice apps</th>
<th>Connect</th>
<th>Extend</th>
<th>Power</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Cloud service model</td>
<td>Azure</td>
<td>Solution Provider</td>
<td><p>Solution Provider +</p>
<p>Azure</p></td>
<td>Azure</td>
</tr>
<tr class="even">
<td>Who operates the solution?</td>
<td>Microsoft</td>
<td>Solution Provider</td>
<td>Solution Provider</td>
<td>Solution Provider</td>
</tr>
<tr class="odd">
<td>M365 Sign-in</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
</tr>
<tr class="even">
<td>Users with Teams calling?</td>
<td>Informal, SME</td>
<td>Informal, SME</td>
<td>Informal, SME, Formal</td>
<td>Informal, SME, Formal</td>
</tr>
<tr class="odd">
<td>IW/SME experience</td>
<td>Teams</td>
<td>Teams</td>
<td><p>Teams +</p>
<p>extensions</p></td>
<td><p>Teams +</p>
<p>extensions</p></td>
</tr>
<tr class="even">
<td>Service connectivity</td>
<td>Platform<br />
(Calling Plans +DR)</td>
<td>Direct routing</td>
<td>Platform<br />
(Calling Plans + DR)</td>
<td>Platform<br />
(Calling Plans + DR)</td>
</tr>
</tbody>
</table>


### The Connect model

This model connects CCaaS solution providers with Microsoft Teams phone system infrastructure, enabling enhanced routing, configuration, and system insights. 

Agents using solutions built on the Connect model can gather information & insights and if necessary transfer calls to subject matter experts directly, using the SME’s presence in Teams to ensure their availability.

Organizations can make sure calls route to the optimal agent by setting up automated virtual assistants and skill-based routing queues.

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, the focus areas include:

  - Office 365 authN for agents to allow agents to connect to their Microsoft tenant from their integrated CCaaS client 

  - Presence indication from Teams users 

  - Support transfers and group calls with Teams users 

  - Teams Graph APIs and Cloud Communication APIs for integration with Teams 

  - Able to support multi-tenant SIP trunking to support several customers on solution provider’s SBC.  

  - Solution Providers to use [<span class="underline">Microsoft certified session border controller (SBC)</span>](./direct-routing-border-controllers.md) 

### The Extend model

This model extends contact center personnel and agent experiences by integrating with the Teams client using the [Teams client platform](/microsoftteams/platform/overview), [Teams Graph APIs](/graph/api/resources/teams-api-overview?view=graph-rest-1.0) and [Cloud Communications API in Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-1.0) and uses the Teams phone system for all contact center calls and call control experiences. In this model, the contact center solution provider acts as a telephony carrier alongside Microsoft 365.

By using Connect and Extend-based solutions, agents can benefit from dynamic, contextual notes correlating data from multiple systems prior to starting an engagement and then avoid costly context switching by working natively within Teams for both internal collaboration and external communications.

Organizations can design workflows and advanced routing configurations down to the individual and measure the quality of their system and interactions.

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, it does highlight the main focus areas:

  - Teams Graph APIs and Cloud Communication APIs for integration with Teams 

  - Teams-based app for agent experiences 

  - Teams as the primary calling endpoint for the agents 

  - Teams client calling for all the call controls

  - Agent experience app should be able to work on Teams web and mobile client as well

  - Analytics, Workflow management, role-based experiences for Agents within the CCaaS app within Teams

  - Chat and collaboration experiences integrated with Teams clients 

  - Preserve performance and quality of Teams client experiences in all apps  

### The Power model

This model enables solution providers to create native Azure-based voice applications using the Teams calling infrastructure and client platform to deliver modern, intelligent solutions for collaborative customer and agent connection. The goal of Extend and Power is to stoke developer creativity and drive customer productivity.

By building directly on Azure, solution providers can rapidly deploy and provision their solution across all Teams regions and geographies, benefitting from our shared, global communications network while taking advantage of Azure’s storage, compute, analytics & cognitive services.

With the Extend and Power integration model,solution providers can provide contact center agents with omni-channel communication experiences while incorporating artificial intelligence to customize how and when participants - or other services - are engaged in a call applying the [Cloud Communications API in Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-1.0).

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, these highlight areas in addition to those provided by the Connect and Extend model.

  - Formal agent experiences natively enabled for omni-channel communication via Teams SDK 

  - Use Teams collaboration services for agent collaboration and customer interactions  

  - Rapid provisioning of cloud services, deploy anywhere 

  - Direct conversation control and interaction with users during Teams conversations 



## Connected Contact Center Solutions

### Certified solutions 

![Certified Badge.](media/English_Solution_Certified_Teams_badge_noBkgrd_GrayText_RGB_500px.png)

|  Solution Provider                                                                                                                               |  Solution website                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `8x8` | https://www.8x8.com/8/8x8-contact-center-for-microsoft-teams                                                    |
| `Anywhere365` | https://anywhere365.io/direct-routing-contact-center-for-microsoft-teams/                                      |
| `ComputerTalk` | https://www.computer-talk.com/product/enterprise-contact-center/ice-contact-center-for-teams         |
| `Content Guru` | https://www.contentguru.com/microsoft-teams-integration/    |
| `Enghouse Interactive` | http://www.enghouseteams.com/         |
| `NICE inContact` | https://www.niceincontact.com/microsoft-teams                                                            |

### Solutions currently in the certification process

|  Solution Provider                                                                                                                               |  Solution website                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Competella` | https://www.competella.com/microsoft-teams-skype-for-business                                  |
| `ContactCenter4All` | www.contactcenter4all.com |
| `Five9` | https://www.five9.com/products/application-integration/uc-integration                                                   |
| `FrontStage` | https://www.frontstage.cc                                                                                        |
| `Genesys` | https://www.genesys.com/microsoft                                                                                   |
| `Geomant` | https://www.geomant.com/buzzeasy-contact-centre-for-microsoft-teams                                          |
| `Landis Technologies` | https://landistechnologies.com/microsoft-teams-contact-center/                                          |
| `Luware` | https://luware.com/en/solutions/                                                                                       |
| `Mida Solutions` | https://www.midasolutions.com/c3-cloud-contact-center-for-teams/                                        |
| `novomind` | https://www.novomind.com/en/customer-service-software-call-center/microsoft-teams/                             |
| `talkdesk` | https://www.talkdesk.com/cloud-contact-center/integrations/microsoft-teams/                                  |
| `Tendfor` | https://www.tendfor.com/en/                                                                                     |

This list will be updated as more solution providers join and meet the certification criteria.

