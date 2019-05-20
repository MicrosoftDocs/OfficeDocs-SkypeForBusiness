---
title: "Add Edge Machine Internal IP 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddEdgeMachineInternalIpPage2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 31b0ac1d-f320-4677-bd0f-b4b0dc84a6a2
description: "Use this page to specify the internal IP address and the internal fully qualified domain name (FQDN) for the Edge Server."
---

# Add Edge Machine Internal IP 2010

Use this page to specify the internal IP address and the internal fully qualified domain name (FQDN) for the Edge Server.

- In **Internal IPv4 address**, type the IP address of the Edge Server that you want to add to the pool.

- In **Internal FQDN**, type the fully qualified domain name (FQDN) of the Edge Server that you want to add to the pool.

The FQDN that you specify must be identical to the computer name that is configured on the server. By default, the computer name of a computer that is not joined to a domain is a short name, not an FQDN. Topology Builder uses FQDNs, not short names. So, you must configure a Domain Name System (DNS) suffix on the name of the computer to be deployed as an Edge Server that is not joined to a domain. For details about adding a DNS suffix to a computer name, see [Configure DNS for Edge Support](https://technet.microsoft.com/library/955493e6-aa29-424d-bb81-1ef87b3b15e3.aspx)


