---
title: 'Lync Server 2013: Enable users for Enterprise Voice'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enable users for Enterprise Voice
ms:assetid: f252b23b-9641-4160-aa81-bf06dc2eced3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413011(v=OCS.15)
ms:contentKeyID: 48185800
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable users for Enterprise Voice in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

After you install files for one or more Mediation Servers, configure outbound call routing, and optionally deploy one or more advanced Enterprise Voice features, you can use the following procedures to enable a user to make calls by using Enterprise Voice:

<div>


> [!NOTE]  
> Of the following procedures, only the first can be performed by using Lync Server Control Panel. For the remaining procedures, you can use only Lync Server Management Shell.



</div>

  - Enable the user account for Enterprise Voice.

  - (Optional) Assign the user account a user-specific voice policy.

  - (Optional) Assign the user account a user-specific dial plan.

<div>

## To enable a user account for Enterprise Voice

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.

5.  In the table, click the user account that you want to enable for Enterprise Voice.

6.  On the **Edit** menu, click **Show details**.

7.  On the **Edit Lync Server User** page, under **Telephony**, click **Enterprise Voice**.

8.  Click **Line URI**, and then type a unique, normalized phone number (for example, tel:+14255550200).

9.  Click **Commit**.

To finish enabling a user for Enterprise Voice, be sure that the user is assigned a voice policy and a dial plan, whether global (assigned by default) or user-specific.

By default, all users are assigned a global voice policy and dial plan. If a voice policy or dial plan exists at the site level for the site on which the user account is homed, those site policies will automatically apply to the user. To apply a per-user voice policy or dial plan to a user, you must run the **Grant-CsVoicePolicy** and **Grant-CsDialPlan** cmdlets. For details, see the [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md) documentation.

</div>

<div>

## Voice Policy Assignment

Global and site-level voice policies are automatically assigned to all user accounts that are enabled for Enterprise Voice. You can also create voice policies that apply to specific users or groups. These per-user policies must be explicitly assigned to the users or groups. If you want to use the global or site voice policy for all users who are enabled for Enterprise Voice, you can skip this section and continue to Dial Plan Assignment section later in this topic.

<div>

## To assign a user-specific voice policy

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  To assign an existing user voice policy to a user, run the following at the command prompt:
    
        Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String>
    
    For example:
    
        Grant-CsVoicePolicy -Identity "Bob Kelly" -PolicyName VoicePolicyJapan
    
    In this example, the user with the display name Bob Kelly is assigned the voice policy with the name **VoicePolicyJapan**.

For details about assigning a user-specific voice policy or about running the **Grant-CsVoicePolicy** cmdlet, see the [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md) documentation.

</div>

</div>

<span id="BKMK_DialPlanAssignment"></span>

<div>

## Dial Plan Assignment

To complete user account configuration for either users of Enterprise Voice or users of dial-in conferencing, the user must be assigned a dial plan. User accounts will automatically use the global dial plan or, if one exists, the site-level dial plan, when you do not explicitly assign an existing per-user dial plan. If you want to use the global or site dial plan for all users who are enabled for Enterprise Voice, you can skip this section.

<div>

## To assign a dial plan

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  To assign a user-specific dial plan, run the following at the command prompt:
    
        Grant-CsDialPlan -Identity <UserIdParameter> -PolicyName <String>
    
    For example:
    
        Grant-CsDialPlan -Identity "Bob Kelly" -PolicyName DialPlanJapan
    
    In this example, the user with the display name Bob Kelly is assigned the user dial plan with the name **DialPlanJapan**.

For details about assigning a user dial plan or about running the **Grant-CsDialPlan** cmdlet, see the [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md) documentation.

</div>

</div>

<div>

## See Also


[Disable a user for Enterprise Voice in Lync Server 2013](lync-server-2013-disable-a-user-for-enterprise-voice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

