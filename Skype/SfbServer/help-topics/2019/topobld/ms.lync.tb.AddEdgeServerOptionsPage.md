---
title: "Add Edge Server Options"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.AddEdgeServerOptionsPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 2405f227-4297-40d0-a117-55427a9e4052
ROBOTS: NOINDEX, NOFOLLOW
description: "Select each feature that you want to enable for the Edge pool. By default, the Edge pool supports remote users in your organization who sign in to from outside the firewall by using a virtual private network (VPN). You also have the following Edge pool feature options:"
---

# Add Edge Server Options

Select each feature that you want to enable for the Edge pool. By default, the Edge pool supports remote users in your organization who sign in to from outside the firewall by using a virtual private network (VPN). You also have the following Edge pool feature options:

- Use of a single fully qualified domain name (FQDN) and IP address for all edge services, including the Access Edge service, Web Conferencing Edge service, and A/V Edge service. If you do not select the option to use a single FQDN and IP address, you will need to specify a separate FQDN and IP address for each of these three Edge services as part of the deployment process. For details about the Edge services, see [Components Required for External User Access](https://technet.microsoft.com/library/2d0f9817-14e7-4109-95dc-62420e3c29e2.aspx) in the Planning documentation.

    > [!NOTE]
    > If you select this option, you must specify a different port number for each of the Edge services (recommended default port settings: 444 for Access Edge service, 8057 for Web Conferencing Edge service, and 443 for A/V Edge service). Selecting this option can help prevent potential connectivity issues, and simplify the configuration because you can then enter one FQDN that is used for all three services.

- Support for federation. Select this option if you want to support communication between internal users and users in trusted domains outside your organization, including any users of a supported public instant messaging (IM) provider. If you select this option, you will need to configure support for the specific federated domains and public IM connectivity service providers that you want to support. For details about configuring support for federation and other types of external user access, see [Configuring Support for External User Access](https://technet.microsoft.com/library/f8424f8c-f965-4414-8485-30f07e10214a.aspx) in the Edge Server Deployment documentation.

    > [!NOTE]
    > Only one Front End pool or Standard Edge Server in your organization may be published externally for federation. All access by federated users, including public IM users, go through the same Edge pool or single Edge Server. For instance, if your deployment includes an Edge pool or single Edge Server deployed in New York and one deployed in London and you enable federation support on the New York Edge pool or single Edge Server, signal traffic for federated users will go through the New York Edge pool or single Edge Server. This is true even for communications with London users, although a London internal user calling a London federated user uses the London pool or Edge Server for A/V traffic.

- Enable XMPP federation. Select this option if you want to support communication between internal users and trusted XMPP partners.

You can add support for external user access when you deploy your initial topology or afterward. For details about adding Edge Servers to an existing topology, see [Define Your Edge Topology](https://technet.microsoft.com/library/787b23f1-8fa0-4c37-abf2-c516c5dd66f0.aspx) in the Edge Server Deployment documentation.


