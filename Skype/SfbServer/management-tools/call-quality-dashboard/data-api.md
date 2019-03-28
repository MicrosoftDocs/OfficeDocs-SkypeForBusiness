---
title: "Data API for Call Quality Dashboard (CQD) in Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 25c2450a-f7b3-4dd2-987d-64f4246dd019
description: "Summary: Learn about the Rata API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Data API for Call Quality Dashboard (CQD) in Skype for Business Server
 
**Summary:** Learn about the Rata API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Data API provides programmatic access for Call Quality Dashboard for Skype for Business Server.
  
## Data API for Call Quality Dashboard

The Data API offers a query interface to the QoE Cube. The Data API is a REST API for working with multi-dimensional database that provides aggregated QoE metrics based on specified dimensions and filters.
  
The REST operations are included in the following table.
  

|**Operation**|**Description**|
|:-----|:-----|
|[Get Cube](get-cube.md) <br/> |Get the list of available dimensions and measurements.  <br/> |
|[Get Dimension Members](get-dimension-members.md) <br/> |Get Dimension Members operation returns the list of members of a specific dimension. It also give the ability to filter the member list and get a subset, to reduce the wire transfer cost.  <br/> |
|[Run Query](run-query.md) <br/> |Run Query operation provides the ability to run a query on the cube based on specified dimensions, measurements, and filters and return back the data.  <br/> |
|[Clear Cache](clear-cache.md) <br/> |Clear Cache operation deletes the cache on server for queries and data. This will reset the cache and we will get fresh data from QoE Cube afterward for new requests.  <br/> |
|[Get Integration Log](get-integration-log.md) <br/> |Get Integration Log operation returns a list of log entries describing the activities in QoE Cube processing.  <br/> |
|[Get Last Integration Data](get-last-integration-data.md) <br/> |Get the last integration data from the cube.  <br/> |
   
 **Cross-Origin Resource Sharing (CORS) Support for Data API**
  
Data API supports Cross-Origin Resource Sharing (CORS). CORS is an HTTP feature that enables a web application running under one domain to access resources in another domain. Web browsers implement a security restriction known as [Same-Origin Policy](https://www.w3.org/Security/wiki/Same_Origin_Policy) same-origin policy that prevents a web page from calling APIs in a different domain. CORS provides a secure way to allow one domain (the origin domain) to call APIs in another domain. See the [CORS specification](https://www.w3.org/TR/cors/) for details on CORS.
  
 **Enabling CORS for Data API**
  
 The following is an excerpt of Data API web.config, showing two domains listed in corsTrustedOrigin application settings. All requests made by the scripts loaded from these servers are trusted by Data API.
  
Remember to include the exact protocol, host name, and port (if any). Do not to put any forward slash character (/) at the end. Multiple entries can be specified by separating with commas.
  
```
<configuration>
  <appSettings>
    <add key="corsTrustedOrigin" value="https://<trusted-server>,http://<another-trusted-domain>:8080" /> <!-- Domains which are trusted to get the data -->
    <add key="QoEDataLib.DebugMode" value="True" /> <!-- Setting this to True, allows seeing of the detail logs in status page -->
…  </appSettings>
</configuration>
```


