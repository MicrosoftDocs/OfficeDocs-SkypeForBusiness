---
title: 'Lync Server 2013: Move users to Lync Online'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Move users to Lync Online
ms:assetid: 6a523c86-2eac-4fa4-973a-4406872c9a7d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204969(v=OCS.15)
ms:contentKeyID: 48184392
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move users to Lync Online in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-29_

Before you start migrating users to Lync Online, you should backup the user data associated with the accounts to be moved. Not all user data is moved with the user account. For information, see [Backup and restoration requirements in Lync Server 2013: data](lync-server-2013-backup-and-restoration-requirements-data.md).

<div>

## Migrate User Settings to Lync Online

User settings are moved with the user account. Some on-premises settings are not moved with the user account.

</div>

<div>

## Moving Pilot Users to Lync Online

Before you begin to move users to Lync Online, you may want to move a few pilot users to confirm that your environment is correctly configured. You can then verify that Lync features and services function as expected before attempting to move additional users.

To move an on-premises user to your Lync Online tenant, run the following cmdlets in the Lync Server Management Shell, using the administrator credentials for your Microsoft Office 365 tenant. Replace "username@contoso.com" with the information for the user that you want to move.

   ```
    $creds=Get-Credential
   ```

   ```
    Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>
   ```

The format of the URL specified for the **HostedMigrationOverrideUrl** parameter must be the URL to the pool where the Hosted Migration service is running, in the following format: Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc.

You can determine the URL to the Hosted Migration Service by viewing the URL for the Lync Online Control Panel for your Office 365 tenant account.

**To determine the Hosted Migration Service URL for your Office 365 tenant**

1.  Login to your Office 365 tenant as an administrator.

2.  Open the **Lync admin center**.

3.  With the **Lync admin center** displayed, select and copy the URL in the address bar up to **lync.com**. An example URL looks similar to the following:
    
    `https://webdir0a.online.lync.com/lscp/?language=en-US&tenantID=`

4.  Replace **webdir** in the URL with **admin**, resulting in the following:
    
    `https://admin0a.online.lync.com`

5.  Append the following string to the URL: **/HostedMigration/hostedmigrationservice.svc**.
    
    The resulting URL, which is the value of the **HostedMigrationOverrideUrl**, should look like the following:
    
    `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`

</div>

<div>

## Moving Users to Lync Online

You can move multiple users by using the [Get-CsUser](https://docs.microsoft.com/powershell/module/skype/Get-CsUser) cmdlet with the –Filter parameter to select the users with a specific property assigned to the user accounts, such as RegistrarPool. You can then pipe the returned users to the [Move-CsUser](https://docs.microsoft.com/powershell/module/skype/Move-CsUser) cmdlet, as shown in the following example.

    Get-CsUser -Filter {UserProperty -eq "UserPropertyValue"} | Move-CsUser -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>

You can also use the –OU parameter to retrieve all users in the specified OU, as shown in the following example.

    Get-CsUser -OU "cn=hybridusers,cn=contoso.." | Move-CsUser -Target sipfed.online.lync.com -Credentials $creds -HostedMigrationOverrideUrl <URL>

</div>

<div>

## Verify Lync Online User Settings and Features

You can verify that the user was moved successfully in the following ways:

  - View the status of the user in the Lync Online Control Panel. The visual indicator for on-premises users and online users is different.

  - Run the following cmdlet:
    
        Get-CsUser -Identity

</div>

</div>

<span> </span>

</div>

</div>

</div>

