---
title: "Repository API for Call Quality Dashboard (CQD) in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d53e990f-1c5f-46d1-9eb1-8396782c2753
description: "Summary: Learn about the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server."
---

# Repository API for Call Quality Dashboard (CQD) in Skype for Business Server
 
**Summary:** Learn about the Repository API for Call Quality Dashboard. Call Quality Dashboard is a tool for Skype for Business Server.
  
The Repository API provides programmatic access for Call Quality Dashboard for Skype for Business Server.
  
## Repository API for Call Quality Dashboard

Repository API offers a data access interface to repository database. The repository allows the contents to be organized in a tree or graph structure such that users can group them in the ways that make sense to the users. The repository supports two general types of users: system user, which is a built-in user representing the repository, and regular users that represent the authorized users of the repository.
  
Repository API consists of three general services: 
  
- [User Service for CQD](user-service.md) - for accessing Users.
    
- [Item Service for Call Quality Dashboard (CQD)](item-service.md) - for accessing Items and the contents stored in Items.
    
- [User Settings Service for Call Quality Dashboard (CQD)](user-settings-service.md) - for accessing User Settings.
    
Call Quality Dashboard uses Repository API to manage the following information: 
  
- **User** - representation of Users who have access to the repository.
    
- **Report** - contains a list of Queries, stored as a content in repository items.
    
- **Query** - used to retrieve data from Data API, stored as a content in repository items.
    
- **User Setting** - describes an optional application behavior for the user.
    
  **Cross-Origin Resource Sharing (CORS) Support for Repository API**
  
Repository API supports Cross-Origin Resource Sharing (CORS). CORS is an HTTP feature that enables a web application running under one domain to access resources in another domain. Web browsers implement a security restriction known as [Same-Origin Policy](https://www.w3.org/Security/wiki/Same_Origin_Policy) same-origin policy that prevents a web page from calling APIs in a different domain. CORS provides a secure way to allow one domain (the origin domain) to call APIs in another domain. See the [CORS specification](https://www.w3.org/TR/cors/) for details on CORS.
  
 **Enabling CORS for Repository API**
  
 The following is an excerpt of Repository API web.config, showing two domains listed in corsTrustedOrigin application settings. All requests made by the scripts loaded from these servers are trusted by Repository API.
  
Remember to include the exact protocol, host name, and port (if any). Do not to put any forward slash character (/) at the end. Multiple entries can be specified by separating with commas.
  
```
<repositoryConfiguration>
    <service corsTrustedOrigin="https://<trusted-server>,http://<another-trusted-domain>:8080"" />
    <diagnostics eventLevel="Verbose" systemLoggedEventLevel="Error">
      <traceLog enabled="true" fileName="repository_trace.log" />
    </diagnostics>
 </repositoryConfiguration>
```


