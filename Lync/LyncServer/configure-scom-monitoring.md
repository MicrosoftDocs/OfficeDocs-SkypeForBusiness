---
title: Configure SCOM monitoring
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure SCOM monitoring
ms:assetid: 4003d225-2a33-448c-abd9-571750661140
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688033(v=OCS.15)
ms:contentKeyID: 49733624
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure SCOM monitoring

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-04_

After migrating to Microsoft Lync Server 2013, you must complete a few tasks to configure Lync Server 2013 to work with System Center Operations Manager.

  - Apply Lync Server 2010 updates to a server elected to manage the central discovery logic.

  - Update the central discovery candidate server registry key.

  - Configure your primary System Center Operations Manager management server to override the candidate central discovery node.

Instructions for carrying out each of these tasks are provided below.

**Apply Lync Server 2010 updates to a server elected to manage the central discovery logic.**

1.  Elect a server that has the System Center Operations Manager agent files installed and is configured as a candidate discovery node.

2.  Apply Lync Server 2010 updates to this server. See the topic [Apply Lync Server 2010 updates](apply-lync-server-2010-updates.md).

**Update the central discovery candidate server registry key.**

1.  On the server elected to manage the central discovery logic, open a Windows PowerShell command window.

2.  At the command line, type the following:
    
       ```
        New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health"
       ```
    
       ```
        New-Item -Path "HKLM:\Software\Microsoft\Real-Time Communications\Health\CentralDiscoveryCandidate"
       ```
    
    <div class="">
    

    > [!NOTE]  
    > Whenever you edit the registry, you may experience an error that the command failed if the registry key already exists. If you experience this, you can safely ignore the error.

    
    </div>

**Configure your primary System Center Operations Manager management server to override the candidate central discovery watcher node.**

1.  On a computer where the System Center Operations Manager console has been installed, expand **Management Pack Objects** and then select **Object Discoveries**.

2.  Click **Change Scope...**

3.  From the **Scope Management Pack Objects** page, select **LS Discovery Candidate**.

4.  Override the **LS Discovery Candidate Effective Value** to the name of the candidate server elected in the earlier procedure.

Lastly, to finalize your changes, restart the health service on the System Center Operations Manager Root Management Server.

</div>

<span> </span>

</div>

</div>

</div>

