---
title: Decommission your on-premises Skype for Business environment
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
audience: ITPro
f1.keywords:
- NOCSH
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Instructions for how to decommission your on-premises Skype for Business environment."

---

# Decommission your on-premises Skype for Business environment

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

If your organization uses Teams with an on-premises deployment of Skype for Business Server, you can migrate these environments fully to the cloud, and then retire your on-premises deployment of Skype for Business Server. 

> [!NOTE]
> Before decommissioning your on-premises environment, you must [configure hybrid connectivity](configure-hybrid-connectivity.md) between your on-premises deployment and Microsoft 365. After configuring hybrid connectivity, you can migrate users to the cloud, while migrating their meetings from on-premises, and migrating any contacts from Skype for Business Server to Teams. Configuring hybrid connectivity is a required step to migrate users from on-premises to the cloud and to ensure full Teams functionality.

To complete your move from on-premises to the cloud and decommission your on-premises Skype for Business Server environment, you must complete the following steps in the following order:

- **Step 1.** [Move all required users from on-premises to online](decommission-move-on-prem-users.md).

- **Step 2.** [Disable your hybrid configuration](cloud-consolidation-disabling-hybrid.md).

- **Step 3.** [Move hybrid application endpoints from on-premises to online](decommission-move-on-prem-endpoints.md).

- **Step 4.** [Remove your on-premises Skype for Business deployment](decommission-remove-on-prem.md).

