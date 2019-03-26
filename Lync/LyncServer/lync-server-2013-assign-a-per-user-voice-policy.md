---
title: 'Lync Server 2013: Assign a per-user voice policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Assign a per-user voice policy
ms:assetid: 9ee47ee7-1030-43b8-a4dc-bf685ea24659
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688155(v=OCS.15)
ms:contentKeyID: 49733758
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

# Assign a per-user voice policy in Lync Server 2013

 


Global and site-level voice policies are automatically assigned to all Lync Server 2013 user accounts that are enabled for Enterprise Voice. You can also assign voice policies to specific users by using either the Lync Server 2013 Control Panel or the Lync Server 2013 Management Shell. Use the procedures in this topic to explicitly assign per-user policies to Lync Server users.

## To assign a user-specific voice policy using the Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**, and then search on the user account that you want to configure.

4.  In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.

5.  In **Edit Lync Server User** under **Voice policy**, select the user policy that you want to apply.
    

    > [!NOTE]  
    > The <STRONG>&lt;Automatic&gt;</STRONG> settings apply the default server or global policy settings.



## Assigning a Per-User Voice Policy by using Windows PowerShell Cmdlets

You can assign per-user voice policies by using Windows PowerShell and the **Grant-CsVoicePolicy** cmdlet. You can run this cmdlet from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## To assign a per-user voice policy to a single user

  - The following command assigns the per-user voice policy RedmondVoicePolicy to the user Ken Myer.
    
        Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

## To assign a per-user voice policy to multiple users

  - This command assigns the per-user voice policy FinanceVoicePolicy to all the users who have accounts in the Finance OU in Active Directory. For more information on the OU parameter used in this command, see the documentation for the [Get-CsUser](https://technet.microsoft.com/en-us/library/gg398125\(v=ocs.15\)) cmdlet.
    
        Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsVoicePolicy -PolicyName "FinanceVoicePolicy"

## To unassign a per-user voice policy

  - The following command unassigns any per-user voice policy previously assigned to Ken Myer. After the per-user policy is unassigned, Ken Myer will automatically be managed by using the global policy or, if one exists, his local site policy. A site policy takes precedence over the global policy.
    
        Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null

For more information, see the help topic for the [Grant-CsVoicePolicy](https://technet.microsoft.com/en-us/library/gg398828\(v=ocs.15\)) cmdlet.

## See Also


[Disable a user for Enterprise Voice in Lync Server 2013](lync-server-2013-disable-a-user-for-enterprise-voice.md)  


[Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md)

