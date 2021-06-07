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

 If you're a contact center solution provider or an organization with support call center environments like sales, customer service, or technical support, this article provides an overview of how contact center solutions can be integrated with Microsoft Teams and the solution providers participating in the Microsoft Teams Connected contact center certification program.

## What is contact center integration for Microsoft Teams?

Microsoft Teams supports customer interaction work streams by acting as the hub for internal and external customer connection across its modes of communication including chat, video meetings and calling. For some organizations, Microsoft Teams’ [cloud voice capabilities](./cloud-voice-landing-page.md), including [auto attendant](./what-are-phone-system-auto-attendants.md) and [call queues](./create-a-phone-system-call-queue.md), provide the features and configuration to meet their needs.

But with the breadth of channels that today’s customers prefer to engage across – phone, email, text, social – and the expanded volume of touch points associated with present day purchase processes, many organizations need a solution that equips every member of their organization with the appropriate tools to handle the expanded scope of customer interactions and drive consistency, improvement, and scale.

For organizations that want solutions with business tools and workflows to drive the customer journey, contact center integration for Microsoft Teams integrates Teams with leading Contact Center as a Service (CCaaS) solution providers.


## Connected contact center for Microsoft Teams certification program

The connected contact center for Microsoft Teams certification program provides customers with the assurance that each participating provider’s solution has been tested and verified to provide the quality, compatibility, and reliability they expect from Microsoft solutions.

If you're an organization looking for an integrated contact center solution, see [Connected Contact Center solutions](#connected-contact-center-solutions) for a list of solution certified providers as well as providers in the process of certification.

If you're a vendor seeking to join the certification program, please email <Teamscategorypartner@microsoft.com>.

<a name="steps"></a>

## Integration models for solution providers

As a contact center solution provider, there are three models to choose from to integrate your connected contact center solution into Teams:

- If you want to use certified SBCs and Direct Routing to connect a contact center solution to Teams, see the [Connect model](#tabs=connect).

- If you want to use Azure bots and the Microsoft Graph Communication APIs to enable solution providers to create Teams apps, see the [Extend model](#tabs=extend).

- If you want to use a SDK that enables solution providers to imbed native Teams experiences in their App, see the [Power model](#tabs=power). Power solutions will be possible when the SDK is available, towards the end of 2021.

### [The Connect model](#tab/connect)

The Connect model leverages Microsoft certified SBCs and Direct Routing to connect contact center solutions to Teams phone system infrastructure, enabling enhanced routing, configuration, and system insights.

Other benefits include the option to set up automated virtual assistants and skill-based routing queues that help agents gather information and connect customers with available subject matter experts.

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, the focus areas include:

  - Office 365 authN for agents to connect to their Microsoft tenant from their integrated CCaaS client 

  - See when agents are available with Teams

  - Transfers and group call support with Teams 

  - Teams Graph APIs and Cloud Communication APIs for integration with Teams 

  - Multi-tenant SIP trunking to support several customers on solution provider’s SBC.  

  - Solution providers to use [<span class="underline">Microsoft certified session border controller (SBC)</span>](./direct-routing-border-controllers.md) 


### [The Extend model](#tab/extend)

The Extend model uses Azure bots, and the Microsoft Graph Communication APIs to enable solution providers to create Teams apps for more integrated contact center experience in Teams.

This model integrates with the Teams client using the [Teams client platform](/microsoftteams/platform/overview), [Teams Graph APIs](/graph/api/resources/teams-api-overview?view=graph-rest-1.0) and [Cloud Communications API in Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-1.0). The Extend model also uses the Teams phone system for all contact center calls and call control experiences, and the contact center solution provider acts as a telephony carrier alongside Microsoft 365.

Agents can working within Teams for internal collaboration and external communication and can benefit from dynamic, contextual notes correlating data from multiple systems prior to starting an engagement and then avoid costly context switching.

Organizations can design workflows and advanced routing configurations down to the individual and measure the quality of their system and interactions.

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, it does highlight the main focus areas:

  - Teams Graph APIs and Cloud Communication APIs for integration with Teams 

  - Teams-based app for agent experiences 

  - Teams as the primary calling endpoint for the agents 

  - Teams client calling for all the call controls

  - Agent experience app for both Teams web and mobile client

  - Analytics, workflow management, role-based experiences for agents in the CCaaS app in Teams

  - Chat and collaboration experiences integrated with Teams clients 

  - Preserve performance and quality of Teams client experiences in all apps  

### [The Power model](#tab/power)

The Power model leverages a SDK enabling solution providers to imbed native Teams experiences in their App.

This model enables solution providers to create native Azure-based voice applications using the Teams calling infrastructure and client platform to deliver modern, intelligent solutions for collaborative customer and agent connection. The goal of Extend and Power is to stoke developer creativity and drive customer productivity.

By building directly on Azure, solution providers can rapidly deploy and provision their solution across all Teams regions and geographies, benefitting from our shared, global communications network while taking advantage of Azure’s storage, compute, analytics & cognitive services.

Solution providers can provide contact center agents with omni-channel communication experiences while incorporating artificial intelligence to customize how and when participants - or other services - are engaged in a call applying the [Cloud Communications API in Microsoft Graph](/graph/api/resources/communications-api-overview?view=graph-rest-1.0).

**Feature highlights:**

While the following is not a comprehensive list of feature capabilities for this model of integration, these highlight areas in addition to those provided by the Connect and Extend model.

  - Formal agent experiences natively enabled for omni-channel communication via Teams SDK 

  - Use Teams collaboration services for agent collaboration and customer interactions  

  - Rapid provisioning of cloud services, deploy anywhere 

  - Direct conversation control and interaction with users during Teams conversations 

>[!NOTE]
> The Power model will be available towards the end of 2021.

#  

### Compare connected contact center integration models

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
