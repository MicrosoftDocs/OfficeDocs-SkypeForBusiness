---
title: "Plan for the Response Group application in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 6cc333e7-4029-4372-86b2-016040c415fb
description: "Planning for response groups in Skype for Business Server Enterprise Voice, which enables you to set up call routing to groups of users. Includes audio file requirements."
---

# Plan for the Response Group application in Skype for Business Server

Planning for response groups in Skype for Business Server Enterprise Voice, which enables you to set up call routing to groups of users. Includes audio file requirements.

If your organization has groups of people who answer and manage certain types of calls, such as for customer service, an internal help desk, or general telephone support for a department, you can deploy the Response Group application to manage these types of calls. The Response Group application routes and queues incoming calls to designated persons, who are known as agents. You can increase the use of telephone support services and reduce the overhead of running these services by using response groups.

When a caller calls a response group, the call is routed to an agent based on a hunt group or the caller's answers to interactive voice response (IVR) questions. The Response Group application uses standard response group routing methods to route the call to the next available agent. Supported call routing methods include serial, longest-idle, parallel, round robin, and Attendant routing (that is, all agents are called at the same time for every incoming call, regardless of their current presence).

If no agents are available, the call is held in a queue until an agent is available. While in the queue, the caller hears music until an available agent accepts the call. If the queue is full, or if the call times out while in the queue, the caller might hear a message and then is either disconnected or transferred to a different destination, such as a different phone number or voicemail. When an agent accepts the call, the caller might or might not be able to see the agent's identity, depending on how the administrator configures the response group. Agents can either be formal, which means that they must sign in to the group before they can accept calls routed to the group, or informal, which means that they do not sign into and out of the group to accept calls.

> [!NOTE]
> Only on-premises users can be agents. If an agent is moved from on-premises to online, Response Group calls will not be routed to that agent.

> [!NOTE]
> The Response Group application uses an internal service, called Match Making, to queue calls and find available agents. Each computer that runs the Response Group application runs the Match Making service, but only one Match Making service per pool is active at a time--the others are passive. If the active Match Making service becomes unavailable during an unplanned outage, one of the passive Match Making services becomes active. The Response Group application does its best to make sure that call routing and queuing continues uninterrupted. However, when a Match Making service transition occurs, any calls that are in transfer at the time are lost. For example, if the transition is due to the Front End Server going down, any calls currently being handled by the active Match Making service on that Front End Server are also lost.

## Response group workflows

A workflow defines the behavior of a call from the time that the phone rings to the time that someone answers the call. The workflow specifies the queue to use for holding the call, and specifies the routing method to use for hunt groups or the questions and answers to use for interactive response groups. A workflow also defines settings such as a welcome message, music on hold, business hours, and holidays.

> [!NOTE]
> You must create agent groups and queues before you create a workflow that uses them.

## Management of response groups

In Skype for Business Server, two management roles are available for managing response groups: Response Group Manager and Response Group Administrator. Response Group Administrators can manage any aspect of any response group. Response Group Managers can manage only certain aspects, and only for the response groups that they own. The Manager role can help you reduce your administration costs, because you can delegate limited responsibilities for specific response groups to any user who is enabled for Enterprise Voice. Note that a user can be both a Response Group Manager and a Response Group Administrator.

To accommodate the Manager role, Response Group application uses a **Workflow Type** of Managed or Unmanaged. The following table describes Managed and Unmanaged response groups.

**Managed and Unmanaged Response Groups**

|**Response group type**|**Description**|
|:-----|:-----|
|Unmanaged  <br/> | Unmanaged response groups have no assigned Managers. Only the Response Group Administrator can configure these response groups. <br/>  Multiple unmanaged response groups can share a queue or agent group. <br/>  When you migrate response groups from a prior version to Skype for Business Server, the type is set to Unmanaged. <br/> |
|Managed  <br/> | Response Group Administrators can configure any aspect of managed response groups. <br/>  Response Group Managers cannot view or modify response groups that are not explicitly assigned to them. <br/>  Response Group Managers can configure only some settings for the response groups that are explicitly assigned to them. <br/>  Managed response groups can't share any queues or agent groups with any other response group, managed or unmanaged. <br/> |

The following table describes the actions that Response Group Managers can and cannot perform for the response groups assigned to them.

**Response Group Manager Capabilities**

|**Can configure:**|**Can create, delete, or configure:**|**Cannot:**|
|:-----|:-----|:-----|
| Agents <br/>  Welcome message <br/>  Response Group name <br/>  Description <br/>  Display number <br/>  Business hours <br/>  Music on hold <br/>  Status (active/inactive) <br/>  Hunt group workflows or Interactive voice response (IVR) workflows <br/> | Agent Groups <br/>  Queues <br/>  Holiday sets <br/> | Create or delete any type of workflow <br/>  Modify core response group settings, such as: **SIP URI**, **Telephone Number**, or **Workflow Type**.  <br/> |

Response Group Managers can use the following tools to manage their designated response groups.

- Skype for Business Server Control Panel

    > [!NOTE]
    > Response Group Managers can only manage Response Group settings with this tool. Other Skype for Business Server settings are not available to Managers.

- Response Group Configuration Tool

- Skype for Business Server Management Shell

Response Group scales well to departmental or workgroup environments (for details, see [Capacity Planning for Response Group](https://technet.microsoft.com/library/a2459a69-1f45-4f2f-bca5-d4f442708e44.aspx)) and can be deployed in entirely new telephony installations. It supports incoming calls from the Enterprise Voice deployment and from the local carrier network. Agents can use Skype for Business, Lync 2013, Lync 2010, Lync 2010 Attendant, or Lync Phone Edition to take the calls routed to them.

## Deployment and requirements

The Response Group application is automatically enabled when you deploy Enterprise Voice.

### Hardware and software requirements

The Response Group application has the same hardware requirements, operating system requirements and software prerequisites as Front End Servers.

If you use Windows Media Audio (.wma) files for Response Group music and announcements, all Front End Servers or Standard Editions servers that run the Response Group application must have the Windows Media Format Runtime installed for servers running Windows Server 2008 R2, or Microsoft Media Foundation for servers running Windows Server 2012 or Windows Server 2012 R2. For Windows Server 2008 R2, Windows Media Format Runtime is installed as part of Windows Desktop Experience.

Response Group uses **Language packs** to support text-to-speech and speech recognition. These speech technologies are used when you configure messages, such as the welcome message and other prompts, and interactive voice response (IVR) questions and answers. By default, the 26 supported language packs are installed when you deploy Skype for Business Server.

### Port Requirements

The Response Group application uses the following ports:

- **Port 5071**   for SIP listening requests

- **Port 8404**   for interserver communications

    > [!NOTE]
    > This port is used for the Match Making service and is required when the Response Group application is deployed in a pool that has more than one Front End Server.

   > [!NOTE]
   > These ports are default settings that you can change by using the **Set-CsApplicationServer** cmdlet. For details about this cmdlet, see the Skype for Business Server Management Shell documentation.

### Audio File Requirements

The Response Group application supports wave (.wav) file format and Windows Media audio (.wma) file format for Response Group messages, on-hold music, or interactive voice response (IVR) questions.

The Windows Media audio file format requires that the Windows Media Format Runtime is installed on Front End Servers running Windows Server 2008 R2 and Windows Server 2008. For more details, see "Software Requirements" earlier in this section.

#### Supported Wave File Formats

All wave files must meet the following requirements:

- 8-bit or 16-bit file

- Linear pulse code modulation (LPCM), A-Law, or mu-Law format

- Mono or stereo

- 4MB or less

For the best performance of wave files, a 16 kHz, mono, 16-bit Wave file is recommended.

#### Supported Windows Media Audio File Formats

If you use a Windows Media audio file, consider using low bit rates, and verify the performance of your system under load.

You can use the Microsoft Expression Encoder 4 to convert a file to the Windows Media Audio format. To download Expression Encoder 4, see [https://go.microsoft.com/fwlink/p/?linkId=202843](https://go.microsoft.com/fwlink/p/?linkId=202843).

### Response Group Configuration Tool Requirements

The Response Group Configuration Tool supports the combinations of operating systems and web browsers described in the following table.

> [!NOTE]
> 32-bit or 64-bit versions of the operating systems are supported. Only 32-bit versions of Internet Explorer are supported.

**Supported Operating Systems and Web Browsers**

|**Operating system**|**Web browser**|
|:-----|:-----|
|Windows Vista with Service Pack (SP) 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows 7  <br/> Windows 7 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2008 with Service Pack 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2008 R2  <br/> Windows Server 2008 R2 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2012  <br/> ||
|Windows Server 2012 R2  <br/> ||

### Response Group Agent Console

The agent console supports the combinations of operating systems and web browsers described in the following table.

> [!NOTE]
> 32-bit or 64-bit versions of the operating systems are supported. Only 32-bit versions of Internet Explorer are supported.

**Supported Operating Systems and Web Browsers**

|**Operating system**|**Web browser**|
|:-----|:-----|
|Windows Vista with Service Pack (SP) 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows 7  <br/> Windows 7 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> Firefox 10.0  <br/> Chrome 18.0  <br/> |
|Windows Server 2008 with Service Pack 2  <br/> |Internet Explorer 7  <br/> Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> |
|Windows Server 2008 R2  <br/> Windows Server 2008 R2 with Service Pack 1  <br/> |Internet Explorer 8 (native mode)  <br/> Internet Explorer 9 (native mode)  <br/> Firefox 10.0  <br/> Chrome 18.0  <br/> |
|Windows Server 2012  <br/> |
|Windows Server 2012 R2  <br/> |

## Client support

The Response Group application supports the following clients:

- Skype for Business desktop client

- Lync 2013 desktop client

- Lync 2010 desktop client

- Lync 2010 Attendant

- Office Communications Server 2007 R2 Attendant

- Lync Phone Edition

> [!NOTE]
> The Response Group application is not supported on Lync mobile clients.

The specific client that you can use depends on the type of Response Group user that you are:

- **Callers** can call a response group by using any of the clients listed previously, and by using a standard telephone over the public switched telephone network (PSTN).

- **Informal agents** (agents who do not sign into and out of their groups to accept calls) can accept calls by using Attendant, Lync, or Lync Phone Edition. Informal agents are automatically signed into their groups when they sign in to Skype for Business Server by using one of these clients.

- **Formal agents** (agents who must sign into and out of their groups to accept calls) can accept calls by using Skype for Business and accessing the agent console from the menu item, or by using Attendant and accessing the agent console directly from Internet Explorer.

## Capacity planning

The following table describes the Response Group user model that you can use as the basis for capacity planning requirements.

> [!NOTE]
> The numbers in the following table assume that you use 16 kHz, mono, 16-bit Wave (.wav) files for all response group audio files. If you use other file formats, such as Windows Media Audio (.wma), the numbers may vary.

> [!IMPORTANT]
> Keep in mind that for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for all the response groups in both pools.

**Response Group User Model**

|**Metric**|**Per Enterprise Edition pool  <br/> (With 8 Front End Servers)**|**Per Standard Edition server**|
|:-----|:-----|:-----|
|Incoming calls per second  <br/> |16  <br/> |2  <br/> |
|Concurrent calls connected to IVR or MoH  <br/> |480  <br/> |60  <br/> |
|Concurrent anonymous sessions (without IM)  <br/> |224  <br/> |28  <br/> |
|Concurrent anonymous sessions (with IM)  <br/> |64  <br/> |8  <br/> |
|Active agents (formal and informal)  <br/> |2400  <br/> |2400  <br/> |
|Number of hunt groups  <br/> |800  <br/> |800  <br/> |
|Number of IVR groups (use speech recognition)  <br/> |400  <br/> |400  <br/> |


