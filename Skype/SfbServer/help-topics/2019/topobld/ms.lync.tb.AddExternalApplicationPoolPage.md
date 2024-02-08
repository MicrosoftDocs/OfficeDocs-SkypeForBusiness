---
ms.date: 03/17/2018
title: "Add Trusted Application Pool FQDN"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.AddExternalApplicationPoolPage
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 5d065268-a694-49a1-b285-9be80a09995c
ROBOTS: NOINDEX, NOFOLLOW
description: "You can define a Trusted Applications pool fully qualified domain name (FQDN)."
---

# Add Trusted Application Pool FQDN
 
To define a Trusted Applications pool fully qualified domain name (FQDN), specify the following:
  
An FQDN of the server or pool of servers that hosts the trusted applications.
  
Select **Multiple computer pool** if you deploy a pool of servers for the trusted applications from load balancing and high availability, or select **Single computer pool** if you don't need load balancing or high availability.
  
> [!IMPORTANT]
> A single Trusted Applications Server cannot be converted to a pool of servers later. If you think you may need a pool in the future, you can deploy a multiple server pool containing a single computer now, and add servers when needed. 
  
For details about Trusted Applications pools, see [New-CsTrustedApplicationPool](/powershell/module/skype/new-cstrustedapplicationpool?view=skype-ps&preserve-view=true).

