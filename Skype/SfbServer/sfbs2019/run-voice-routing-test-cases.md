---
title: "Run voice routing test cases in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fb4d32df-b9ea-4944-8cd7-a6102c78c465
description: "You can run all of the test cases in your voice routing test case suite, or you can run one or more selected test cases."
---

# Run voice routing test cases in Lync Server 2013
[]
You can run all of the test cases in your voice routing test case suite, or you can run one or more selected test cases.
  
### To run all voice routing test cases

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing** and then click **Test Voice Routing**.
    
4. On the **Test Voice Routing** page, click **Action** and then click **Run all**.
    
    The pass or fail status of each test case is shown in the **Pass/fail** column. If a test case has not yet been run, N/A is shown in the **Pass/fail** column. 
    
5. (Optional) To see detailed results for each test case, double-click the test case name. Results are shown in the shaded area on the right side of the **Edit Test Case** page: 
    
1. **Test result**: Overall pass or fail status of the test case run.
    
2. **Normalization rule**: The first normalization rule in the dial plan selected for this test case that matches the dialed number (the value in the **Number to test** field). 
    
3. **Normalized number**: The value of the dialed number after the normalization rule has translated it.
    
4. **First PSTN usage**: The first public switched telephone network (PSTN) usage record in the voice policy selected for this test case that matches the dialed number.
    
5. **First route**: The first voice route in the first PSTN usage record that matches the dialed number.
    
    > [!NOTE]
    > The **Expected PSTN usage record** and **Expected route** fields are optional in voice routing test case configuration. If the test case does not specify these values, the corresponding field in the test results will be empty. 
  
### To run one or more selected voice routing test cases

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing**, and then click **Test Voice Routing**.
    
4. On the **Test Voice Routing** page, click the names of the test cases that you want to run. 
    
5. On the **Action** menu, click **Run selected**.
    
    The pass or fail status of each test case is shown in the **Pass/fail** column. If a test case has not yet been run, N/A is shown in the **Pass/fail** column. 
    
6. (Optional) To see detailed results for each test case, double-click the test case name. Results are shown in the shaded area on the right side of the **Edit Test Case** page: 
    
1. **Test result**: Overall pass or fail status of the test case run.
    
2. **Normalization rule**: The first normalization rule in the dial plan selected for this test case that matches the dialed number (the value in the **Number to test** field). 
    
3. **Normalized number**: The value of the dialed number after the normalization rule has translated it.
    
4. **First PSTN usage**: The first PSTN usage record in the voice policy selected for this test case that matches the dialed number.
    
5. **First route**: The first voice route in the first PSTN usage record that matches the dialed number.
    
    > [!NOTE]
    > The **Expected PSTN usage record** and **Expected route** fields are optional in voice routing test case configuration. If the test case does not specify these values, the corresponding field in the test results will be empty. 
  
## See also

#### 

[Test voice routing in Lync Server 2013](test-voice-routing.md)
  
[Running voice routing tests in Lync Server 2013](running-voice-routing-tests.md)

