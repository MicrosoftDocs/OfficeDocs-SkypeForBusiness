---
title: "Publish pending changes to the voice routing configuration in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: quickstart
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: ff941d0b-fb4b-47d2-b866-6d990ac66b81
description: "Summary: Learn how to review, publish, or cancel voice routing configuration changes in Skype for Business Server by using the Skype for Business Server Control Panel."
---

# Publish pending changes to the voice routing configuration in Skype for Business
 
**Summary:** Learn how to review, publish, or cancel voice routing configuration changes in Skype for Business Server by using the Skype for Business Server Control Panel.
  
After you make changes to any of the configuration settings in pages in the **Voice Routing** group, perform this procedure to review, publish, or cancel the pending changes.
  
> [!IMPORTANT]
> Be sure that only one user at a time modifies the Voice Routing configuration settings. 
  
> [!NOTE]
> All pending changes must be published at the same time by running the **Commit all** command. You cannot selectively publish pending changes. Before you publish pending changes, run the **Review uncommitted changes** command and cancel any configuration changes that you do not want to publish.
  
> [!NOTE]
> If you navigate away from the pages in the **Voice Routing** group before committing pending changes, all pending changes will be lost. However, you can export the current configuration (including any pending changes) to a voice configuration file, and then import and publish the updated configuration. For details, see [Export or import a voice route configuration file in Skype for Business](voice-route-configuration-import-export.md). 
  
### To review, publish, or cancel voice routing configuration changes

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the **CsVoiceAdministrator**, **CsServerAdministrator**, or **CsAdministrator** administrative role.
    
2. Open Skype for Business Server Control Panel.
    
3. In the left navigation bar, click **Voice Routing**.
    
4. Make the configuration changes you want to the settings on each page of the **Voice Routing** group.
    
5. To review pending changes without publishing them, select **Review uncommitted changes** from the **Commit** menu.
    
6. If you want to cancel any of the pending changes, do one of the following:
    
   - Select **Cancel all uncommitted changes** from the **Commit** menu.
    
   - Navigate to the tab of the **Voice Routing** page that has pending changes you want to cancel, select the item with the pending changes, click **Commit**, and then click **Cancel selected changes**.
    
7. After you have reviewed all pending changes and canceled any that you do not want to publish, click **Commit**, and then click **Commit all**.
    
8. In the **Uncommitted Voice Configuration Settings** dialog box, which displays a list of all of the pending changes, click **OK**. 
    
    When Skype for Business Server Control Panel has committed the changes, the **Successfully published voice routing configuration** message appears.
    

