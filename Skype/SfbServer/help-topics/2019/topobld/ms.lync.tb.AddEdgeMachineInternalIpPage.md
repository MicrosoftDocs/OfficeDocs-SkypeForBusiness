---
title: "Add Edge Machine Internal IP"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.AddEdgeMachineInternalIpPage
ms.prod: skype-for-business-itpro
ms.localizationpriority: medium
ms.assetid: 34717d03-5ece-4be3-9d05-25497250dc16
ROBOTS: NOINDEX, NOFOLLOW
description: "Use this page to specify the internal IP address and internal fully qualified domain name (FQDN) for the Edge Server."
---

# Add Edge Machine Internal IP

Use this page to specify the internal IP address and internal fully qualified domain name (FQDN) for the Edge Server.

The FQDN that you specify must be identical to the computer name configured on the server. By default, the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. So, you must configure a Domain Name System (DNS) suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. For details about adding a DNS suffix to a computer name, see [Configure DNS for Edge Support](/previous-versions/office/lync-server-2013/lync-server-2013-configure-dns-for-edge-support)