---
title: Teams Contact Center
author: microsoftheidi
ms.author: heidip
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




# Contact Center integrations for Microsoft Teams

Integrating popular contact center solutions with Microsoft Teams is a common need for customers deploying Teams Calling capabilities.  This article provides an overview of how contact center solutions can be integrated with Microsoft Teams and additional information on the partner solutions participating in the Microsoft Teams Connected Contact Center Certification Program.

## What is a Contact Center integration for Microsoft Teams?

Today’s contact centers provide much more than support – they act as one of the main vehicles for interaction and unfiltered feedback on a customer’s experience with a brand. Due to the breadth of channels that today’s customers prefer to engage across – phone, email, text, social – and the expanded volume of touch points associated with present day purchase processes, many organizations have realized two additional realities:

1. Every member of the organization has the potential to be involved in engaging a customer directly and therefore needs to be equipped with the appropriate tools.

2. This expanded scope of customer interactions requires tools that can help drive consistency, constant improvement, and scale.

Microsoft Teams supports customer interaction work streams by acting as the hub for internal and external customer connection across its modes of communication including chat, video meetings and calling. For some companies, Microsoft Teams’ [cloud voice capabilities](https://docs.microsoft.com/microsoftteams/cloud-voice-landing-page), including [auto attendant](https://docs.microsoft.com/microsoftteams/what-are-phone-system-auto-attendants) and [call queues](https://docs.microsoft.com/microsoftteams/create-a-phone-system-call-queue), provide the features and configuration to meet their needs.

For others who desire integrated solutions with business tools and workflows to drive the customer journey, Microsoft Teams also integrates with some of the industry’s leading Contact Center as a Service (CCaaS) solution providers.

## Connected Contact Center for Microsoft Teams Certification Program

The APIs allow partners to develop and integrate CCaaS solutions for Teams. In addition, we have developed the Connected Contact Center for Microsoft Teams Certification Program to provide customers with the assurance that each participating partner’s solution has been tested and verified to provide the quality, compatibility and reliability they expect from Microsoft solutions.

The following partners are in the process of certifying their solution for Microsoft Teams and are ready to engage customers:

| **Partner**                                                                                                                              | **Solution website**                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Anywhere365 | https://anywhere365.io/direct-routing-contact-center-for-microsoft-teams/                                      |
| Competella | https://www.competella.com/microsoft-teams-skype-for-business                                  |
| ComputerTalk | https://www.computer-talk.com/product/enterprise-contact-center/ice-contact-center-for-teams         |
| ContactCenter4All | www.contactcenter4all.com. |
| Enghouse Interactive | http://www.enghouseteams.com/                                                       |
| Five9 | https://www.five9.com/products/application-integration/uc-integration                                                   |
| Genesys | https://www.genesys.com/microsoft                                                                                   |
| Landis Technologies | https://landistechnologies.com/microsoft-teams-contact-center/                                          |
| Luware | https://luware.com/en/solutions/                                                                                       |
| NICE inContact | https://www.niceincontact.com/microsoft-teams                                                            |
| Tendfor | https://www.tendfor.com/en/                                                                                     |

This list will be updated as more partners join and meet the certification criteria.

## How do contact center solutions work in Microsoft Teams?

Microsoft Teams offers a range of capabilities to support the development of third-party voice solutions, including:

1. [Direct Routing Connectivity](https://docs.microsoft.com/MicrosoftTeams/direct-routing-landing-page)

2. [Microsoft Graph Cloud Communication APIs](https://docs.microsoft.com/graph/cloud-communications-get-started)

3. Teams platform and extensibility

4. Teams SDKs

Together, these capabilities enable 3 models of integration:

  - **Connect** (via Direct Routing)

  - **Connect and Extend** (Direct Routing, Graph APIs and Teams apps platform)

  - **Extend and Power** (embedding Teams SDKs into 3p Apps for native Teams interactions)

### Connect

This model connects CCaaS partners with Microsoft Teams phone system infrastructure, enabling enhanced routing, configuration and system insights. In this model, the contact center partner solution can also provide telephony services for selected numbers and users.

Agents using solutions built on the Connect model can gather information & insights and if necessary transfer calls to subject matter experts directly, leveraging the SME’s presence in Teams to ensure their availability.

Organizations can make sure calls route to the optimal agent by setting up automated virtual assistants and skill-based routing queues.

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, the focus areas include:

  - Office 365 authN for agents to allow agents to connect to their Microsoft tenant from their integrated CCaaS client 

  - Presence indication from Teams users 

  - Call flows via Direct Routing (as indicated in test plans) 

  - Support transfers and group calls with Teams users 

  - Teams Graph APIs and Cloud Communication APIs for integration with Teams 

  - Able to support multi-tenant SIP trunking to support several customers on partner’s SBC.  

  - Partners to implement [<span class="underline">Microsoft certified session border controller (SBC)</span>](https://docs.microsoft.com/MicrosoftTeams/direct-routing-border-controllers) 

### Connect and extend

This model extends contact center personnel and agent experiences by integrating with the Teams client using the [Teams client platform](https://docs.microsoft.com/microsoftteams/platform/overview), [Teams Graph APIs](https://docs.microsoft.com/graph/api/resources/teams-api-overview?view=graph-rest-1.0) and [Cloud Communications API in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/communications-api-overview?view=graph-rest-1.0) and uses the Teams phone system for all contact center calls and call control experiences. In this model, the contact center partner acts as a telephony carrier alongside Microsoft 365.

Leveraging Connect and Extend-based solutions, agents can benefit from dynamic, contextual notes correlating data from multiple systems prior to starting an engagement and then avoid costly context switching by working natively within Teams for both internal collaboration and external communications.

Organizations can design workflows and advanced routing configurations down to the individual and measure the quality of their system and interactions.

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, it does highlight the main focus areas:

  - Teams Graph APIs and Cloud Communication APIs for integration with Teams 

  - Teams based app for agent experiences 

  - Teams as the primary calling endpoint for the agents 

  - Teams client calling for all the call controls

  - Agent experience app should be able to work on Teams web and mobile client as well

  - Analytics, Workflow management, role-based experiences for Agents within the CCaaS app within Teams

  - Chat and collaboration experiences integrated with Teams clients 

  - Preserve performance and quality of Teams client experiences in all apps  

### Extend and power

This model enables partners to create native Azure-based voice applications leveraging the Teams calling infrastructure and client platform to deliver modern, intelligent solutions for collaborative customer and agent connection. The goal of Extend and Power is to stoke developer creativity and drive customer productivity.

By building directly on Azure, partners can rapidly deploy and provision their solution across all Teams regions and geographies, benefitting from our shared, global communications network while taking advantage of Azure’s storage, compute, analytics & cognitive services.

With the Extend and Power integration model, partners can provide contact center agents with omni-channel communication experiences while incorporating artificial intelligence to customize how and when participants - or other services - are engaged in a call leveraging the [Cloud Communications API in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/communications-api-overview?view=graph-rest-1.0).

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, these highlight areas in addition to those provided by the Connect and Extend model.

  - Formal agent experiences natively enabled for omni-channel communication via Teams SDK 

  - Leverage Teams collaboration services for agent collaboration and customer interactions  

  - Rapid provisioning of cloud services, deploy anywhere 

  - Direct conversation control and interaction with users during Teams conversations 

### Comparing connected contact center integration models

Please review the table below for an overview of the integration models that Microsoft Teams supports.

<table>
<thead>
<tr class="header">
<th></th>
<th><strong>Teams voice apps</strong></th>
<th><strong>Connect</strong></th>
<th><strong>Connect + extend</strong></th>
<th><strong>Extend + power</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Cloud service model</td>
<td>Azure</td>
<td>Partner</td>
<td><p>Partner +</p>
<p>Azure</p></td>
<td>Azure</td>
</tr>
<tr class="even">
<td>Who operates the solution?</td>
<td>Microsoft</td>
<td>Partner</td>
<td>Partner</td>
<td>Partner</td>
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
<td>Direct routing</td>
<td>Platform<br />
(Calling Plans + DR)</td>
</tr>
</tbody>
</table>

## Next steps

If you are a vendor seeking to join the certification program, please email <Teamscategorypartner@microsoft.com>.
