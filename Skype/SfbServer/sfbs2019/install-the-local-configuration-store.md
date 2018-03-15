---
title: "Install the Local Configuration store in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b563030d-d338-411f-9611-28d5eb4b3238
description: "Before following these steps, make sure you're logged onto the server with a domain user account that's both a local administrator and a member of the RTCUniversalReadOnlyAdmin group."
---

# Install the Local Configuration store in Lync Server 2013
[]
Before following these steps, make sure you're logged onto the server with a domain user account that's both a local administrator and a member of the RTCUniversalReadOnlyAdmin group.
  
To be able to do anything with the Lync Server Deployment Wizard, we need the Local Configuration store to exist on a server. The Local Configuration store is a read-only copy of the Central Management store, which gets created after the local installation of SQL Server Express. The Central Management store itself is added to the existing SQL Server database installed on the Standard Edition server or SQL Server Express-based database.
  
> [!IMPORTANT]
> If you haven't run Lync Server 2013 setup on this server before, you'll be prompted for a drive and path to install Lync Server 2013 to. This will let you install to a drive other than the system drive, if your organization requires it, or if you have space concerns. You can just change the installation location path for the Lync Server files in the Setup dialog box to a new, available drive. If you install the Setup files to this path, including OCSCore.msi, the rest of the Lync Server 2013 files will deploy there as well. 
  
### To install the Local Configuration store

1. From your installation media, browse to \setup\amd64\Setup.exe, and then click **OK**.
    
2. If you're prompted to install the Microsoft Visual C++ 2012 Redistributable, click **Yes**.
    
3. On the **Lync Server 2013 Installation Location** page, click **OK**.
    
4. On the **End User License Agreement** page, review the license terms, you'll need to select **I accept the terms in the license agreement**, and then click **OK** to be able to continue. 
    
5. On the Deployment Wizard page, click **Install or Update Lync Server System**.
    
6. On the **Lync Server 2013** page, next to **Step1: Install Local Configuration Store**, click **Run**.
    
7. On the **Install Local Configuration Store** page, make sure that the **Retrieve directly from the Central Management store** option is selected, and then click **Next**.
    
8. When the local server configuration installation is complete, you should click **Finish**.
    

