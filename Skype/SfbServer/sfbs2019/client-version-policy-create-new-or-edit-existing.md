---
title: "Client Version Policy Create New or Edit Existing"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientCVPolicyEdit
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e32c6712-6dc9-4de9-8d74-9fdccf3de1ba
description: "You can specify the version of clients that are supported in your environment. When two clients that are running different versions interact, the features that are available to either client can be limited by the capabilities of the other client. To make the greatest use of features included in Lync Server 2013 and to improve the overall user experience, you can use the client version filter to restrict the client versions that are used in your environment. By using the client version filter, you can also help reduce costs associated with supporting multiple client versions."
---

# Client Version Policy: Create New or Edit Existing
[]
You can specify the version of clients that are supported in your environment. When two clients that are running different versions interact, the features that are available to either client can be limited by the capabilities of the other client. To make the greatest use of features included in Lync Server 2013 and to improve the overall user experience, you can use the client version filter to restrict the client versions that are used in your environment. By using the client version filter, you can also help reduce costs associated with supporting multiple client versions.
  
> [!IMPORTANT]
> Filters are listed in order of precedence. For example, if you have a filter that allows clients running version 1.5 to connect, followed by a filter that blocks clients running a version earlier than 2.0, the first filter takes precedence, and clients running version 1.5 are allowed to connect. 
  
## Tasks you can perform

You can perform the following tasks on the **New Client Version Policy** or **Edit Client Version Policy** page: 
  
- Add or modify the name or description of the client version policy.
    
- Add or modify client version rules for the client version policy.
    
## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.
  
- **Scope** Identifies the scope (Site, Pool, or User) of the client version policy. 
    
- **Name** You can add or modify the name of the client version policy. 
    
- **Description** You can add a description to help in identifying the policy in the list on the Client Version Policy page. 
    
- **New** You can add a new client version rule to the policy. 
    
- **Show details** This option opens a dialog box in which you can change the options for a client version rule. 
    
- **Remove** This option removes the selected client version rule from the policy. 
    
- **Up and down arrows** This option moves the selected client version rule up or down in priority. Rules are processed in the order listed. 
    
For details about interoperability among clients and client versions, see [Client interoperability in Lync 2013](client-interoperability-in-lync-2013.md) in the Planning documentation. For details about working with client version policies, see [Specifying the client applications that can be used to log on to Lync Server 2013](specifying-the-client-applications-that-can-be-used-to-log-on-to-lync-server-201.md) in the Operations documentation. 
  

