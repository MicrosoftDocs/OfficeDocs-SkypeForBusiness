---
title: 'Lync Server 2013: Modify existing Registrar configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Modify existing Registrar configuration settings
ms:assetid: a8931511-3e66-49ed-a3ec-03bcd61ce1f0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182566(v=OCS.15)
ms:contentKeyID: 48185095
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify existing Registrar configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

You can use the Registrar to configure proxy server authentication protocols. For information about the available protocols, see [Create Registrar configuration settings in Lync Server 2013](lync-server-2013-create-registrar-configuration-settings.md).

<div>


> [!NOTE]  
> We recommend that you enable both Kerberos and NTLM when a server supports authentication for both remote and enterprise clients. The Edge Server and internal servers communicate to ensure that only NTLM authentication is offered to remote clients. If only Kerberos is enabled on these servers, they cannot authenticate remote users. If enterprise users also authenticate against the server, Kerberos is used.



</div>

Follow these steps to modify an existing Registrar.

<div>

## To modify existing registrar configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Security** and then click **Registrar**.

4.  On the **Registrar** page, click a service, click **Edit**, and then click **Show details**.

5.  In **Edit Registrar Setting**, select one or more of the following depending on the capabilities of the clients and support in your environment:
    
      - **Enable Kerberos authentication** to have the servers in the pool issue challenges using Kerberos authentication.
    
      - **Enable NTLM authentication** to have the servers in the pool issue challenges using NTLM.
    
      - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.

6.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

