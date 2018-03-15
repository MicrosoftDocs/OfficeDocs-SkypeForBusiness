---
title: "Publish pending changes to the voice routing configuration in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ff941d0b-fb4b-47d2-b866-6d990ac66b81
description: "After you make changes to any of the configuration settings in pages in the Voice Routing group, perform this procedure to review, publish, or cancel the pending changes."
---

# Publish pending changes to the voice routing configuration in Lync Server 2013
[]
After you make changes to any of the configuration settings in pages in the **Voice Routing** group, perform this procedure to review, publish, or cancel the pending changes. 
  
> [!IMPORTANT]
> Be sure that only one user at a time modifies the Voice Routing configuration settings. > All pending changes must be published at the same time by running the **Commit all** command. You cannot selectively publish pending changes. Before you publish pending changes, run the **Review uncommitted changes** command and cancel any configuration changes that you do not want to publish. > If you navigate away from the pages in the **Voice Routing** group before committing pending changes, all pending changes will be lost. However, you can export the current configuration (including any pending changes) to a voice configuration file, and then import and publish the updated configuration. For details, see [Export a voice route configuration file in Lync Server 2013](export-a-voice-route-configuration-file.md). 
  
### To review, publish, or cancel voice routing configuration changes

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing**.
    
4. Make the configuration changes you want to the settings on each page of the **Voice Routing** group. 
    
5. To review pending changes without publishing them, select **Review uncommitted changes** from the **Commit** menu. 
    
6. If you want to cancel any of the pending changes, do one of the following:
    
  - Select **Cancel all uncommitted changes** from the **Commit** menu. 
    
  - Navigate to the tab of the **Voice Routing** page that has pending changes you want to cancel, select the item with the pending changes, click **Commit**, and then click **Cancel selected changes**.
    
7. After you have reviewed all pending changes and canceled any that you do not want to publish, click **Commit**, and then click **Commit all**.
    
8. In the **Uncommitted Voice Configuration Settings** dialog box, which displays a list of all of the pending changes, click **OK**.
    
    When Lync Server Control Panel has committed the changes, the **Successfully published voice routing configuration** message appears. 
    

