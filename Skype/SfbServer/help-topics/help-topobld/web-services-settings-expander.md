---
title: "Web Services Settings Expander"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/25/2015
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.WebServicesSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aefc9f51-a171-4a58-be65-7accb470cb2a
description: "From within Topology Builder, you can modify the port settings used for both your internal and external web services. In addition, and if you are deploying Domain Name System (DNS) load balancing, you can use Topology Builder to configure the fully qualified domain name (FQDN) of the pool that resolves to the physical IP addresses of all the servers in that pool."
---

# Web Services Settings Expander
 
From within Topology Builder, you can modify the port settings used for both your internal and external web services. In addition, and if you are deploying Domain Name System (DNS) load balancing, you can use Topology Builder to configure the fully qualified domain name (FQDN) of the pool that resolves to the physical IP addresses of all the servers in that pool.
  
### Editing Web Services Settings

1. Select the appropriate Standard Edition Front End Server or the appropriate Enterprise Edition Front End Pool, and then click **Edit Properties**.
    
2. In the **Edit Properties** dialog box, click the **Web services** tab.
    
    > [!CAUTION]
    > If you have more than one Front End pool or Front End Server, the external Web services FQDN must be unique. For example, if you define the external Web services FQDN of a Front End Server as **pool01.contoso.com**, you cannot use **pool01.contoso.com** for another Front End pool or Front End Server. If you are also deploying Directors, the external Web services FQDN defined for any Director or Director pool must be unique from any other Director or Director pool as well as any Front End pool or Front End Server. If you decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director or a Director pool.
  
3. If you are editing the properties of an Enterprise Edition pool, you have the option to select **Override FQDN**. This option should be selected only if you are using Domain Name System (DNS) load balancing. If you are using DNS load balancing, select **Override FQDN** and then, in the text box, type the FQDN of the pool that resolves to the physical IP addresses of all the servers in that pool. If you are not using DNS load balancing, and if you do not select **Override FQDN**, you cannot change the Internal web services FQDN. The Internal web services FQDN is the URL used by internal users to connect to Skype for Business Server.
    
4. Optionally, enter new HTTP, HTTPS, or HTTP and HTTPS values for the **Listening ports** and the **Published ports**. Listening ports are the ports used by Internet Information Services (IIS) to listen for incoming Session Initiation Protocol (SIP) traffic; published ports are ports configured on a load balancer or reverse proxy server and are also used to listen for incoming SIP traffic. By default, both the HTTP listening port and the HTTP published port are set to port 80; the corresponding HTTPS ports are both set to 443. The default value for the two HTTP published ports is 8080 and the corresponding HTTPS ports are set to 4443.
    
5. Click **OK**.
    
If you modify either the internal FQDN or any of the listening port assignments, you must local setup again on all the servers in the pool in order to have those changes take effect.
  

