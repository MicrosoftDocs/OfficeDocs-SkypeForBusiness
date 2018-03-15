---
title: "Modify a dial plan in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a91f02df-cf60-40cf-82fe-e0342c118b91
description: "To modify an existing dial plan, perform the steps in the following procedure. If you want to create a new dial plan, see Create a dial plan in Lync Server 2013."
---

# Modify a dial plan in Lync Server 2013
[]
To modify an existing dial plan, perform the steps in the following procedure. If you want to create a new dial plan, see [Create a dial plan in Lync Server 2013](create-a-dial-plan.md).
  
### To modify a dial plan

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md).
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Voice Routing** and then click **Dial Plan**.
    
4. On the **Dial Plan** page, double-click a dial plan name. 
    
    > [!NOTE]
    > The dial plan scope and name were set when the dial plan was created. They cannot be changed. 
  
5. (Optional) In **Edit Dial Plan**, edit the **Simple name** field, which is prepopulated with the same name that appears in the **Name** field to specify a more descriptive name that reflects the site, service, or user to which the dial plan applies. 
    
    > [!IMPORTANT]
    > The **Simple name** must be unique among all dial plans within the Lync Server 2013 deployment. It cannot exceed 256 Unicode characters, each of which can be an alphabetic or numeric character, a hyphen (-), a period (.), a plus sign (+), or an underscore (_). > Spaces are not allowed in the **Simple name** field. 
  
6. (Optional) In the **Description** field, type descriptive information about the dial plan. 
    
7. (Optional) If you want to use this dial plan as a region for dial-in access numbers, specify a **Dial-in conferencing region**. If you do not want to use this dial plan for dial-in access numbers, leave this field empty. 
    
    > [!NOTE]
    > Dial-in conferencing regions are required to associate dial-in conferencing access numbers with one or more dial plans. 
  
8. (Optional) In the **External access prefix** field, specify a value only if users need to dial one or more additional leading digits to get an external line (for example, 9). You can type in a prefix value of up to four characters (that is, #, *, and 0-9). 
    
    > [!NOTE]
    > If you specify an external access prefix, you do not need to create a new normalization rule to accommodate the prefix. 
  
9. Associate and configure normalization rules for the dial plan:
    
  - To choose one or more rules from a list of all normalization rules available in your Enterprise Voice deployment, click **Select**. In the **Select Normalization Rules** dialog box, highlight the rules that you want to associate with the dial plan and then click **OK**.
    
  - To define a new normalization rule and associate it with the dial plan, click **New**. For details about defining a new rule, see [Defining normalization rules in Lync Server 2013](defining-normalization-rules.md).
    
  - To edit a normalization rule that is already associated with the dial plan, highlight the rule name and click **Show details**. For details about editing the rule, see [Defining normalization rules in Lync Server 2013](defining-normalization-rules.md).
    
  - To copy an existing normalization rule to use as a starting point for defining a new rule, highlight the rule name and click **Copy**, and then click **Paste**. For details about editing the copy, see [Defining normalization rules in Lync Server 2013](defining-normalization-rules.md).
    
  - To remove a normalization rule from the dial plan, highlight the rule name and click **Remove**.
    
    > [!NOTE]
    > Each dial plan must have at least one associated normalization rule. For details about how to determine all of the normalization rules a dial plan requires, see [Dial plans and normalization rules in Lync Server 2013](dial-plans-and-normalization-rules.md) in the Planning documentation. 
  
10. Verify that the dial plan's normalization rules are arranged in the correct order. To change a rule's position in the list, highlight the rule name and then click the up or down arrow.
    
    > [!IMPORTANT]
    > Lync Server traverses the normalization rule list from the top down and uses the first rule that matches the dialed number. If you configure a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones. > The default **Keep All** normalization rule ^(\d{11})$ matches any 11-digit number. If, for example, you add a normalization rule that matches 11-digit numbers that start with 1425, make sure that **Keep All** is sorted below the more restrictive ^(1425\d{7})$ rule. 
  
11. (Optional) Enter a number to test the dial plan and then click **Go**. The test results are displayed under **Enter a number to test**.
    
    > [!NOTE]
    > You can save a dial plan that does not yet pass the test and then reconfigure it later. For details, see [Test voice routing in Lync Server 2013](test-voice-routing.md). 
  
12. Click **OK**. 
    
13. On the **Dial Plan** page, click **Commit**, and then click **Commit all**. 
    
    > [!NOTE]
    > Any time you create or modify a dial plan, you must run the **Commit all** command to publish the configuration change. For details, see [Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md) in the Operations documentation. 
  
## See also

#### 

[Create a dial plan in Lync Server 2013](create-a-dial-plan.md)
  
[Publish pending changes to the voice routing configuration in Lync Server 2013](publish-pending-changes-to-the-voice-routing-configuration.md)
#### 

[Defining normalization rules in Lync Server 2013](defining-normalization-rules.md)

