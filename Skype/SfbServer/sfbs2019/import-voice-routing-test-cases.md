---
title: "Import voice routing test cases in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6546e24c-9ad2-428b-92b2-63948ed0f884
description: "Test cases provide a way for you to test voice routes in your organization: you define such things as the number to be dialed and the dial plan and voice policy to be employed, and Lync Server 2013 can then verify that that, given those conditions, the supplied number can successfully be routed to the PSTN network."
---

# Import voice routing test cases in Lync Server 2013
[]
Test cases provide a way for you to test voice routes in your organization: you define such things as the number to be dialed and the dial plan and voice policy to be employed, and Lync Server 2013 can then verify that that, given those conditions, the supplied number can successfully be routed to the PSTN network. 
  
Test cases, which can be created by using Lync Server Control Panel, are typically saved only on the server where the case was originally created and run. However, these test cases can be exported as XML files (with the .vtest extension) and then imported on other servers. This enables you to run the same tests on different computers located at different points in your topology.
  
### To import a voice routing test case

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing**.
    
4. On the **Actions** menu, click **Import test cases**.
    
5. Find the test case file (.vtest) that you want to import, and then click **Open**.
    
6. Click **Commit**, and then click **Commit all**. 
    
    > [!NOTE]
    > Whenever you import a .vtest file, you must run the **Commit all** command to publish the test case. For details, see [Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md) in the Operations documentation. 
  
## See also

#### 

[Export voice routing test cases in Lync Server 2013](export-voice-routing-test-cases.md)

