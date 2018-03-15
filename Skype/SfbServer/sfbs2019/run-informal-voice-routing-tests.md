---
title: "Run informal voice routing tests in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ea0e6059-bf04-4b03-b6d3-8f5534b731e2
description: "You can use the Create voice routing test case information dialog box to run informal tests before creating an actual test case. When you are satisfied with the outcome of a test, you have the option of saving it as a formal test case."
---

# Run informal voice routing tests in Lync Server 2013
[]
You can use the **Create voice routing test case information** dialog box to run informal tests before creating an actual test case. When you are satisfied with the outcome of a test, you have the option of saving it as a formal test case. 
  
### To run an informal voice routing test

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing**, and then click **Test Voice Routing**.
    
4. On the **Test Voice Routing** page, click **Create voice routing test case information**.
    
5. In the **Dialed number** field, type in the phone number you want to use for this test. This number will be normalized and displayed in the **Normalized number** field of the **Results** pane. 
    
6. In the **Dial plan** list, select the dial plan to use for testing the dialed number. Default is the Global dial plan. 
    
    When you run the test, the first normalization rule in this dial plan that matches the dialed number will be displayed in the **Normalization rule** field of the **Results** pane. 
    
7. In the **Voice Policy** list, select the voice policy to use for testing the dialed number. Default is the Global voice policy. 
    
    When you run the test, the first matching PSTN usage record in this voice policy will be displayed in the **First PSTN usage** field of the **Results** pane. Also, the first matching voice route that is associated with this PSTN usage record will be displayed in the **First route** field. 
    
8. (Optional) Select the **Populate from user** check box if you want to test the dialed number against the voice policy assigned to a particular user. 
    
1. Click **Browse** to display the **Select Enterprise Voice Users** dialog box. 
    
2. Click **Find** to display the list of users who are enabled for Enterprise Voice. 
    
3. Double-click the user name whose assigned voice policy you want to use for this test. The **Policy** field is now populated with the voice policy assigned to the selected user. 
    
    When you run the test, the first matching public switched telephone network (PSTN) usage record in this voice policy will be displayed in the **First PSTN usage** field of the **Results** pane. Also, the first matching voice route that is associated with this PSTN usage record will be displayed in the **First route** field. 
    
9. Click **Run** to run the test case. The results are shown in the right panel of the dialog box. 
    
10. (Optional) Click **Save as** if you want to save this test configuration as a formal test case. 
    
1. In the **Name** field of the **Save Voice Routing Test Case Information** dialog box, type a unique name for the test case. 
    
    The name must be unique among all voice routing test cases in your Enterprise Voice deployment. It can be up to 32 characters in length and may contain any alphanumeric characters, in addition to the backslash (\), period (.), or underscore (_).
    
2. Note that the remaining fields on the **Save Voice Routing Test Case Information** dialog box are read-only, and are prepopulated from the informal test configuration  *and*  results. Verify that this is the configuration that you want to save for the test case. 
    
    > [!NOTE]
    >  Values from the test results are used to prepopulate fields on the **Save Voice Routing Test Case Information** dialog box as follows: > **Expected translation** is prepopulated with the value in the **Normalized number** field. > **Expected route** is prepopulated with the value in the **First route** field. > **Expected PSTN usage record** is prepopulated with the value in the **First PSTN usage** field. >  If matches for any of these values were not found during the test run, the corresponding field is empty on the **Save Voice Routing Test Case Information** dialog box. 
  
3. Click **Ok** to save the test case, or click **Cancel** to return to return to the **View voice routing test case information** dialog box to further develop the test before saving it. 
    
11. Click **Commit**, and then click **Commit all**. 
    
    > [!NOTE]
    > Whenever you create a voice routing test case, you must run the **Commit all** command to publish the test case. For details, see [Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md) in the Operations documentation. 
  
## See also

#### 

[Create a voice routing test case in Lync Server 2013](create-a-voice-routing-test-case.md)
  
[Run voice routing test cases in Lync Server 2013](run-voice-routing-test-cases.md)
  
[Export voice routing test cases in Lync Server 2013](export-voice-routing-test-cases.md)
  
[Import voice routing test cases in Lync Server 2013](import-voice-routing-test-cases.md)
#### 

[Configuring dial plans in Lync Server 2013](configuring-dial-plans.md)
  
[Configuring voice policies, PSTN usage records, and voice routes in Lync Server 2013](configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

