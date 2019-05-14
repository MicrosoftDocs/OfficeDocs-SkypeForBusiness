---
title: 'Lync Server 2013: Assign an external user access policy to a Lync enabled user'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Assign an external user access policy to a Lync enabled user
ms:assetid: 736fcaad-9f95-4896-b767-e199d86a00a4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398551(v=OCS.15)
ms:contentKeyID: 48184483
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assign an external user access policy to a Lync enabled user in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

If a user has been enabled for Lync Server, you can configure SIP federation, XMPP federation, remote user access, and public instant messaging (IM) connectivity in the Lync Server Control Panel by applying the appropriate policies to specific users. For example, if you created a policy to support remote user access, you must apply it to the user before the user can connect to Lync Server from a remote location and collaborate with internal users from the remote location.

<div>


> [!NOTE]  
> To support external user access, you must enable support for each type of external user access you want to support, and configure the appropriate policies and other options to control its use. For details, see <A href="lync-server-2013-configuring-support-for-external-user-access.md">Configuring support for external user access in Lync Server 2013</A> in the Deployment documentation or <A href="lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md">Managing federation and external access to Lync Server 2013</A> in the Operations documentation.



</div>

Use the procedure in this topic to apply a previously created external user access policy to one or more user accounts.

<div>

## To apply an external user policy to a user account

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**, and then search on the user account that you want to configure.

4.  In the table that lists the search results, click the user account, click **Edit**, and then click **Show details**.

5.  In **Edit Lync Server User** under **External access policy**, select the user policy that you want to apply.
    
    <div>
    

    > [!NOTE]  
    > The <STRONG>&lt;Automatic&gt;</STRONG> settings apply the default server or global policy settings.

    
    </div>

</div>

<div>

## Assigning Per-User External Access Policies by Using Windows PowerShell Cmdlets

Per-user external access policies can be assigned by using Windows PowerShell and the Grant-CsExternalAccessPolicy cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To assign a per-user external access policy to a single user

  - This command assigns the per-user external access policy RedmondExternalAccessPolicy to the user Ken Myer.
    
        Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName "RedmondExternalAccessPolicy"

</div>

<div>

## To assign a per-user external access policy to multiple users

  - This command assigns the per-user external access policy USAExternalAccessPolicy to all the users who have accounts in the UnitedStates OU in Active Directory. For more information on the OU parameter used in this command, see the documentation for the [Get-CsUser](https://docs.microsoft.com/powershell/module/skype/Get-CsUser) cmdlet.
    
        Get-CsUser -OU "ou=UnitedStates,dc=litwareinc,dc=com" | Grant-CsExternalAccessPolicy -PolicyName "USAExternalAccessPolicy"

</div>

<div>

## To unassign a per-user external access policy

  - This command unassigns any per-user external access policy previously assigned to Ken Myer. After the per-user policy is unassigned, Ken Myer will automatically be managed by using the global policy or, if one exists, his local site policy. A site policy takes precedence over the global policy.
    
        Grant-CsExternalAccessPolicy -Identity "Ken Myer" -PolicyName $Null

</div>

For more information, see the help topic for the [Grant-CsExternalAccessPolicy](https://docs.microsoft.com/powershell/module/skype/Grant-CsExternalAccessPolicy) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

