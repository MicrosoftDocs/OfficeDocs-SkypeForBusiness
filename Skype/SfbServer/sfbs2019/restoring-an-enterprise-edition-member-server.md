---
title: "Restoring an Enterprise Edition member server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d960b19c-2104-4719-b736-0d940f254d42
description: "If a server running one of the following server roles fails, follow the procedure in this topic to restore the server. If multiple servers fail independently, follow the procedure for each server."
---

# Restoring an Enterprise Edition member server in Lync Server 2013
[]
If a server running one of the following server roles fails, follow the procedure in this topic to restore the server. If multiple servers fail independently, follow the procedure for each server.
  
- Front End Server
    
- Mediation Server
    
- Director
    
- Persistent Chat Server
    
- Edge Server
    
> [!TIP]
> We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates. 
  
### To restore a member server

1. Start with a clean or new server that has the same fully qualified domain name (FQDN) as the failed server, install the operating system, and then restore or reenroll the certificates.
    
    > [!NOTE]
    > Follow your organization's server deployment procedures to perform this step. 
  
2. From a user account that is a member of the RTCUniversalServerAdmins group, log on to the server that you are restoring.
    
3. Browse to the Lync Server installation folder or media, and start the Lync Server Deployment Wizard located at \setup\amd64\Setup.exe. 
    
4. Follow the Deployment Wizard to do the following:
    
1. Run **Step 1: Install Local Configuration Store** to install the local configuration files. 
    
2. Run **Step 2: Setup or Remove Lync Server Components** to install the Lync Server server role. 
    
3. Run **Step 3: Request, Install or Assign Certificates** to assign the certificates. 
    
4. Run **Step 4: Start Services** to start services on the server. 
    
    For details about running the Deployment Wizard, see the Deployment documentation for the server role that you are restoring.
    

