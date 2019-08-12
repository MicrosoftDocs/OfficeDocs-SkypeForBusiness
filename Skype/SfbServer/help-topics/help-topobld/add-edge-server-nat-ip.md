---
title: "Add Edge Server NAT IP"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddEdgeServerNatIpPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: aa97fd0e-48b9-4a66-b55a-12291641c967
description: "The public IP address is the IP address that is used by network address translation (NAT). The IP address must be publicly routable. This is required because you selected The external IP address of this Edge pool is translated by NAT option on the Select features page of this wizard."
---

# Add Edge Server NAT IP

The public IP address is the IP address that is used by network address translation (NAT). The IP address must be publicly routable. This is required because you selected **The external IP address of this Edge pool is translated by NAT** option on the **Select features** page of this wizard.

> [!NOTE]
> Network address translation (NAT) enables clients or servers on a private network (for example, the 192.168.0.0 range) to communicate with systems on remote networks over the public Internet networks. NAT works by using a single public IP address on an external interface and associating internal IP addresses with the one public IP address. NAT mapping maps an internal address to the external public IP address. The remote system sees only the public address of the source. The remote system responds to the source, and the source refers to the NAT map to determine what internal IP address the response should be returned to.

You can add support for external user access when you deploy your initial topology or afterward. For details about adding Edge Servers to an existing topology, see [Define Your Edge Topology](https://technet.microsoft.com/library/787b23f1-8fa0-4c37-abf2-c516c5dd66f0.aspx) in the Edge Server Deployment documentation.


