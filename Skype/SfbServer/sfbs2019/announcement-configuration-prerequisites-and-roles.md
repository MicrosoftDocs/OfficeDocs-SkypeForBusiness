---
title: "Announcement configuration prerequisites and roles in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 82f2dfe9-4c5e-4d65-96a1-96495d506ea4
description: "Announcement is an Enterprise Voice call management feature. This topic describes what you need to have in place before you can configure Announcement and the role assignments that you need to perform configuration tasks."
---

# Announcement configuration prerequisites and roles in Lync Server 2013
[]
Announcement is an Enterprise Voice call management feature. This topic describes what you need to have in place before you can configure Announcement and the role assignments that you need to perform configuration tasks. 
  
This section assumes that you have read the planning documentation related to Announcement (see [Planning for call management features in Lync Server 2013](planning-for-call-management-features.md)).
  
## Announcement Configuration Prerequisites

The Announcement application requires the following components:
  
- Application service
    
- Response Group application
    
- File Store, to hold audio files
    
All of these components are installed by default when you deploy Enterprise Voice.
  
## Announcement Configuration Roles

You can use the following administrative tools to configure announcements:
  
- Lync Server Control Panel
    
- Lync Server Management Shell
    
Configuring Announcement application requires one of the following administrative roles:
  
- **CsVoiceAdministrator** This administrator role can create, configure, and manage all voice-related settings and policies, including Announcement settings. 
    
- **CsServerAdministrator** This administrator role can manage, monitor, and troubleshoot servers and services, and configure all Announcement settings. 
    
- **CsAdministrator** This administrator role can perform all administrative tasks and modify all settings. 
    
- **CsViewOnlyAdministrator** This administrator role can view the deployment to monitor deployment health. 
    
> [!NOTE]
> For details about administrative user rights, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation. 
  
## See also

#### 

[Deploying Enterprise Voice in Lync Server 2013](deploying-enterprise-voice.md)
#### 

[Planning for call management features in Lync Server 2013](planning-for-call-management-features.md)

