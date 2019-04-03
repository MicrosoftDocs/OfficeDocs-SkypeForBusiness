---
title: "Deployment overview for Skype Room System"
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 99443d60-e64a-4a8a-a7bf-95f790b0ad5c
ms.collection: M365-voice
description: "Read about how do deploy Skype Room System, a meeting room solution consisting of integrated hardware and software that is optimized to join Skype for Business meetings."
---

# Deployment planning for Skype Room System in Skype for Business
 
Read about how do deploy Skype Room System, a meeting room solution consisting of integrated hardware and software that is optimized to join Skype for Business meetings.
  
> [!NOTE]
> For the purposes of this content, Skype for Business for SMART Room System, Crestron RL, and Polycom CX8000 will be referred to as Skype Room System. 

> [!NOTE]
> Microsoft Teams Rooms is a different product with different dependencies and deployment procedures. For information on Microsoft Teams Rooms, see [Plan Microsoft Teams Rooms](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md).
  
 Skype Room System is a Skype for Business unified communications client that has been optimized for Skype for Business meetings in physical conference rooms.
  
The Skype Room System client was developed from the Skype for Business client by using the Skype for Business SDK. The Skype for Business client runs in the background in partial UI suppressed mode. The Skype for Business client controls the video gallery and content stage on the screen at the front of the room. The Skype Room System client provides a console experience on the tabletop display for controlling the meetings. Skype Room System provides: 
  
- A one-touch meeting join experience
    
- Automatic setup of multi-view video gallery 
    
- Touch-enabled white boarding on the screen at the front of the room 
    
- Calendar integration for access to scheduled meetings
    
- Content sharing and switching 
    
This document guides you through provisioning Skype Room System in Skype for Business Server and Exchange Server. See also the Skype Room System Installation Guide provided by your administrator, which guides you through setting up the appliance PC and devices in the meeting room. 
  
## Prerequisites

Following are the requirements for Skype Room System: 
  
- An Exchange resource mailbox account to facilitate calendar scheduling for the meeting rooms with AutoDiscover service enabled on Exchange Server (2013 preferred).
    
- A Skype for Business-enabled Skype Room System account on a Skype for Business Server pool (Enterprise or Standard Edition).
    
- A Skype Room System client appliance PC with all required software installed. The appliance PC must be running Windows 7 Embedded Standard operating system. This hardware is provided by OEM partners along with all devices (displays, camera, microphone, speakers).
    
- If you decide to join the Skype Room System appliance PC to an Active Directory Domain Services (AD DS) domain, you must specify group policy settings that do not interfere with Skype Room System. Alternatively, you can leave this appliance PC in the Workgroup. 
    
- Appropriate user rights to run the cmdlets specified in this document. The CsMeetingRoom cmdlets are modeled after the CsUser cmdlet. Therefore, all role-based access control (RBAC) roles required to run CsUser cmdlets also apply to CsMeetingRoom cmdlets. 
    
## Supported topologies

The following table indicates Skype Room System client interoperability among various deployments of Skype for Business and Exchange topologies, either on premises or in the cloud: 
  

|**Topology**|**AD**|**Skype for Business**|**Exchange**|
|:-----|:-----|:-----|:-----|
|On premises  <br/> |On premises  <br/> |On premises  <br/> |On premises  <br/> |
|Office 365 Multi-tenant (O365MT)  <br/> |Online  <br/> |Online  <br/> |Online  <br/> |
|Office 365 Dedicated  <br/> (Contact your service provider)  <br/> |On premises  <br/> |Online  <br/> |Online  <br/> |
|Hybrid (Split domain)  <br/> Unsupported  <br/> |On premises  <br/> On premises  <br/> On premises  <br/> |On premises  <br/> Online  <br/> Online  <br/> |Online  <br/> Online  <br/> On premises  <br/> |
   
Releases prior to Lync Server 2013 are partially supported. In these scenarios, Skype Room System can participate in Skype for Business conferences (those that are scheduled by users homed on Lync Server 2010) as long as the conferences are "public," meaning the conferences aren't customized for restricted access. 
  
Skype Room System cannot be homed on a Lync server version earlier than Lync Server 2013. When a Skype Room System cannot connect to Exchange to retrieve calendar settings--for example, when there is no Exchange mailbox configured for the Skype Room System account or Exchange cannot be accessed--Meet Now and ad hoc conferencing will work, but joining a scheduled meeting will not. 
  
The following table indicates Skype Room System client supportability with versions of Exchange Server: 
  

|**Exchange**|**On premises**|**Online**|**Hybrid**|
|:-----|:-----|:-----|:-----|
|Exchange 2010  <br/> |Yes (single forest only)  <br/> |N/A  <br/> |N/A  <br/> |
|Exchange 2013  <br/> |Yes (multi forest support available for Exchange 2013 CU6 and later versions)  <br/> |Yes  <br/> |Yes  <br/> |
|Exchange 2016  <br/> |Yes (multi forest support available)  <br/> |Yes  <br/> |Yes  <br/> |
   

