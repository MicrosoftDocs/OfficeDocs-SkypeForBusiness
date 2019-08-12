---
title: Migrate response groups
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrate response groups
ms:assetid: 43741ae7-c871-4573-b660-f2f5febc0856
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204854(v=OCS.15)
ms:contentKeyID: 48184020
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrate response groups

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-09-23_

After your users are moved to Lync Server 2013 pools, you can migrate your response groups. Migrating response groups includes copying agent groups, queues, workflows, audio files, and moving Response Group contact objects from the legacy deployment to the Lync Server 2013 pool. After you migrate your legacy response groups, calls to the response groups are handled by the Response Group application in the Lync Server 2013 pool. Calls to response groups are no longer handled by the legacy pool.

<div>


> [!NOTE]  
> Although you can migrate response groups before you move all users to the Lync Server 2013 pool, we recommend that you move all users first. In particular, users who are response group agents will not have full functionality of new features until they are moved to the Lync Server 2013 pool.



</div>

Before you migrate response groups, you must have deployed a Lync Server 2013 pool that includes the Response Group application. The Response Group application is installed and activated by default when you deploy Enterprise Voice. You can ensure that the Response Group application is installed by running the **Get-CsService –ApplicationServer** cmdlet.

<div>


> [!NOTE]  
> You can create new Lync Server 2013 response groups in the Lync Server 2013 pool before you migrate your legacy response groups.



</div>

To migrate response groups from a legacy pool to the Lync Server 2013, you run the **Move-CsRgsConfiguration** cmdlet.

<div>


> [!IMPORTANT]  
> The Response Group migration cmdlet moves the Response Group configuration for the entire pool. You cannot select specific groups, queues, or workflows to migrate.



</div>

After you migrate the response groups, you need to use Lync Server Control Panel or Lync Server Management Shell cmdlets to verify that all agent groups, queues, and workflows moved successfully.

When you migrate response groups, the Lync Server 2010 response groups are not removed. When you manage response groups after migration by using either Lync Server Control Panel or Lync Server Management Shell, you can see both the Lync Server 2010 response groups and the Lync Server 2013 response groups. You should apply updates only to the Lync Server 2013 response groups. The Lync Server 2010 response groups are retained only for rollback purposes.

<div>


> [!WARNING]  
> After the migration has been completed and the new response groups have been created, the Lync Server Control Panel and the Lync Server Management Shell will display the Lync Server 2010 and Lync Server 2013 versions of each response group. Do not use Lync Server Control Panel or Lync Server Management Shell to remove the Lync Server 2010 response groups. If you do remove one, the corresponding response group that was created during migration will stop working. The Lync Server 2010 response groups will be removed when you decommission the Lync Server 2010 pool.



</div>

<div>


> [!IMPORTANT]  
> We recommend that you do not remove any data from your previous deployment until you decommission the pool. In addition, we strongly recommend that you export response groups immediately after you migrate. If a Lync Server 2010 response group should get removed, you can then restore your response groups from the backup to get Lync Server 2013 response groups running again.



</div>

Lync Server 2013 introduces a new Response Group feature called **Workflow Type**. **Workflow Type** can be **Managed** or **Unmanaged**. All response groups are migrated with **Workflow Type** set to **Unmanaged** and with an empty Manager list.

When you run the **Move-CsRgsConfiguration** cmdlet, the agent groups, queues, workflows, and audio files remain in the legacy pool for rollback purposes. If you do need to roll back to the legacy pool, however, you need to run the **Move-CsApplicationEndpoint** cmdlet to move contact objects back to the legacy pool.

The following procedure for migrating Response Group configurations assumes that you have a one-to-one relationship between your legacy pools and the Lync Server 2013 pools. If you plan to consolidate or split up pools during your migration and deployment, you need to plan which legacy pool maps to which Lync Server 2013 pool.

<div>

## To migrate Response Group configurations

1.  Log on to the computer with an account that is a member of the RTCUniversalServerAdmins group or has equivalent administrator rights and permissions.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

3.  Run:
    
        Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
    
    For example:
    
        Move-CsRgsConfiguration -Source lync-old.contoso.net -Destination lync-new.contoso.net

4.  After you migrate response groups and agents to the Lync Server 2013 pool, the URL that agents use to sign in and sign out is a Lync Server 2013 URL and is available from the **Tools** menu. Remind agents to update any references, such as bookmarks, to the new URL.

</div>

<div>

## To verify Response Group migration by using Lync Server Control Panel

1.  Log on to the computer with an account that is a member of RTCUniversalReadOnlyAdmins group or is minimally a member of the CsViewOnlyAdministrator role.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation pane, click **Response Groups**.

4.  On the **Workflow** tab, verify that all the workflows in your Lync Server 2010 environment are included in the list.

5.  Click the **Queue** tab, and verify that all the queues in your Lync Server 2010 environment are included in the list.

6.  Click the **Group** tab, and verify that all the agent groups in your Lync Server 2010 environment are included in the list.

</div>

<div>

## To verify Response Group migration by using Lync Server Management Shell

1.  Log on to the computer with an account that is a member of RTCUniversalReadOnlyAdmins group or is minimally a member of the CsViewOnlyAdministrator role.

2.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
    For details about the following cmdlets, run:
    
        Get-Help <cmdlet name> -Detailed

3.  Run:
    
        Get-CsRgsAgentGroup

4.  Verify that all the agent groups in your Lync Server 2010 environment are included in the list.

5.  Run:
    
        Get-CsRgsQueue

6.  Verify that all the queues in your Lync Server 2010 environment are included in the list.

7.  Run:
    
        Get-CsRgsWorkflow

8.  Verify that all the workflows in your Lync Server 2010 environment are included in the list.

</div>

</div>

<span> </span>

</div>

</div>

</div>

