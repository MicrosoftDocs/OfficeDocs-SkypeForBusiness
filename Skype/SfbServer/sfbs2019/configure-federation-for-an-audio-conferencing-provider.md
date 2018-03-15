---
title: "Configure federation for an audio conferencing provider in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 08dedcce-0d3f-45da-8282-cf2634a41665
description: "If you want to use an Audio Conferencing Provider (ACP) in your hybrid deployment (Lync Server on-premises with Lync Online), you need to configure federation between your on-premises Lync deployment and the ACP partner as an Allowed Partner Server. You can configure federation by adding the ACP partner domain and Edge server (this may also be called the Access Proxy) to the Federated Domains list for your on-premises deployment. Your ACP partner then needs to add the FQDN of your on-premises Edge Server pool to their allowed federated domains list. Contact your ACP provider for additional detailsYour ACP partner then needs to add the FQDN of your on-premises Edge Server pool to their allowed federated domains list."
---

# Configure federation for an audio conferencing provider in Lync Server 2013
[]
If you want to use an Audio Conferencing Provider (ACP) in your hybrid deployment (Lync Server on-premises with Lync Online), you need to configure federation between your on-premises Lync deployment and the ACP partner as an Allowed Partner Server. You can configure federation by adding the ACP partner domain and Edge server (this may also be called the Access Proxy) to the Federated Domains list for your on-premises deployment. Your ACP partner then needs to add the FQDN of your on-premises Edge Server pool to their allowed federated domains list. Contact your ACP provider for additional detailsYour ACP partner then needs to add the FQDN of your on-premises Edge Server pool to their allowed federated domains list.
  
- **Adding the ACP Domain and Edge Server as an Allowed Federated Domain**
    
    To add the ACP domain as an Allowed Partner Server (allowed Federated Domain), follow the steps in [Configure support for allowed external domains in Lync Server 2013](configure-support-for-allowed-external-domains.md). For the Edge Server, add the FQDN of the ACP partner's Edge Server. You may need to contact your ACP partner to obtain the FQDN for their Edge Server, which may also be referred to by your ACP as their Access Proxy.
    
- **Provide the FQDN of your Edge Server Pool to the ACP partner**
    
    The ACP partner needs to configure federation to add your on-premises domain as an Allowed Partner Server by adding the FQDN of your Edge Server pool as an allowed Federated domain.
    

