---
title: "Group Call Pickup configuration prerequisites and user rights in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8757b1d3-751d-49c3-b1b8-b678f663f18e
description: "Group Call Pickup is a call management feature that is installed by default when you deploy Enterprise Voice. This topic describes what you need to have in place before you can configure Group Call Pickup and the user rights that you need to perform configuration tasks."
---

# Group Call Pickup configuration prerequisites and user rights in Lync Server 2013
[]
Group Call Pickup is a call management feature that is installed by default when you deploy Enterprise Voice. This topic describes what you need to have in place before you can configure Group Call Pickup and the user rights that you need to perform configuration tasks. 
  
This section assumes that you have read the planning documentation related to Group Call Pickup (see [Planning for Group Call Pickup in Lync Server 2013](planning-for-group-call-pickup.md)).
  
## Group Call Pickup Configuration Prerequisites

Group Call Pickup requires the following components:
  
- Application service
    
- Call Park application
    
These components are installed automatically when you deploy Enterprise Voice. 
  
## Group Call Pickup Configuration User Rights

You use the following administrative tools to configure Group Call Pickup:
  
- Lync Server Management Shell
    
- SEFAUtil resource kit tool
    
Use Lync Server Management Shell to create and manage call pickup groups in the Call Park orbit table. Use the SEFAUtil resource kit tool to assign a call pickup group and enable Group Call Pickup for users or to disable Group Call Pickup for users.
  
Configuring Group Call Pickup requires any of the following administrative roles, depending on the task:
  
- **CsVoiceAdministrator**: This administrator role can create, configure, and manage all voice-related settings and policies.
    
- **CsUserAdministrator**: This administrator role can enable Group Call Pickup for users. This administrator role also has read-only view access to all voice configurations.
    
- **CsServerAdministrator**: This administrator role can manage, monitor, and troubleshoot servers and services. 
    
- **CsAdministrator**: This administrator role can perform all of the tasks of CsVoiceAdministrator, CsServerAdministrator, and CsUserAdministrator.
    
> [!NOTE]
> For details about administrative rights, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation. 
  
## See also

#### 

[Deploying Enterprise Voice in Lync Server 2013](deploying-enterprise-voice.md)
#### 

[Planning for call management features in Lync Server 2013](planning-for-call-management-features.md)

