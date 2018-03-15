---
title: "Call Park configuration prerequisites and user rights in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 25b8cfe0-e4e7-487c-9e78-8c040f629059
description: "Call Park is a call management feature that is installed by default when you deploy Enterprise Voice. This topic describes what you need to have in place before you can configure Call Park and the user rights that you need to perform configuration tasks."
---

# Call Park configuration prerequisites and user rights in Lync Server 2013
[]
Call Park is a call management feature that is installed by default when you deploy Enterprise Voice. This topic describes what you need to have in place before you can configure Call Park and the user rights that you need to perform configuration tasks. 
  
> [!IMPORTANT]
> Customized music-on-hold files for the Call Park application are not backed up as part of the Lync Server 2013 disaster recovery process, and the files will be lost if the files uploaded to the pool are damaged, corrupted, or erased. Always keep a separate backup copy of the customized music-on-hold files that you have uploaded for Call Park. 
  
This section assumes that you have read the planning documentation related to Call Park (see [Planning for call management features in Lync Server 2013](planning-for-call-management-features.md)).
  
## Call Park Configuration Prerequisites

Call Park requires the following components:
  
- Application service
    
- Call Park application
    
These components are installed automatically when you deploy Enterprise Voice. 
  
If you want callers to hear music while the call is parked, a music-on-hold file is also required. A default music-on-hold file is installed automatically when you deploy Enterprise Voice. You can substitute the default file with your own music-on-hold file. Call Park uses File Store to hold the audio file.
  
## Call Park Configuration User Rights

You can use the following administrative tools to configure Call Park:
  
- Lync Server Control Panel
    
- Lync Server Management Shell
    
You use these tools to set up the Call Park orbit table and to configure other settings used by Call Park.
  
Configuring Call Park requires any of the following administrative roles, depending on the task:
  
- **CsVoiceAdministrator**: This administrator role can create, configure, and manage all voice-related settings and policies.
    
- **CsUserAdministrator**: This administrator role can enable Call Park in voice policy. This administrator role also has read-only view access to all voice configurations.
    
- **CsServerAdministrator**: This administrator role can manage, monitor, and troubleshoot servers and services. 
    
- **CsAdministrator**: This administrator role can perform all of the tasks of CsVoiceAdministrator, CsServerAdministrator, and CsUserAdministrator.
    
> [!NOTE]
> For details about administrative rights, see [Planning for role-based access control in Lync Server 2013](planning-for-role-based-access-control-rbac.md) in the Planning documentation. 
  
## See also

#### 

[Deploying Enterprise Voice in Lync Server 2013](deploying-enterprise-voice.md)
#### 

[Planning for call management features in Lync Server 2013](planning-for-call-management-features.md)

