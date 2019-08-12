---
title: 'Lync Server 2013: Modify a dial plan'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Modify a dial plan
ms:assetid: a91f02df-cf60-40cf-82fe-e0342c118b91
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412797(v=OCS.15)
ms:contentKeyID: 48185099
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify a dial plan in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

To modify an existing dial plan, perform the steps in the following procedure. If you want to create a new dial plan, see [Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md).

<div>

## To modify a dial plan

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing** and then click **Dial Plan**.

4.  On the **Dial Plan** page, double-click a dial plan name.
    
    <div>
    

    > [!NOTE]  
    > The dial plan scope and name were set when the dial plan was created. They cannot be changed.

    
    </div>

5.  (Optional) In **Edit Dial Plan**, edit the **Simple name** field, which is prepopulated with the same name that appears in the **Name** field to specify a more descriptive name that reflects the site, service, or user to which the dial plan applies.
    
    <div>
    

    > [!IMPORTANT]  
    > The <STRONG>Simple name</STRONG> must be unique among all dial plans within the Lync Server 2013 deployment. It cannot exceed 256 Unicode characters, each of which can be an alphabetic or numeric character, a hyphen (-), a period (.), a plus sign (+), or an underscore (_).<BR>Spaces are not allowed in the <STRONG>Simple name</STRONG> field.

    
    </div>

6.  (Optional) In the **Description** field, type descriptive information about the dial plan.

7.  (Optional) If you want to use this dial plan as a region for dial-in access numbers, specify a **Dial-in conferencing region**. If you do not want to use this dial plan for dial-in access numbers, leave this field empty.
    
    <div>
    

    > [!NOTE]  
    > Dial-in conferencing regions are required to associate dial-in conferencing access numbers with one or more dial plans.

    
    </div>

8.  (Optional) In the **External access prefix** field, specify a value only if users need to dial one or more additional leading digits to get an external line (for example, 9). You can type in a prefix value of up to four characters (that is, \#, \*, and 0-9).
    
    <div>
    

    > [!NOTE]  
    > If you specify an external access prefix, you do not need to create a new normalization rule to accommodate the prefix.

    
    </div>

9.  Associate and configure normalization rules for the dial plan:
    
      - To choose one or more rules from a list of all normalization rules available in your Enterprise Voice deployment, click **Select**. In the **Select Normalization Rules** dialog box, highlight the rules that you want to associate with the dial plan and then click **OK**.
    
      - To define a new normalization rule and associate it with the dial plan, click **New**. For details about defining a new rule, see [Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - To edit a normalization rule that is already associated with the dial plan, highlight the rule name and click **Show details**. For details about editing the rule, see [Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - To copy an existing normalization rule to use as a starting point for defining a new rule, highlight the rule name and click **Copy**, and then click **Paste**. For details about editing the copy, see [Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - To remove a normalization rule from the dial plan, highlight the rule name and click **Remove**.
    
    <div>
    

    > [!NOTE]  
    > Each dial plan must have at least one associated normalization rule. For details about how to determine all of the normalization rules a dial plan requires, see <A href="lync-server-2013-dial-plans-and-normalization-rules.md">Dial plans and normalization rules in Lync Server 2013</A> in the Planning documentation.

    
    </div>

10. Verify that the dial plan’s normalization rules are arranged in the correct order. To change a rule’s position in the list, highlight the rule name and then click the up or down arrow.
    
    <div>
    

    > [!IMPORTANT]  
    > Lync Server traverses the normalization rule list from the top down and uses the first rule that matches the dialed number. If you configure a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones.<BR>The default <STRONG>Keep All</STRONG> normalization rule <STRONG>^(\d{11})$</STRONG> matches any 11-digit number. If, for example, you add a normalization rule that matches 11-digit numbers that start with 1425, make sure that <STRONG>Keep All</STRONG> is sorted below the more restrictive <STRONG>^(1425\d{7})$</STRONG> rule.

    
    </div>

11. (Optional) Enter a number to test the dial plan and then click **Go**. The test results are displayed under **Enter a number to test**.
    
    <div>
    

    > [!NOTE]  
    > You can save a dial plan that does not yet pass the test and then reconfigure it later. For details, see <A href="lync-server-2013-test-voice-routing.md">Test voice routing in Lync Server 2013</A>.

    
    </div>

12. Click **OK**.

13. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.
    
    <div>
    

    > [!NOTE]  
    > Any time you create or modify a dial plan, you must run the <STRONG>Commit all</STRONG> command to publish the configuration change. For details, see <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publish pending changes to the voice routing configuration in Lync Server 2013</A> in the Operations documentation.

    
    </div>

</div>

<div>

## See Also


[Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Publish pending changes to the voice routing configuration in Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  


[Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

