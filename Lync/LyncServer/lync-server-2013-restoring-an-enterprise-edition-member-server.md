---
title: 'Lync Server 2013: Restoring an Enterprise Edition member server'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Restoring an Enterprise Edition member server
ms:assetid: d960b19c-2104-4719-b736-0d940f254d42
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Hh202191(v=OCS.15)
ms:contentKeyID: 51541523
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Restoring an Enterprise Edition member server in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-18_

If a server running one of the following server roles fails, follow the procedure in this topic to restore the server. If multiple servers fail independently, follow the procedure for each server.

  - Front End Server

  - Mediation Server

  - Director

  - Persistent Chat Server

  - Edge Server

<div>


> [!TIP]  
> We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates.



</div>

<div>

## To restore a member server

1.  Start with a clean or new server that has the same fully qualified domain name (FQDN) as the failed server, install the operating system, and then restore or reenroll the certificates.
    
    <div>
    

    > [!NOTE]  
    > Follow your organization's server deployment procedures to perform this step.

    
    </div>

2.  From a user account that is a member of the RTCUniversalServerAdmins group, log on to the server that you are restoring.

3.  Browse to the Lync Server installation folder or media, and start the Lync Server Deployment Wizard located at \\setup\\amd64\\Setup.exe.

4.  Follow the Deployment Wizard to do the following:
    
    1.  Run **Step 1: Install Local Configuration Store** to install the local configuration files.
    
    2.  Run **Step 2: Setup or Remove Lync Server Components** to install the Lync Server server role.
    
    3.  Run **Step 3: Request, Install or Assign Certificates** to assign the certificates.
    
    4.  Run **Step 4: Start Services** to start services on the server.
    
    For details about running the Deployment Wizard, see the Deployment documentation for the server role that you are restoring.

</div>

</div>

<span> </span>

</div>

</div>

</div>

