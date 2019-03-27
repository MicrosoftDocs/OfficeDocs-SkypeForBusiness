---
title: Migration process - details
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migration process - details
ms:assetid: ca7e352c-9bde-47d9-8273-5cf2fdfdfe7e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205264(v=OCS.15)
ms:contentKeyID: 48185412
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migration process - details

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

Use the following prerequisites and detailed steps to migrate either Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server.

<div>

## Prerequisites for Migration

Be sure that you’ve met the following prerequisites before migrating either Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat to Lync Server 2013, Persistent Chat Server.

1.  Deploy at least one Lync Server 2013 pool. If you have multiple Lync Server 2013 pools, decide which Lync Server 2013 pool will be the home pool for the new Lync Server 2013 Persistent Chat Server pool.

2.  Install the Lync Server 2013, Persistent Chat Server pool. It will be empty (no categories, rooms, or add-ins). Before you migrate your legacy categories, rooms, or add-ins, you can create rooms, categories, or add-ins in your Lync Server 2013, Persistent Chat Server deployment.
    
    <div>
    

    > [!IMPORTANT]  
    > Be aware that these newly created items may conflict with legacy items that you migrate. Avoid any naming conflicts; otherwise, they will be overwritten when the legacy data is migrated.

    
    </div>

</div>

<div>

## Preparing the Source Data for Migration

Perform the following steps to properly prepare your source data for migration.

1.  Back up the source databases for either Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat. For details about backing up SQL Server, see "Backup Overview (SQL Server)" at <http://go.microsoft.com/fwlink/p/?linkid=254851>.
    
    <div>
    

    > [!IMPORTANT]  
    > Active Directory Domain Services should be the same. As a condition for migration, you cannot migrate to a pool in a different deployment (specifically, in a different Active Directory forest).

    
    </div>

2.  Inspect your Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat chat rooms and category configuration. Any changes to categories, rooms, or add-ins in your existing legacy deployment will be done by the Group Chat Admin Tool.
    
    <div>
    

    > [!TIP]  
    > Any changes to categories, rooms, or add-ins in your Lync Server 2013, Persistent Chat Server deployment are performed by the Lync Server Control Panel or Windows PowerShell cmdlets.

    
    </div>
    
    Follow these steps to prepare your legacy system for migration.
    
    1.  Persistent Chat Server supports a single level of categories, unlike a deep hierarchical set of categories. After migration, the subcategories are prefixed with full parent category names. You might want to simplify and flatten your existing category structure so that the resulting structure meets your requirements.
    
    2.  Verify the **Managers** at the root Category. If any Managers exist at this level, these users will be added as **Managers to all rooms** after migration. If this is not a requirement for your organization, you need to remove these Managers from the root Category.
    
    3.  Verify the length of room names. After migration, due to simplified category structures, if the rooms exist under a child category, they are prefixed with full parent category names. The naming limit is 256 characters, including parent category names. You must verify the length of the room names and possibly shorten the length, if they are too long.
    
    4.  In Lync Server 2013, if the category **invitations** settings are set to true, you can choose true or false for invitations to rooms under that category. However if the category invitations settings are set to false, rooms under that category have invitations turned off. Before migration, you must reset the invitation settings in your legacy Lync Server Group Chat Server version, if you want room(s) to exist under a specific category. Otherwise, during migration, Lync Server 2013 displays warnings and sets rooms to the default value of false.
    
    5.  If you used files in chat rooms, you must XCOPY the files manually to the new Persistent Chat file store after migration. The tools don’t do this.
    
    6.  If you had federated users and rooms with federated users, be aware that Persistent Chat Server does not support federation. Rooms with federated users will be migrated; however, the users themselves won’t be able to access the content, because federated access is not supported.
    
    7.  Identify those rooms that you do not want to migrate, and mark them as disabled.
    
    8.  Identify the date beyond which you want to migrate the chat room content. For example, you may not want to migrate messages earlier than January 1, 2010, because these messages may be obsolete or not relevant for migration.

</div>

<div>

## Performing the Migration

Perform the following steps to migrate your legacy Group Chat Server.

1.  Shut down the Lync Server 2010, Group Chat, Office Communications Server 2007 R2 Group Chat or Lync Server 2013, Persistent Chat Server services. All services must be stopped, so plan to do this at a time when there is enough downtime. As previously described, make sure to back up your current Group Chat database.

2.  Run the Windows PowerShell **Export-CsPersistentChatData** cmdlet as a member of the Persistent Chat administrator RBAC role (CsPersistentChatAdministrator). For details about the export/import cmdlets, see [Troubleshooting Persistent Chat Server configuration using Windows PowerShell cmdlets in Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md).
    
    Inspect the exported contents.

3.  Before you’re ready to import, shut down Lync Server 2013, Persistent Chat Server services. All services need to be stopped, so plan to do this at a time when there is enough downtime.

4.  Perform a backup of the Persistent Chat database if you had created any categories, rooms, or add-ins in your Lync Server 2013 deployment before the migration. The export/import process will be able to merge the legacy data into the Lync Server 2013 deployment, but you’ll want to back up the database in case that content is inadvertently overwritten (for example, if naming conflicts still exist).

5.  Run the Windows PowerShell **Import-CsPersistentChatData** cmdlet (import tool), with a **WhatIf** command to populate the Back End Server of the Persistent Chat Server pool with migrated data. Some conversions happen in the process to accommodate the simplified administration model. Fix any errors or warnings that appear.

6.  Run the Persistent Chat Server Windows PowerShell **Import-CsPersistentChatData** cmdlet as a member of the Persistent Chat administrator RBAC role (CsPersistentChatAdministrator). For details about the export/import cmdlets, see [Troubleshooting Persistent Chat Server configuration using Windows PowerShell cmdlets in Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md).

7.  You must XCOPY all uploaded files (the entire folder) to the new Lync Server 2013, Persistent Chat file store.
    
    <div>
    

    > [!IMPORTANT]  
    > The Lync 2013 (client) does not support uploading or viewing files in chat rooms. You can still use the legacy client to post and view files in the room.

    
    </div>

8.  Port the Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat Lookup Server URI to the Lync Server 2013, Persistent Chat Server contact object. The following steps are required if either your Lync 2010 Group Chat or Office Communicator 2007 R2 Group Chat clients need to connect to the latest Lync 2013, Persistent Chat (client) after migration without any client-side configuration changes:
    
      - Delete the ocschat@\<domainName\>.com Lookup Server user account. This was used to point to the Lookup Service in Lync Server 2010, Group Chat. You can uninstall the pool and remove trusted entries later.
    
      - Create a legacy endpoint (Persistent Chat Server contact object) by running the Windows PowerShell cmdlet, **New-CsPersistentChatEndpoint**, with the identical SIP URI so that the legacy client will work effectively when the service is restarted.
    
    The mandatory migration process is complete at this point. Lync 2010 Group Chat (clients) or Office Communicator 2007 R2 Group Chat (clients) can connect to the new Persistent Chat Server pool now, transparently.
    
    Follow these additional decommissioning steps for Lync Server 2010, Group Chat or Office Communications Server 2007 R2 Group Chat.

9.  Start the Persistent Chat Server services by turning on all computers in the new Persistent Chat Server pool.

10. Use the Lync Server Control Panel and Windows PowerShell cmdlets to verify that the data has migrated successfully.

11. Uninstall Lync 2010 Group Chat or Office Communicator 2007 R2 Group Chat from the computers in the Group Chat Server pool.

12. Delete the trusted application and trusted application pool using Windows PowerShell cmdlets. This deletes these items from the Central Management store and the associated Trusted Service Entries (TSEs) from the Active Directory. Alternatively, this step works by using the Topology Builder (the trusted applications/pools have a dedicated node there, also).

13. You can now begin to enable Persistent Chat Server functionality through the new clients. For details about enabling Persistent Chat Server, see [Deploying Persistent Chat Server in Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md).
    
    <div>
    

    > [!IMPORTANT]  
    > Lync Server 2013 supports multiple Persistent Chat Server pools. However, we support migrating a Lync 2010 Group Chat or Office Communications Server 2007 R2&nbsp;Group Chat pool to a single Lync Server 2013, Persistent Chat Server pool. You can add additional new Persistent Chat Server pools in your deployment to meet the regulatory needs (for example, keeping data within a given geography).

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

