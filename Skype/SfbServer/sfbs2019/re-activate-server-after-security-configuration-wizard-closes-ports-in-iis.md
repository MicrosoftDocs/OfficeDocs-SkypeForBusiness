---
title: "Re-activate server after Security Configuration Wizard closes ports in IIS"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cb8e17cf-f8c1-4099-b63b-c242d656c26a
description: "Some Lync Server 2013 roles run Web Services on Internet Information Services (IIS) port 4443. Running the Lync Server Deployment Wizard, Bootstrapper.exe, or using the Enable-CsComputer cmdlet creates an exception in the firewall and opens the port. If you then run the Windows Server 2008 R2 Security Configuration Wizard (or other hardening scripts), port 4443 will be blocked, and external clients will not be able to contact Web Services. To reopen the port you can either modify the firewall exception directly or re-activate the server."
---

# Re-activate server after Security Configuration Wizard closes ports in IIS
[]
Some Lync Server 2013 roles run Web Services on Internet Information Services (IIS) port 4443. Running the Lync Server Deployment Wizard, Bootstrapper.exe, or using the **Enable-CsComputer** cmdlet creates an exception in the firewall and opens the port. If you then run the Windows Server 2008 R2 Security Configuration Wizard (or other hardening scripts), port 4443 will be blocked, and external clients will not be able to contact Web Services. To reopen the port you can either modify the firewall exception directly or re-activate the server. 
  
### To re-activate the server by using the Deployment Wizard

1. On the Lync Server Deployment Wizard page, click **Run** next to **Step 2: Setup or Remove Lync Server Components**.
    
2. On **Setup Lync Server components** page, click **Next**.
    
3. On the **Executing Commands** page, when the task status is shown as completed, click **Finish**.
    
    > [!NOTE]
    > You can also use bootstrapper.exe or **Enable-CsComputer** to re-activate the server. 
  

