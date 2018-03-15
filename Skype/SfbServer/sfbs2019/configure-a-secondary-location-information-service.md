---
title: "Configure a secondary Location Information service in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 083ffbc6-7c18-4141-85f9-8825b62c3d10
description: "Lync Server 2013 provides a web service interface that you can use to point the Location Information service to a Secondary Location Source (SLS) database. The web service interface that connects to the SLS database must conform to Location Information service WSDL. If both a location database and secondary location database are configured, the Location Information service first queries the location database, and if no match is found, sends the location request from the client to the SLS database. If the location exists in the SLS, the Location Information service then sends the location back to the client."
---

# Configure a secondary Location Information service in Lync Server 2013
[]
Lync Server 2013 provides a web service interface that you can use to point the Location Information service to a Secondary Location Source (SLS) database. The web service interface that connects to the SLS database must conform to Location Information service WSDL. If both a location database and secondary location database are configured, the Location Information service first queries the location database, and if no match is found, sends the location request from the client to the SLS database. If the location exists in the SLS, the Location Information service then sends the location back to the client. 
  
For details, see the Lync Server Management Shell documentation for the following cmdlet:
  
- **Set-CsWebServiceConfiguration**
    
### To configure Secondary Location database

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Run the following cmdlet to configure the URL for the location of the secondary location database. 
    
  ```
  Set-CsWebServiceConfiguration -SecondaryLocationSourceURL "<web service url>" 
  ```


