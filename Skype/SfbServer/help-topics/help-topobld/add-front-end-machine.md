---
title: "Add Front End Machine"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddFrontEndMachinePage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e7fe2522-1bd2-416a-9dbb-51cacea9c6e0
description: "Specify the fully qualified domain name (FQDN) of each computer that you want to add as a Front End Server in this pool. After adding a computer to the list, you can update the FQDN of the computer or remove it from the pool at any time prior to publishing the topology. After you publish the topology, changing the FQDN requires deleting the server in Topology Builder and then adding a new server to the pool with the new FQDN. For details about adding a Front End pool to the topology, see Define and Configure a Front End Pool in the Deployment documentation."
---

# Add Front End Machine

Specify the fully qualified domain name (FQDN) of each computer that you want to add as a Front End Server in this pool. After adding a computer to the list, you can update the FQDN of the computer or remove it from the pool at any time prior to publishing the topology. After you publish the topology, changing the FQDN requires deleting the server in Topology Builder and then adding a new server to the pool with the new FQDN. For details about adding a Front End pool to the topology, see [Define and Configure a Front End Pool](https://technet.microsoft.com/library/713fc263-23dd-414a-b001-82932e4fe966.aspx) in the Deployment documentation.

> [!IMPORTANT]
> Note that Topology Builder indicates that you can have up to 20 Front End Servers in a pool. The maximum supported number of servers is 12. You can have up to 20 statefull servers defined in the fabric, of which 12 can be active and online at any one time.


