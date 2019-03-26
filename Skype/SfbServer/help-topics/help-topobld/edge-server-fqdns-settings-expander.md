---
title: "Edge Server FQDNs Settings Expander"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/25/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.EdgeFqdnsSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 9e4e9445-0147-4dd6-84f0-b41de142b332
description: "To edit or specify External Settings for the Edge Servers, you first must determine if you will use separate IP addresses for Session Initiation Protocol (SIP) access, the Web Conferencing Edge service, and the Audio/Video Edge service."
---

# Edge Server FQDNs Settings Expander

To edit or specify **External Settings** for the Edge Servers, you first must determine if you will use separate IP addresses for Session Initiation Protocol (SIP) access, the Web Conferencing Edge service, and the Audio/Video Edge service.

If you intend to use separate IP addresses for each, select the check box **Enable separate FQDN and IP address for Web conferencing and A/V**. Each service must have a corresponding Domain Name System (DNS) host (A) record created for it.

For each of the external-facing services, specify a fully qualified domain name (FQDN) and an associated port. For example, for **SIP Access**, you might use sip.contoso.com with an associated port of 5061.

> [!IMPORTANT]
> If you select separate FQDNs for each of the external-facing services, each service must have a unique port value associated with it. By default, SIP is on port 5061/TLS, the Web Conferencing Edge service is on port 444/TLS, and the A/V Conferencing Edge service is on port 443/TLS. If you make changes to any of these settings, including using separate FQDN and IP addresses or ports, you must update all other services that will rely on the initially configured values.

If you determine that your organization will use a single FQDN and IP address for the external-facing services, clear the **Enable separate FQDN and IP address for Web conferencing and A/V** check box. You can then edit the **SIP Access** pool FQDN and port values, if necessary.

> [!IMPORTANT]
> If you make changes to any of these settings, including using separate FQDN and IP addresses or ports, you must update all other services that will rely on the initially configured values.

For details about defining and configuring the settings for the Edge services, see [Define Your Edge Topology](https://technet.microsoft.com/library/787b23f1-8fa0-4c37-abf2-c516c5dd66f0.aspx).


