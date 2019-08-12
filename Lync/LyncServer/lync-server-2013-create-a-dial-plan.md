---
title: 'Lync Server 2013: Create a dial plan'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Create a dial plan
ms:assetid: d2fef3d0-7e78-4591-b712-d62ac71d71a5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398909(v=OCS.15)
ms:contentKeyID: 48185424
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a dial plan in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-10-24_

To create a new dial plan, perform the steps in the following procedure. If you want to edit a dial plan, see [Modify a dial plan in Lync Server 2013](lync-server-2013-modify-a-dial-plan.md).

<div>

## To create a dial plan

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing** and then click **Dial Plan**.

4.  On the **Dial Plan** page, click **New** and select a scope for the dial plan:
    
      - **Site dial plan** applies to an entire site, except any users or groups that are assigned to a user dial plan. If you select **Site** for a dial plan’s scope, you must choose the site from the **Select a Site** dialog box. If a dial plan has already been created for a site, the site does not appear in the **Select a Site** dialog box.
    
      - **Pool dial plan** can apply to a public switched telephone network (PSTN) gateway or a Registrar. If you select **Pool** for a dial plan’s scope, choose the PSTN gateway or Registrar from the **Select a Service** dialog box. If a dial plan has already been created for a service (PSTN gateway or Registrar), the service does not appear in the list.
    
      - **User dial plan** can be applied to specified users or groups.
    
    <div>
    

    > [!NOTE]  
    > After you select the dial plan scope, it cannot be changed.

    
    </div>

5.  If you are creating a user dial plan, enter a descriptive name in the **Name** field on the **New Dial Plan** dialog box. After this name is saved, it cannot be changed.
    
    <div>
    

    > [!NOTE]  
    > For site dial plans, the <STRONG>Name</STRONG> field is prepopulated with the site name and cannot be changed.<BR>For pool dial plans, the <STRONG>Name</STRONG> field is prepopulated with the PSTN gateway or Registrar name and cannot be changed.

    
    </div>

6.  The **Simple name** field is prepopulated with the same name that appears in the **Name** field. You can optionally edit this field to specify a more descriptive name that reflects the site, service, or user to which the dial plan applies.
    
    <div>
    

    > [!IMPORTANT]  
    > The <STRONG>Simple name</STRONG> must be unique among all dial plans within the Lync Server deployment. It cannot exceed 256 Unicode characters, each of which can be an alphabetic or numeric character, a hyphen (-), a period (.), or an underscore (_).<BR>Characters <STRONG>not supported</STRONG> include spaces and Reserved characters as defined in RFC 3966 (http://www.ietf.org/rfc/rfc3966.txt). Reserved characters that are <STRONG>not supported</STRONG> in the <STRONG>Simple Name</STRONG> include the following:<BR>";" "/" "?" ":" "@" "&amp;" "=" "+" "$" ","

    
    </div>

7.  (Optional) In the **Description** field, you can type additional descriptive information about the dial plan.

8.  (Optional) If you want to use this dial plan as a region for dial-in access numbers, specify a **Dial-in conferencing region**. If you do not want to use this dial plan for dial-in access numbers, leave this field empty.
    
    <div>
    

    > [!NOTE]  
    > Dial-in conferencing regions are required to associate dial-in conferencing access numbers with one or more dial plans.

    
    </div>

9.  (Optional) In the **External access prefix** field, specify a value only if users need to dial one or more additional leading digits (for example, 9) to get an external line. You can type in a prefix value of up to four characters (\#, \*, and 0-9).
    
    <div>
    

    > [!NOTE]  
    > If you specify an external access prefix, you do not need to create a new normalization rule to accommodate the prefix.

    
    </div>

10. Associate and configure normalization rules for the dial plan as follows:
    
      - To choose one or more rules from a list of all normalization rules available in your Enterprise Voice deployment, click **Select**. In **Select Normalization Rules**, highlight the rules you want to associate with the dial plan and then click **OK**.
    
      - To define a new normalization rule and associate it with the dial plan, click **New**. For details about defining a new rule, see [Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - To edit a normalization rule that is already associated with the dial plan, highlight the rule name and click **Show details**. For details about editing the rule, see [Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - To copy an existing normalization rule to use as a starting point for defining a new rule, highlight the rule name and click **Copy**, and then click **Paste**. For details about editing the copy, see [Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md).
    
      - To remove a normalization rule from the dial plan, highlight the rule name and click **Remove**.
    
    <div>
    

    > [!NOTE]  
    > Each dial plan must have at least one associated normalization rule. For information about how to determine all of the normalization rules a dial plan requires, see <A href="lync-server-2013-dial-plans-and-normalization-rules.md">Dial plans and normalization rules in Lync Server 2013</A> in the Planning documentation.

    
    </div>

11. Verify that the dial plan’s normalization rules are arranged in the correct order. To change a rule’s position in the list, highlight the rule name and then click the up or down arrow.
    
    <div>
    

    > [!IMPORTANT]  
    > Lync Server traverses the normalization rule list from the top down and uses the first rule that matches the dialed number. If you configure a dial plan so that a dialed number can match more than one normalization rule, make sure the more restrictive rules are sorted above the less restrictive ones.<BR>The default <STRONG>Keep All</STRONG> normalization rule <STRONG>^(\d{11})$</STRONG> matches any 11-digit number. For example, if you add a normalization rule that matches 11-digit numbers that start with 1425, make sure that <STRONG>Keep All</STRONG> is sorted below the more restrictive <STRONG>^(1425\d{7})$</STRONG> rule.

    
    </div>

12. (Optional) Enter a number to test the dial plan and then click **Go**. The test results are displayed under **Enter a number to test**.
    
    <div>
    

    > [!NOTE]  
    > You can save a dial plan that does not yet pass the test and then reconfigure it later. For details, see <A href="lync-server-2013-test-voice-routing.md">Test voice routing in Lync Server 2013</A>.

    
    </div>

13. Click **OK**.

14. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.
    
    <div>
    

    > [!NOTE]  
    > Any time you create a dial plan, you must run the <STRONG>Commit all</STRONG> command to publish the configuration change. For details, see <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publish pending changes to the voice routing configuration in Lync Server 2013</A> in the Operations documentation.

    
    </div>

</div>

<div>

## See Also


[Modify a dial plan in Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)  
[Publish pending changes to the voice routing configuration in Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  


[Defining normalization rules in Lync Server 2013](lync-server-2013-defining-normalization-rules.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

