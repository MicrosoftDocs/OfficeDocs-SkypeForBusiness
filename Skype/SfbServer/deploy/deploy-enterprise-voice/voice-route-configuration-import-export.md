---
title: "Export or import a voice route configuration file in Skype for Business"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: 02ce922d-9ca8-4513-b09f-9de51f5c5bdc
description: "Summary: Learn how to export or import a voice routing configuration file in Skype for Business Server by using the Skype for Business Server Control Panel."
---

# Export or import a voice route configuration file in Skype for Business
 
**Summary:** Learn how to export or import a voice routing configuration file in Skype for Business Server by using the Skype for Business Server Control Panel.
  
If you want to save your voice routing configuration without publishing it, follow these steps to save and retrieve a snapshot of your voice routing configuration. 
  
When you import a voice routing configuration file (.vcfg), but changes have been made to the voice routing configuration on the server in the meantime, the pages in the **Voice Routing** group in Skype for Business Server Control Panel will indicate that there are uncommitted changes to voice routing. Those uncommitted changes are the differences between the two configurations that require reconciliation.
  
If you have made any uncommitted changes to the settings on any page within the group, the changes are saved in the exported voice configuration file (.vcfg). This enables you to make voice routing configuration changes during multiple sessions before you publish the changes. 
  
### To export a voice routing configuration

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Voice Routing**.
    
4. On the **Actions** menu, click **Export configuration**.
    
5. Specify a location and file name, and then click **Save**.
    
### To import a voice routing configuration

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Voice Routing**.
    
4. On the **Actions** menu, click **Import configuration**.
    
5. Find the configuration file you want to import and then click **Open**.
    
6. Click **Commit**, and then click **Commit all**.
    
    > [!NOTE]
    > Whenever you import a voice configuration file, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Skype for Business](voice-route-config-changes.md) in the Operations documentation.
  

