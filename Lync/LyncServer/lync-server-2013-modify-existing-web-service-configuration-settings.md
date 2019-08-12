---
title: 'Lync Server 2013: Modify existing Web Service configuration settings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Modify existing Web Service configuration settings
ms:assetid: bd9c7aa5-d31c-4fab-b31d-8baae26b1296
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182580(v=OCS.15)
ms:contentKeyID: 48185272
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Modify existing Web Service configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

You can use the **Web Service** page to configure the authentication methods for accessing Lync Server 2013 related web servers and Web Services.

Follow these steps to modify an existing Web Service policy.

<div>

## To modify existing Web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Security** and then click **Web Service**.

4.  On the **Web Service** page, click a configuration, click **Edit**, and then click **Show details**.

5.  In **Edit Web Service Setting**, in **Integrated Windows authentication**, select **Negotiate**, **Integrated Windows authentication**, or **None**.

6.  Select one or more of the following depending on the capabilities of the clients and support in your environment:
    
      - **Enable PIN Authentication** to enable clients to be authenticated using PIN numbers.
    
      - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.
    
      - **Enable certificate chain download** to have servers presented with an authentication certificate download the certificate chain for that certificate.

7.  Click **Commit**.

</div>

<div>

## See Also


[Configuring authentication in the Lync Server 2013 Control Panel](lync-server-2013-configuring-authentication-in-the-lync-server-control-panel.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

