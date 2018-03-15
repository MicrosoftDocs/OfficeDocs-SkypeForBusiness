---
title: "Create new Web Service configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f3f04d81-8a1f-427f-bd0f-fb659024e096
description: "You can use the Web Service page to configure the authentication methods for accessing Lync Server 2013 related web servers and Web Services."
---

# Create new Web Service configuration settings in Lync Server 2013
[]
You can use the **Web Service** page to configure the authentication methods for accessing Lync Server 2013 related web servers and Web Services. 
  
Follow these steps to create a new Web Service policy.
  
### To create new web service configuration settings

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or assigned to the CsServerAdministrator or CsAdministrator role, log on to any computer that is in the network in which you deployed Lync Server 2013. 
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Security** and then click **Web Service**.
    
4. On the **Web Service** page, click **New**, and then do one of the following:
    
  - To configure the Web Service for a site, click **Site configuration**. In **Select a Site**, click the site to which the Web Service policy will be applied a site and click **OK**.
    
  - To configure the Web Service for a pool, click **Pool configuration**. In **Select a Service**, click the service to which the Web Service policy will be applied and click **OK**. 
    
5. In **New Web Service Setting**, in **Integrated Windows authentication**, select **Negotiate**, **Integrated Windows authentication**, or **None**.
    
6. Select one or more of the following depending on the capabilities of the clients and support in your environment:
    
  - **Enable PIN Authentication** to enable clients to be authenticated using PIN numbers. 
    
  - **Enable certificate authentication** to have the servers in the pool issue certificates to clients. 
    
  - **Enable certificate chain download** to have servers presented with an authentication certificate download the certificate chain for that certificate. 
    
7. Click **Commit**.
    

