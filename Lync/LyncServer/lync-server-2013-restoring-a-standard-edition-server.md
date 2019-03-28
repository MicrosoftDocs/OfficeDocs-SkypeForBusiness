---
title: 'Lync Server 2013: Restoring a Standard Edition server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Restoring a Standard Edition server
ms:assetid: d1845663-3138-4fd6-b3e7-337e294d40d8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202190(v=OCS.15)
ms:contentKeyID: 51541519
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring a Standard Edition server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

If a Standard Edition server that does not host the Central Management store fails, follow the procedures in this section. If the Central Management store fails, see [Restoring the server hosting the Central Management store in Lync Server 2013](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md).

<div>


> [!TIP]  
> We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or re-enroll the certificates.



</div>

<div>

## To restore a Standard Edition server

1.  Start with a clean or new server that has the same fully qualified domain name (FQDN) as the failed computer, install the operating system, and then restore or reenroll the certificates.
    
    <div>
    

    > [!NOTE]  
    > Follow your organization's server deployment procedures to perform this step.

    
    </div>

2.  From a user account that is a member of the RTCUniversalServerAdmins group and the Local Administrators group, log on to the server that you are restoring.

3.  Restore the File Store by copying the appropriate File Store from $Backup to the File Store location on the server and share the folder.
    
    <div>
    

    > [!IMPORTANT]  
    > The path and file name for the restored File Store should be exactly the same as the backed up File Store so that components that use the files can access them.

    
    </div>

4.  Run Topology Builder:
    
    1.  Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
    2.  Click **Download Topology from existing deployment**, and then click **OK**.
    
    3.  Select the topology, and then click **Save**. Click **Yes** to confirm your selection.

5.  Browse to the Lync Server installation folder or media, and then start the Lync Server Deployment Wizard located at \\setup\\amd64\\Setup.exe. Use the Lync Server Deployment Wizard to do the following:
    
    1.  Run **Step 1: Install Local Configuration Store** to install the local configuration files.
    
    2.  Run **Step 2: Setup or Remove Lync Server Components** to install the Lync Server server roles.
    
    3.  Run **Step 3: Request, Install or Assign Certificates** to assign the certificates.
    
    4.  Run **Step 4: Start Services** to start services on the server.
    
    For details about running the Deployment Wizard, see the Deployment documentation for the server role you are restoring.

6.  Restore user data by performing the following:
    
    1.  Copy ExportedUserData.zip from $Backup\\ to a local directory.
    
    2.  Before you restore the user data, you must stop Lync services. To do so, type:
        
            Stop-CsWindowsService
    
    3.  To restore the user data, at the command line, type:
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        For example:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    4.  Restart Lync services by typing:
        
            Start-CsWindowsService

7.  If you deployed Response Group on this Standard Edition server, restore the Response Group configuration data. For details, see [Restoring Response Group settings in Lync Server 2013](lync-server-2013-restoring-response-group-settings.md).

8.  If you deployed Persistent Chat on this Standard Edition server, restore the Persistent Chat database (mgc.mdf).
    
    If you used SQL Server Backup to back up the Persistent Chat database, use SQL Server restore procedures to restore it.
    
    If you used the Export-CsPersistentChatData cmdlet to back it up, use the Import-CsPersistentChatData to restore it.

</div>

</div>

<span> </span>

</div>

</div>

</div>

