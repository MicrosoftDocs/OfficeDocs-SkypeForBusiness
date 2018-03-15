---
title: "Export voice routing test cases in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 489ac472-1a35-4755-b390-48f7cdf31e94
description: "Test cases provide a way for you to test voice routes in your organization: you define such things as the number to be dialed and the dial plan and voice policy to be employed, and Lync Server can then verify that that, given those conditions, the supplied number can successfully be routed to the PSTN network."
---

# Export voice routing test cases in Lync Server 2013
[]
Test cases provide a way for you to test voice routes in your organization: you define such things as the number to be dialed and the dial plan and voice policy to be employed, and Lync Server can then verify that that, given those conditions, the supplied number can successfully be routed to the PSTN network. 
  
Test cases, which can be created by using Lync Server Control Panel, are typically saved only on the server where the case was originally created and run. However, these test cases can be exported as XML files (with the .vtest extension) and then imported on other servers. This enables you to run the same tests on different computers located at different points in your topology.
  
### To export a voice routing test case

1. In Lync Server Control Panel, click **Voice Routing** and then click **Test Voice Routing**.
    
2. On the **Test Voice Routing** tab, select the test case (or test cases) to be exported. To select multiple test cases, click the first case to be exported, then hold down the Ctrl key and select the additional cases to be exported. 
    
3. Click **Action**, then click **Export test cases**.
    
4. In the **Save As** dialog box, select a folder to store the exported test cases and type a name for the resulting XML file in the **File name** box. Note that if you are exporting multiple tests cases all of these test cases will be saved to a single XML file. 
    
5. To save the test cases, click **Save**.
    
## See also

#### 

[Import voice routing test cases in Lync Server 2013](import-voice-routing-test-cases.md)

