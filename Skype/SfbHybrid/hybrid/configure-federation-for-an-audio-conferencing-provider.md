---
title: "Configure federation for an audio conferencing provider in your hybrid deployment"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
ms.custom:
description: "Summary: Learn how to configure federation for an audio conferencing provider in Skype for Business Online."
---

# Configure federation for an audio conferencing provider in your hybrid deployment

**Summary:** Learn how to configure federation for an audio conferencing provider in Skype for Business Online.

If you want to use an Audio Conferencing Provider (ACP) in your hybrid deployment (on-premises with online), you need to configure federation between your on-premises deployment and the ACP partner as an Allowed Partner Server. You can configure federation by adding the ACP partner domain and Edge server (this may also be called the Access Proxy) to the Federated Domains list for your on-premises deployment. Your ACP partner then needs to add the FQDN of your on-premises Edge Server pool to their allowed federated domains list. Contact your ACP provider for additional details. Your ACP partner then needs to add the FQDN of your on-premises Edge Server pool to their allowed federated domains list.

- **Adding the ACP Domain and Edge Server as an Allowed Federated Domain**

    To add the ACP domain as an Allowed Partner Server (allowed Federated Domain), follow the steps in [Configure Support for Allowed External Domains](https://technet.microsoft.com/library/3ee6e175-986d-4c33-b03a-b9f93083dca6.aspx). For the Edge Server, add the FQDN of the ACP partner's Edge Server. You may need to contact your ACP partner to obtain the FQDN for their Edge Server, which may also be referred to by your ACP as their Access Proxy.

- **Providing the FQDN of your Edge Server Pool to the ACP partner**

    The ACP partner needs to configure federation to add your on-premises domain as an Allowed Partner Server by adding the FQDN of your Edge Server pool as an allowed Federated domain.


