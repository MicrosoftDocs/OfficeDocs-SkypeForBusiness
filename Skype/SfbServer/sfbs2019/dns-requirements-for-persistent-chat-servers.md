---
title: "DNS requirements for Persistent Chat Servers in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f7531374-d7ed-4b63-ae81-02294cb4496a
description: "This section describes the Domain Name System (DNS) records that are required for deployment of Persistent Chat Servers."
---

# DNS requirements for Persistent Chat Servers in Lync Server 2013
[]
This section describes the Domain Name System (DNS) records that are required for deployment of Persistent Chat Servers.
  
## DNS Records for Persistent Chat Servers

The following table specifies DNS requirements for Persistent Chat Server deployment.
  
**DNS Requirements for a Persistent Chat Server**

|**Deployment scenario**|**DNS requirement**|
|:-----|:-----|
|One Persistent Chat Server  <br/> |An internal A record that resolves the fully qualified domain name (FQDN) of the server to its IP address.  <br/> |
|Persistent Chat pool  <br/> |An internal A record that resolves the fully qualified domain name (FQDN) of the servers to its IP address.  <br/> **Example** <br/> PersistentChatServer01.contoso.com 10.10.10.1  <br/> PersistentChatServer02.contoso.com 10.10.10.2  <br/> An internal A record that resolves the fully qualified domain name (FQDN) of the servers to its IP address.  <br/> **Example** <br/> PersistentChatPool.contoso.com 10.10.10.1  <br/> PersistentChatPool.contoso.com 10.10.10.2  <br/> |
   

