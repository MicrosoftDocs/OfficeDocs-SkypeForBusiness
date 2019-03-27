---
title: 'Lync Server 2013: Create new Web Service configuration settings'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create new Web Service configuration settings
ms:assetid: f3f04d81-8a1f-427f-bd0f-fb659024e096
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182605(v=OCS.15)
ms:contentKeyID: 48185801
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create new Web Service configuration settings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

You can use the **Web Service** page to configure the authentication methods for accessing Lync Server 2013 related web servers and Web Services.

Follow these steps to create a new Web Service policy.

<div>

## To create new web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Security** and then click **Web Service**.

4.  On the **Web Service** page, click **New**, and then do one of the following:
    
      - To configure the Web Service for a site, click **Site configuration**. In **Select a Site**, click the site to which the Web Service policy will be applied a site and click **OK**.
    
      - To configure the Web Service for a pool, click **Pool configuration**. In **Select a Service**, click the service to which the Web Service policy will be applied and click **OK**.

5.  In **New Web Service Setting**, in **Integrated Windows authentication**, select **Negotiate**, **Integrated Windows authentication**, or **None**.

6.  Select one or more of the following depending on the capabilities of the clients and support in your environment:
    
      - **Enable PIN Authentication** to enable clients to be authenticated using PIN numbers.
    
      - **Enable certificate authentication** to have the servers in the pool issue certificates to clients.
    
      - **Enable certificate chain download** to have servers presented with an authentication certificate download the certificate chain for that certificate.

7.  Click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

