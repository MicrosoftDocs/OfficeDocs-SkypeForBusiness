---
title: "Legacy Merge"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.LegacyMergeAddPicPage
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 085fde15-e33a-4d95-8d06-4da1d5d7c770
ROBOTS: NOINDEX, NOFOLLOW
description: "The Web Conferencing external FQDN permits external users to join on-premises meetings. Enter the fully qualified domain name (FQDN) of the web conferencing external interface of the legacy Edge Server."
---

# Legacy Merge

The **Web Conferencing external FQDN** permits external users to join on-premises meetings. Enter the fully qualified domain name (FQDN) of the web conferencing external interface of the legacy Edge Server.

The **External Web Conferencing external port** value of **443** is the default Transmission Control Protocol (TCP) Session Initiation Protocol (SIP) port configured for conferencing clients. If the default value was not used, update the **External Web Conferencing external port** value.

Select the **This Edge pool is used for federation and public IM connectivity** check box if you plan to use this Edge Server for federation. If you have multiple Edge Servers deployed, only one of them will be enabled for federation. If you do not check this box and you decide later that you want to enable federation, you must run the Topology Builder Merge wizard again, as well as publish your topology. For details, see [Phase 4: Merge Topologies](https://technet.microsoft.com/library/81eb5bb2-1fd7-4611-a2aa-eb2393c8abc9.aspx).


