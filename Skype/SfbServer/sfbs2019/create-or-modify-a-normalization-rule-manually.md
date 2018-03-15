---
title: "Create or modify a normalization rule manually in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fc0335e6-8830-4cfb-8c64-6aeb98c0a992
description: "Complete the following steps if you want to create or modify a normalization rule manually. If you want to create or modify a normalization rule by using Build a Normalization Rule in Lync Server Control Panel, see Create or modify a normalization rule by using Build a Normalization Rule in Lync Server 2013."
---

# Create or modify a normalization rule manually in Lync Server 2013
[]
Complete the following steps if you want to create or modify a normalization rule manually. If you want to create or modify a normalization rule by using Build a Normalization Rule in Lync Server Control Panel, see [Create or modify a normalization rule by using Build a Normalization Rule in Lync Server 2013](create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md).
  
### To define a normalization rule manually

1. Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. (Optional) Follow the steps in [Create a dial plan in Lync Server 2013](create-a-dial-plan.md) or [Modify a dial plan in Lync Server 2013](modify-a-dial-plan.md). 
    
4. In **New Normalization Rule** or **Edit Normalization Rule**, type a name that describes the number pattern being normalized in **Name** (for example, name the normalization rule 5DigitExtension).
    
5. (Optional) In **Description** field, type a description of the normalization rule (for example, "Translates 5-digit extensions"). 
    
6. In **Build a Normalization Rule**, click **Edit**.
    
7. Enter the following in **Type a Regular Expression**:
    
  - In **Match this pattern**, specify the pattern that you want to use to match the dialed phone number.
    
  - In **Translation rule**, specify a pattern for the format of translated E.164 phone numbers.
    
    For example, if you enter ^(\d{7})$ in **Match this pattern** and +1425$1 in **Translation rule**, the rule normalizes 5550100 to +14255550100.
    
8. (Optional) If the normalization rule results in a phone number that is internal to your organization, select **Internal extension**.
    
9. (Optional) Enter a number to test the normalization rule and then click **Go**. The test results are displayed under **Enter a number to test**.
    
    > [!NOTE]
    > You can save a normalization rule that does not yet pass the test and then reconfigure it later. For details, see [Test voice routing in Lync Server 2013](test-voice-routing.md). 
  
10. Click **OK** to save the normalization rule. 
    
11. Click **OK** to save the dial plan. 
    
12. On the **Dial Plan** page, click **Commit**, and then click **Commit all**. 
    
    > [!NOTE]
    > Whenever you create or change a normalization rule, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md) in the Operations documentation. 
  
## See also

#### 

[Create or modify a normalization rule by using Build a Normalization Rule in Lync Server 2013](create-or-modify-a-normalization-rule-by-using-build-a-normalization-rule.md)
  
[Create a dial plan in Lync Server 2013](create-a-dial-plan.md)
  
[Modify a dial plan in Lync Server 2013](modify-a-dial-plan.md)
  
[Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md)
#### 

[Test voice routing in Lync Server 2013](test-voice-routing.md)

