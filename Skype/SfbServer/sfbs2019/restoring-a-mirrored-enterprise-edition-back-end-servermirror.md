---
title: "Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4b3c8eae-6f1f-4377-b39b-6699e725c517
description: "If you have an Enterprise Edition Back End Server in a mirrored configuration and only the mirror fails, follow the procedures in this section. If both the primary database and mirror fail, see Restoring an Enterprise Edition Back End Server in Lync Server 2013. If only the primary fails, see Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - primary. If the database hosting the Central Management store fails, see Restoring the server hosting the Central Management store in Lync Server 2013. If an Enterprise Edition member server that is not the Back End Server fails, see Restoring an Enterprise Edition member server in Lync Server 2013."
---

# Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - mirror
[]
If you have an Enterprise Edition Back End Server in a mirrored configuration and only the mirror fails, follow the procedures in this section. If both the primary database and mirror fail, see [Restoring an Enterprise Edition Back End Server in Lync Server 2013](restoring-an-enterprise-edition-back-end-server.md). If only the primary fails, see [Restoring a mirrored Enterprise Edition Back End Server in Lync Server 2013 - primary](restoring-a-mirrored-enterprise-edition-back-end-serverprimary.md). If the database hosting the Central Management store fails, see [Restoring the server hosting the Central Management store in Lync Server 2013](restoring-the-server-hosting-the-central-management-store.md). If an Enterprise Edition member server that is not the Back End Server fails, see [Restoring an Enterprise Edition member server in Lync Server 2013](restoring-an-enterprise-edition-member-server.md).
  
We recommend that you take an image copy of the system before you start restoration. You can use this image as a rollback point, in case something goes wrong during restoration. You might want to take the image copy after you install the operating system and SQL Server, and restore or reenroll the certificates.
  
### To restore an Enterprise Edition Back End Server Mirror Database

1. From a user account that is a member of the RTCUniversalServerAdmins group, log on to a Front End Server.
    
2. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
3. Uninstall mirroring. First, type the following cmdlet: 
    
  ```
  Uninstall -CsMirrorDatabase -DatabaseType User -SqlServerFqdn <PrimaryServerFqdn> -SqlInstanceName <SQLInstance> -verbose
  ```

    For example: 
    
  ```
  Uninstall -CsMirrorDatabase -DatabaseType User -SqlServerFqdn server4.contoso.com -SqlInstanceName archinst -verbose
  ```

    Do this for all database types on this server.
    
4. Create a clean or new server that has the same fully qualified domain name (FQDN) (DB1.contoso.com) as the failed computer, install the operating system, and then restore or reenroll the certificates. This server will function as the new mirror.
    
5. From a user account that is a member of the RTCUniversalServerAdmins group, log on to the new server.
    
6. Install SQL Server 2012 or SQL Server 2008 R2, keeping the instance names the same as before the failure.
    
7. From a user account that is a member of the RTCUniversalServerAdmins group, log on to a Front End Server.
    
8. Use Topology Builder to install the mirror database. Perform the following: 
    
  - Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
  - Right-click the Lync Server 2013 node, click **Topology**, and then click **Install Database**.
    
  - Follow the **Install Database** wizard. On the **Create databases** page, select the databases that you want to recreate. 
    
  - Follow the wizard until a prompt of **Create Mirror Database** appears. Select the database that you want to install and complete this process. 
    
    > [!TIP]
    > Instead of running Topology Builder, you can use the **Install-CsMirrorDatabase** cmdlet to configure mirroring. For details, see the Lync Server Management Shell documentation. 
  

