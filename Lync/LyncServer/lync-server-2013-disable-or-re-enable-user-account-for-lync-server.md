---
title: 'Lync Server 2013: Disable or re-enable user account for Lync Server'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Disable or re-enable user account for Lync Server
ms:assetid: 12497d00-f665-4a97-be68-854c5a8be4fc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg429696(v=OCS.15)
ms:contentKeyID: 48183455
ms.date: 04/05/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Disable or re-enable user account for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-04-04_

You can use the following procedure to disable a previously enabled user account in Lync Server 2013 without losing the Lync Server settings that you configured for the user account. Because you do not lose the Lync Server user account settings, you can re-enable a previously enabled user account again without having to reconfigure the user account.

<div>


> [!WARNING]  
> Simply disabling a user account in Active Directory <STRONG>will not</STRONG> stop a user from being able to sign into or use Lync Server. This is because Lync uses certificate authentication that streamlines the authentication process, and these client certificates are valid for 180 days. If you want to stop disabled Active Directory accounts that had been enabled for Lync from having access to Lync Server, you must use the <STRONG>Disable-CsUser</STRONG> cmdlet, or use the <STRONG>Lync Server Control Panel</STRONG> as laid out in this article. Once the user is disabled in Lync and the Central Management store has been replicated in the environment the users will no longer be able to sign in. Also, users that are signed in will get disconnected.



</div>

<div>

## To disable or re-enable a previously enabled user account for Lync Server

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want to disable or re-enable, and then click **Find**.

5.  In the table, click the user account that you want to disable or re-enable.

6.  On the **Action** menu, do one of the following:
    
      - To temporarily disable the user account for Lync Server 2013, click **Temporarily disable for Lync Server**.
    
      - To enable the user account for Lync Server 2013, click **Re-enable for Lync Server**.

</div>

<div>

## Using Windows PowerShell to Disable or Re-enable User Accounts

User accounts can be temporarily disabled, and then later re-enabled, by using the **Set-CsUser** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To disable a user account

  - To temporarily disable a user account, set the value of the Enabled property to False ($False). For example:
    
        Set-CsUser -Identity "Ken Myer" -Enabled $False

</div>

<div>

## To re-enable a user account

  - To re-enable a disabled user account, set the value of the Enabled property to True ($True). For example:
    
        Set-CsUser -Identity "Ken Myer" -Enabled $True

</div>

For more information, see the help topic for the [Set-CsUser](https://docs.microsoft.com/powershell/module/skype/Set-CsUser) cmdlet.

</div>

<div>

## See Also


[Add and enable user account for Lync Server 2013](lync-server-2013-add-and-enable-user-account-for-lync-server.md)  


[Enabling and disabling users for Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

