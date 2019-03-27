---
title: 'Lync Server 2013: Create Registrar configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create Registrar configuration settings
ms:assetid: eddfbdd2-cfd0-4c03-986e-443d6728db7d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182601(v=OCS.15)
ms:contentKeyID: 48185758
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create Registrar configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-17_

You can use the Registrar to configure proxy server authentication methods. The authentication protocol you specify determines which type of challenges the servers in the pool issue to clients. The available protocols are:

  - **Kerberos**   This is the strongest password-based authentication scheme available to clients, but it is normally available only to enterprise clients because it requires client connection to a Key Distribution Center (Kerberos domain controller). This setting is appropriate if the server authenticates only enterprise clients.

  - **NTLM**   This is the password-based authentication available to clients that use a challenge-response hashing scheme on the password. This is the only form of authentication available to clients without connectivity to a Key Distribution Center (Kerberos domain controller), such as remote users. If a server authenticates only remote users, you should choose NTLM.

  - **Certificate authentication**   This is the new authentication method when the server needs to obtain certificates from Lync Phone Edition clients, common area phones, Lync 2013 and the Lync Windows Store app. On Lync Phone Edition clients, after a user signs in and is successfully authenticated by providing a personal identification number (PIN), Lync Server 2013 then provisions the SIP URI to the phone and provisions a Lync Server signed certificate or a user certificate that identifies Joe (Ex: SN=joe@contoso.com ) to the phone. This certificate is used for authenticating with the Registrar and Web Services.

<div>


> [!NOTE]  
> We recommend that you enable both Kerberos and NTLM when a server supports authentication for both remote and enterprise clients. The Edge Server and internal servers communicate to ensure that only NTLM authentication is offered to remote clients. If only Kerberos is enabled on these servers, they cannot authenticate remote users. If enterprise users also authenticate against the server, Kerberos is used.<BR>If you will use Lync Windows Store app clients, you must enable certificate authentication.



</div>

Follow these steps to create a new Registrar.

<div>

## To create new Registrar configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Security** and then click **Registrar**.

4.  On the **Registrar** page, click **New**

5.  In **Select a Service**, click the service to which the Registrar is to be applied and then click **OK**.

6.  In **New Registrar Setting**, select one or more of the following depending on the capabilities of the clients and support in your environment:
    
      - **Enable Kerberos authentication** to have the servers in the pool issue challenges using Kerberos authentication.
    
      - **Enable NTLM authentication** to have the servers in the pool issue challenges using NTLM.
    
      - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.

7.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

