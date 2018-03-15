---
title: "Configure an SNMP application in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c4b4a736-3b2e-45b9-a965-19d22161ad57
description: "Lync Server 2013 includes a standard web service interface that you can use to connect the Location Information service to Simple Network Management Protocol (SNMP) applications that match MAC addresses with port and switch information."
---

# Configure an SNMP application in Lync Server 2013
[]
Lync Server 2013 includes a standard web service interface that you can use to connect the Location Information service to Simple Network Management Protocol (SNMP) applications that match MAC addresses with port and switch information. 
  
If an SNMP application is installed and the Location Information service fails to find a match in the location database, the Location Information service automatically queries the application by using the MAC address provided by the client. The Location Information service then uses the port and switch information returned by the SNMP application to query the location database again.
  
For details, see [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md).
  
> [!NOTE]
> MAC addresses are not available on computers running Windows 8. 
  
### To configure the SNMP application URL

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlet to configure the URL for the SNMP application. 
    
  ```
  Set-CsWebServiceConfiguration -MACResolverUrl "<SNMP application url>" 
  ```


