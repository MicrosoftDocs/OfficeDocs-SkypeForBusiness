---
title: 'Re-activate server after Security Configuration Wizard closes ports in IIS'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Re-activate server after Security Configuration Wizard closes ports in IIS
ms:assetid: cb8e17cf-f8c1-4099-b63b-c242d656c26a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398851(v=OCS.15)
ms:contentKeyID: 48185644
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Re-activate server after Security Configuration Wizard closes ports in IIS

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

Some Lync Server 2013 roles run Web Services on Internet Information Services (IIS) port 4443. Running the Lync Server Deployment Wizard, Bootstrapper.exe, or using the **Enable-CsComputer** cmdlet creates an exception in the firewall and opens the port. If you then run the Windows Server 2008 R2 Security Configuration Wizard (or other hardening scripts), port 4443 will be blocked, and external clients will not be able to contact Web Services. To reopen the port you can either modify the firewall exception directly or re-activate the server.

<div>

## To re-activate the server by using the Deployment Wizard

1.  On the Lync Server Deployment Wizard page, click **Run** next to **Step 2: Setup or Remove Lync Server Components**.

2.  On **Setup Lync Server components** page, click **Next**.

3.  On the **Executing Commands** page, when the task status is shown as completed, click **Finish**.
    
    <div>
    

    > [!NOTE]
    > You can also use bootstrapper.exe or <STRONG>Enable-CsComputer</STRONG> to re-activate the server.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

