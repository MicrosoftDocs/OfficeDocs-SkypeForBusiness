---
title: 'Lync Server 2013: Create or modify a new client version policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a new client version policy
ms:assetid: 4be6e449-aa82-4b46-abb1-d31281573a72
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ898476(v=OCS.15)
ms:contentKeyID: 50873756
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a new client version policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

You can use client version policies to specify the versions of clients that are supported in your environment. Using client versioning can help reduce the costs associated with supporting multiple client versions. It can also improve the overall user experience, because when earlier and later versions of clients interact, the available features can be limited by the earlier version of the client. You can create or modify client version policies from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.

<div>

## To create or modify client version policies by using Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Clients**.
    
    <div>
    

    > [!NOTE]  
    > The <STRONG>Client Version Policy</STRONG> tab is selected by default.

    
    </div>

4.  On the **Client Version Policy** page, do one of the following:
    
      - To create a client version policy, click **New**, select **Site policy**, **Pool policy**, or **User policy**, and then click **OK**.
    
      - To modify the global policy or another existing client version policy, select the policy, click **Edit**, and then click **Show details**.

5.  On the **Edit Client Version Policy** page, create or modify rules as described in [Create or modify a new client version policy rule in Lync Server 2013](lync-server-2013-create-or-modify-a-new-client-version-policy-rule.md).

</div>

<div>

## Creating or Modifying Client Version Policies by Using Windows PowerShell Cmdlets

You can create client version policies by using the **New-CsClientVersionPolicy** cmdlet, and modify them by using the **Set-CsClientVersionPolicy** cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To create a new site-scoped client version policy

  - The following command creates a new client version policy applied to the Redmond site. Because no additional parameters are specified, the new policy will use the default client version settings.
    
        New-CsClientVersionPolicy -Identity "site:Redmond"

</div>

<div>

## To create a new per-user client version policy

  - To create a per-user policy, use a command similar to this:
    
        New-CsClientVersionPolicy -Identity "RedmondClientVersionPolicy"

</div>

For details, see the Help topics for the [New-CsClientVersionPolicy](https://docs.microsoft.com/powershell/module/skype/New-CsClientVersionPolicy) cmdlet and the [Set-CsClientVersionPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsClientVersionPolicy) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

