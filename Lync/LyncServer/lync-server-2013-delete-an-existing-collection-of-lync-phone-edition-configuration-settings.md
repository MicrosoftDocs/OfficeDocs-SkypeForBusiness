---
title: 'Delete an existing collection of Lync Phone Edition configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Delete an existing collection of Lync Phone Edition configuration settings
ms:assetid: 1bfc427d-4dcd-4199-b25f-8d5cfec2164f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687984(v=OCS.15)
ms:contentKeyID: 49733574
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Delete an existing collection of Lync Phone Edition configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

If you no longer want to use a collection of settings for devices running Lync Phone Edition, delete it. If you delete a collection for a site, the global settings will apply to the phones in that site. You cannot delete the global collection.

<div>


> [!NOTE]
> Instead of deleting a collection, you might just want to change some of the settings. For details about how to do so, see <A href="lync-server-2013-create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md">Create or modify a collection of Lync Phone Edition configuration settings in Lync Server 2013</A>.



</div>

<div>

## To delete a collection of Lync Phone Edition configuration settings

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Clients**, and then click the **Device Configuration** navigation button.

4.  On the **Device Configuration** page, click the collection you want to delete, click the **Edit** menu, and then click **Delete**.
    
    <div>
    

    > [!NOTE]
    > If you delete the global collection, the settings just revert to the default settings. The collection does not go away.

    
    </div>

5.  In the confirmation box, click **OK**.

</div>

<div>

## Removing Lync Phone Edition Configuration Settings by Using Windows PowerShell Cmdlets

You can delete Lync Phone Edition configuration settings by using Windows PowerShell and the **Remove-CsUCConfiguration** cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To remove a specified collection of Lync Phone Edition configuration settings

  - This command deletes the UC phone configuration settings applied to the Redmond site:
    
        Remove-CsUCPhoneConfiguration -Identity "site:Redmond"

</div>

<div>

## To remove all of the Lync Phone Edition configuration settings applied to the site scope

  - This command removes all the UC phone configuration settings applied to the service scope:
    
        Get-CsUCPhoneConfiguration -Filter "site:*" | Remove-CsUCPhoneConfiguration

</div>

<div>

## To remove all of the Lync Phone Edition configuration settings where phone locking is disabled

  - This command deletes any collection of UC phone configuration settings where phone locking has been disabled:
    
        Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False} | Remove-CsUCPhoneConfiguration

</div>

For details, see [Remove-CsUCPhoneConfiguration](https://technet.microsoft.com/en-us/library/Gg398249(v=OCS.15)).

</div>

</div>

<span> </span>

</div>

</div>

</div>

