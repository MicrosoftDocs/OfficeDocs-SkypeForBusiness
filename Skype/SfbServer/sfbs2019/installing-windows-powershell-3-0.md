---
title: "Installing Windows PowerShell 3.0 for Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d87bf21e-0a43-41cb-8fdc-626cedec8538
description: "To deploy Lync Server 2013 successfully, you'll need Windows PowerShell 3.0 on each computer that's part of your Lync Server topology."
---

# Installing Windows PowerShell 3.0 for Lync Server 2013
[]
To deploy Lync Server 2013 successfully, you'll need Windows PowerShell 3.0 on each computer that's part of your Lync Server topology.
  
Now, for systems running Windows Server 2012 or Windows Server 2012 R2, you don't need to do anything here, and can go ahead to the next stage of deployment, because PowerShell 3.0 is included with those operating systems.
  
> [!IMPORTANT]
> But for systems running Windows Server 2008 R2 SP1, you'll need to install PowerShell 3.0 as a prerequisite before you install Lync Server 2013, or things won't work. To install PowerShell 3.0, see [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=329800). This is a direct link to the PowerShell 3.0 download page, along with information relating to installing it successfully. 
  
Once you've done the install, or if you just want to check and be sure before continuing with the Lync Server deployment, confirming that PowerShell 3.0 is on a server is pretty straightforward if you do this:
  
1. On the server you want to check, choose **Start**, click **All Programs**, click **Accessories**, click **Windows PowerShell**, and then click **Windows PowerShell**.
    
2. In the Windows PowerShell console, type the following command at the command prompt, and then press ENTER:
    
  ```
  Get-Host | Select-Object Version
  ```

3. If Windows PowerShell 3.0 is installed you'll see output that looks like this:
    
  ```
  Version
  -------
  3.0
  ```


