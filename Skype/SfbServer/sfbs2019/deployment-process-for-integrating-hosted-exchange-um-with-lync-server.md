---
title: "Deployment process for integrating hosted Exchange UM with Lync Server 2013"
ms.author: tonysmit
author: tonysmit
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dbec9c38-7f66-419d-b8c3-c61380052cac
description: "Effective planning for integrating Lync Server 2013 with hosted Exchange Unified Messaging (UM) requires that you take into account the following:"
---

# Deployment process for integrating hosted Exchange UM with Lync Server 2013
[]
Effective planning for integrating Lync Server 2013 with hosted Exchange Unified Messaging (UM) requires that you take into account the following:
  
- Prerequisites for integrating Lync Server 2013 with hosted Exchange UM
    
- Steps required during the integration process
    
## Deployment Prerequisites for Integrating with Hosted Exchange UM

Before you can begin the integration process, you must already have deployed Lync Server 2013 (at a minimum, a Front End pool or a Standard Edition server), an Edge Server, and Lync 2013 or Lync 2010 clients.
  
## Integration Process

The following table provides an overview of the hosted Exchange UM integration process. For details about deployment steps, see [Providing Lync Server 2013 users voice mail on hosted Exchange UM](providing-lync-server-2013-users-voice-mail-on-hosted-exchange-um.md) in the Deployment documentation. 
  
|**Phase**|**Steps**|**Rights and permissions**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Configure the Edge Server.  <br/> |
Configure the Edge Server for federation. Manually replicate data to the Edge Server. Configure the hosting provider on the Edge Server. |RTCUniversalServerAdmins  <br/> |[Configure the Edge Server for integration with hosted Exchange UM](configure-the-edge-server-for-integration-with-hosted-exchange-um.md) <br/> |
|Configure hosted voice mail policy.  <br/> |
Either modify the global hosted voice mail policy or create a new hosted voice mail policy with Site or Per-User scope. For policies with Per-User scope, assign the policy to users or groups. |RTCUniversalServerAdmins  <br/> |[Manage hosted voice mail policies in Lync Server 2013](manage-hosted-voice-mail-policies.md) <br/> |
|Enable users for hosted voice mail.  <br/> | Configure user accounts for users whose mailboxes are on a hosted Exchange service.  <br/> |RTCUniversalUserAdmins  <br/> |[Enable users for hosted voice mail in Lync Server 2013](enable-users-for-hosted-voice-mail.md) <br/> |
|Configure hosted contact objects.  <br/> |
Create auto-attendant Contact objects for hosted Exchange UM. Create Subscriber Access contact objects for hosted Exchange UM. |RTCUniversalUserAdmins  <br/> 
> [!NOTE]
> To create, modify or remove contact objects, the user who runs the New-CsExUmContact, Set-CsExUmContact or Remove-CsExUmContact cmdlet must have the correct permission to the Active Directory organizational unit where the new contact objects are stored. This permission can be granted by running the Grant-CsOUPermission cmdlet. For details, see the Lync Server Management Shell documentation. 
  
|[Create contact objects for hosted Exchange UM in Lync Server 2013](create-contact-objects-for-hosted-exchange-um.md) <br/> |
   

