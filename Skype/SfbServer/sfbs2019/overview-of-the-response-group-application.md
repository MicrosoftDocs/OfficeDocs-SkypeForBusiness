---
title: "Overview of the Response Group application in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6cc333e7-4029-4372-86b2-016040c415fb
description: "When a caller calls a response group, the call is routed to an agent based on a hunt group or the caller's answers to interactive voice response (IVR) questions. The Response Group application uses standard response group routing methods to route the call to the next available agent. Call routing methods include serial, longest-idle, parallel, round robin, and Attendant routing (that is, all agents are called at the same time for every incoming call, regardless of their current presence). If no agents are available, the call is held in a queue until an agent is available. While in the queue, the caller hears music until an available agent accepts the call. If the queue is full, or if the call times out while in the queue, the caller might hear a message and then is either disconnected or transferred to a different destination. When an agent accepts the call, the caller might or might not be able to see the agent's identity, depending on how the administrator configures the response group. Agents can either be formal, which means that they must sign in to the group before they can accept calls routed to the group, or informal, which means that they do not sign into and out of the group to accept calls."
---

# Overview of the Response Group application in Lync Server 2013
[]
When a caller calls a response group, the call is routed to an agent based on a hunt group or the caller's answers to interactive voice response (IVR) questions. The Response Group application uses standard response group routing methods to route the call to the next available agent. Call routing methods include serial, longest-idle, parallel, round robin, and Attendant routing (that is, all agents are called at the same time for every incoming call, regardless of their current presence). If no agents are available, the call is held in a queue until an agent is available. While in the queue, the caller hears music until an available agent accepts the call. If the queue is full, or if the call times out while in the queue, the caller might hear a message and then is either disconnected or transferred to a different destination. When an agent accepts the call, the caller might or might not be able to see the agent's identity, depending on how the administrator configures the response group. Agents can either be formal, which means that they must sign in to the group before they can accept calls routed to the group, or informal, which means that they do not sign into and out of the group to accept calls.
  
> [!NOTE]
> Only on-premises users can be agents. If an agent is moved from on-premises to online, Response Group calls will not be routed to that agent. 
  
> [!NOTE]
> The Response Group application uses an internal service, called Match Making, to queue calls and find available agents. Each computer that runs the Response Group application runs the Match Making service, but only one Match Making service per Lync Server pool is active at a time--the others are passive. If the active Match Making service becomes unavailable during an unplanned outage, one of the passive Match Making services becomes active. The Response Group application does its best to make sure that call routing and queuing continues uninterrupted. However, when a Match Making service transition occurs, any calls that are in transfer at the time are lost. For example, if the transition is due to the Front End Server going down, any calls currently being handled by the active Match Making service on that Front End Server are also lost. 
  
In Lync Server 2013, two management roles are available for managing response groups: Response Group Manager and Response Group Administrator. Response Group Administrators can manage any aspect of any response group. Response Group Managers can manage only certain aspects, and only for the response groups that they own. The new Manager role can help reduce administration costs, because you can delegate limited responsibilities for specific response groups to any user who is enabled for Enterprise Voice. 
  
To accommodate the new Manager role, Lync Server 2013 Response Group application introduces a **Workflow Type** of Managed or Unmanaged. The following table describes Managed and Unmanaged response groups. 
  
**Managed and Unmanaged Response Groups**

|**Response group type**|**Description**|
|:-----|:-----|
|Unmanaged  <br/> | Unmanaged response groups have no assigned Managers. Only the Response Group Administrator can configure these response groups.  <br/>  Multiple unmanaged response groups can share a queue or agent group.  <br/>  When you migrate response groups from a prior version to Lync Server 2013, the type is set to Unmanaged.  <br/> |
|Managed  <br/> | Response Group Administrators can configure any aspect of managed response groups.  <br/>  Response Group Managers cannot view or modify response groups that are not explicitly assigned to them.  <br/>  Response Group Managers can configure only some settings for the response groups that are explicitly assigned to them.  <br/>  Managed response groups can't share any queues or agent groups with any other response group, managed or unmanaged.  <br/> |
   
The following table describes the actions that Response Group Managers can and cannot perform for the response groups assigned to them.
  
**Response Group Manager Capabilities**

|**Can configure:**|**Can create, delete, or configure:**|**Cannot:**|
|:-----|:-----|:-----|
| Agents  <br/>  Welcome message  <br/>  Response Group name  <br/>  Description  <br/>  Display number  <br/>  Business hours  <br/>  Music on hold  <br/>  Status (active/inactive)  <br/>  Hunt group workflows or Interactive voice response (IVR) workflows  <br/> | Agent Groups  <br/>  Queues  <br/>  Holiday sets  <br/> | Create or delete any type of workflow  <br/>  Modify core response group settings, such as: **SIP URI**, **Telephone Number**, or **Workflow Type**.  <br/> |
   
Response Group Managers can use the following tools to manage their designated response groups. 
  
- Lync Server Control Panel
    
    > [!NOTE]
    > Response Group Managers can only manage Response Group settings with this tool. Other Lync Server settings are not available to Managers. 
  
- Response Group Configuration Tool
    
- Lync Server Management Shell
    
Response Group scales well to departmental or workgroup environments (for details, see [Capacity planning for Response Group in Lync Server 2013](capacity-planning-for-response-group.md)) and can be deployed in entirely new telephony installations. It supports incoming calls from the Enterprise Voice deployment and from the local carrier network. Agents can use Lync 2013, Lync 2010, Lync 2010 Attendant, or Lync Phone Edition to take the calls routed to them.
  
The Response Group application is a component of Enterprise Voice. When you deploy Enterprise Voice, the Response Group application is installed and activated automatically.
  

