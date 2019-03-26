---
title: 'Lync Server 2013: Assign a per-user dial plan policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Assign a per-user dial plan policy
ms:assetid: 9fea861f-7770-4cae-9b1f-2a960595bfc9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688156(v=OCS.15)
ms:contentKeyID: 49733760
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

# Assign a per-user dial plan policy in Lync Server 2013

 


To complete user account configuration for either users of Enterprise Voice or users of dial-in conferencing, the user must be assigned a dial plan. User accounts will automatically use the global dial plan or, if one exists, the site-level dial plan when you do not explicitly assign an existing per-user dial plan. If you want to use the global or site dial plan for all users that are enabled for Enterprise Voice, you can skip this section.

## To assign a dial plan by using the Lync Server 2013 Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to enable, and then click **Find**.

5.  In the table, click the user account that you want to assign a dial plan.

6.  On the **Edit** menu, click **Show details**.

7.  On the **Edit Lync Server User** page, under **Telephony**, click **Enterprise Voice**.

8.  Click **Dial plan policy**, and then choose the desired dial plan.

9.  Click **Commit**.

For details about configuring dial plans, see the [Configuring dial plans in Lync Server 2013](lync-server-2013-configuring-dial-plans.md) topic.

## Assign a Per-User Dial Plan by Using Windows PowerShell Cmdlets

You can assign per-user dial plans with Windows PowerShell and the **Grant-CsdialPlan** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## To assign a per-user dial plan to a single user

  - The following command assigns the per-user dial plan RedmondDialPlan to the user Ken Myer.
    
        Grant-CsDialPlan -Identity "Ken Myer" -PolicyName "RedmondDialPlan"

## To assign a per-user dial plan to multiple users

  - This command assigns the per-user dial plan RedmondDialPlan to all the users who work in the city of Redmond. For more information on the LdapFilter parameter used in this command, see the documentation for the [Get-CsUser](https://technet.microsoft.com/en-us/library/gg398125\(v=ocs.15\)) cmdlet.
    
        Get-CsUser -LdapFilter "l=Redmond" | Grant-CsDialPlan -PolicyName "RedmondDialPlan"

## To unassign a per-user dial plan

  - The following command unassigns any per-user dial plan previously assigned to Ken Myer. After the per-user dial plan is unassigned, Ken Myer will automatically be managed by using the global dial plan, his local site dial plan (if one exists), or the service-scope dial plan assigned to his Registrar or PSTN gateway. A service scope dial plan takes precedence over any site dial plan, and a site dial plan takes precedence over the global dial plan.
    
        Grant-CsDialPlan -Identity "Ken Myer" -PolicyName $Null

For more information, see the help topic for the [Grant-CsDialPlan](https://technet.microsoft.com/en-us/library/gg398547\(v=ocs.15\)) cmdlet.

## See Also


[Configuring dial plans in Lync Server 2013](lync-server-2013-configuring-dial-plans.md)  
[User accounts enabled for Lync Server 2013](lync-server-2013-user-accounts-enabled-for-lync-server.md)

