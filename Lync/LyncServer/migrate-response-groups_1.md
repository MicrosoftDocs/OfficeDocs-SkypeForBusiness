---
title: Migrate response groups
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrate response groups
ms:assetid: 5c07bf4b-ad8a-4b83-b970-7d933bb7c4ef
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204931(v=OCS.15)
ms:contentKeyID: 48184250
ms.date: 07/23/2014
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

_**Topic Last Modified:** 2012-10-19_

After your users are moved to Lync Server 2013 pools, you can migrate your response groups. Migrating response groups includes copying agent groups, queues, workflows, and audio files, and moving Response Group contact objects from the legacy deployment to the Lync Server 2013 pool. After you migrate your legacy response groups, calls to the response groups are handled by the Response Group application in the Lync Server 2013 pool. Calls to response groups are no longer handled by the legacy pool.

<div>


> [!NOTE]  
> Although you can migrate response groups before you move all users to the Lync Server 2013 pool, we recommend that you move all users first. In particular, users who are response group agents will not have full functionality of new features until they are moved to the Lync Server 2013 pool.



</div>

Before you migrate response groups, you must have deployed a Lync Server 2013 pool that includes the Response Group application. The Response Group application is installed and activated by default when you deploy Enterprise Voice. You can ensure that the Response Group application is installed by running the **Get-CsService–ApplicationServer** cmdlet.

<div>


> [!NOTE]  
> You can create new Lync Server 2013 response groups in the Lync Server 2013 pool before you migrate your legacy response groups.



</div>

To migrate response groups from a legacy pool to the Lync Server 2013, you run the **Move-CsRgsConfiguration** cmdlet. Before you can run **Move-CsRgsConfiguration**, you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package. Install this application by running OCSWMIBC.msi. You can find OCSWMIBC.msi on the installation media in the Setup folder.

<div>


> [!IMPORTANT]  
> The Response Group migration cmdlet moves the Response Group configuration for the entire pool. You cannot select specific groups, queues, or workflows to migrate.



</div>

After you migrate the response groups, you need to update the URL that formal agents use to sign into and out of their response groups, and use Lync Server Control Panel or Lync Server Management Shell cmdlets to verify that all agent groups, queues, and workflows moved successfully.

<div>


> [!WARNING]  
> When you migrate response groups, the Office Communications Server 2007 R2 response groups are not removed. Do not remove Office Communications Server 2007 R2 response groups. If you remove an Office Communications Server 2007 R2 response group, the response groups in Lync Server 2013 stop working.



</div>

<div>


> [!IMPORTANT]  
> We recommend that you do not remove any data from your previous deployment until you decommission the pool. In addition, we strongly recommend that you export response groups immediately after you migrate. If an Office Communications Server 2007 R2 response group gets removed, you can then restore your response groups from the backup to get Lync Server 2013 response groups running again.



</div>

When you run the **Move-CsRgsConfiguration** cmdlet, the agent groups, queues, workflows, and audio files remain in the legacy pool for rollback purposes. If you do need to roll back to the legacy pool, however, you need to run the **Move-CsApplicationEndpoint** cmdlet to move contact objects back to the legacy pool.

<div>


> [!IMPORTANT]  
> We recommend that you don't delete any response group data from the legacy pool until you decommission the pool.



</div>

The procedure that follows for migrating Response Group configurations assumes that you have a one-to-one relationship between your legacy pools and the Lync Server 2013 pools. If you plan to consolidate or split up pools during your migration and deployment, you need to plan which legacy pool maps to which Lync Server 2013 pool.

<div>

## To Migrate Response Group Configurations

1.  Locate OCSWMIBC.msi in the Setup folder of the installation media and install it.

2.  Log on to the computer with an account that is a member of the RTCUniversalServerAdmins group or has equivalent administrator rights and permissions.

3.  Open the Lync Server Management Shell.

4.  At the command line, type the following:
    
        Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
    
    For example:
    
        Move-CsRgsConfiguration -Source pool01.contoso.net -Destination pool02.contoso.net

5.  If you deployed the Response Group tab for Microsoft Office Communicator 2007 R2 in your Office Communications Server 2007 R2 environment, remove the tab from the Office Communicator 2007 R2 tabs.xml file.
    
    <div>
    

    > [!NOTE]  
    > Formal agents used the Response Group tab to sign in to their response groups before they could receive calls. If you deployed the Response Group tab, you chose the location for the Office Communicator 2007 R2 tabs.xml file when you deployed it.

    
    </div>

6.  Provide users with the updated URL that agents need to sign into and out of their response groups.
    
    <div>
    

    > [!NOTE]  
    > The URL is typically https://webpoolFQDN/RgsClients/Tab.aspx, where webpoolFQDN is the fully qualified domain name (FQDN) of the web pool that is associated with the pool that you just migrated to Lync Server 2013.

    
    </div>
    
    <div>
    

    > [!NOTE]  
    > This step is not required after users upgrade to Lync 2013 because the URL is available from the <STRONG>Tools</STRONG> menu in Lync.

    
    </div>

</div>

<div>

## To Verify Response Group Migration by Using Lync Server Control Panel

1.  Open the Lync Server Control Panel.

2.  In the left navigation pane, click **Response Groups**.

3.  On the **Workflow** tab, verify that all the workflows in your Office Communications Server 2007 R2 environment are included in the list.

4.  Click the **Queue** tab, and verify that all the queues in your Office Communications Server 2007 R2 environment are included in the list.

5.  Click the **Group** tab, and verify that all the agent groups in your Office Communications Server 2007 R2 environment are included in the list.

</div>

<div>

## To Verify Response Group Migration by Using Cmdlets

1.  Open the Lync Server Management Shell.
    
    For details about the following cmdlets, run:
    
        Get-Help <cmdlet name> -Detailed

2.  At the command line, type the following:
    
        Get-CsRgsAgentGroup

3.  Verify that all the agent groups in your Office Communications Server 2007 R2 environment are included in the list.

4.  At the command line, type the following:
    
        Get-CsRgsQueue

5.  Verify that all the queues in your Office Communications Server 2007 R2 environment are included in the list.

6.  At the command line, type the following:
    
        Get-CsRgsWorkflow

7.  Verify that all the workflows in your Office Communications Server 2007 R2 environment are included in the list.

</div>

</div>

<span> </span>

</div>

</div>

</div>

