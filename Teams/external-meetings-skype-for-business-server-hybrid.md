---
title: Configure external meetings and chat with Skype for Business Server
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.reviewer: nas, pbafna
ms.date: 06/28/2024
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
  - Tier2
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
- ms.teamsadmincenter.externalaccess.overview
- chat-teams-channels-revamp
appliesto: 
  - Microsoft Teams
ms.localizationpriority: Medium
description: Learn how to configure Skype for Business Server for external chat and meetings with other Microsoft 365 organizations and external chat and calls with Skype users.
---

# Configure external meetings and chat with Skype for Business Server

If you're using Skype for Business Server by itself or in a hybrid configuration with Teams in Microsoft 365, you can configure chat and meetings with people in other Microsoft 365 organizations and chat and calling with Skype users.

> [!NOTE]
> Chat with unmanaged Teams users (those not connected to an organization) is not supported for on-premises only organizations. To configure this for Teams in Microsoft 365, see [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md).

## Configure external meetings and chat with other Microsoft 365 organizations

To allow chatting and meetings with other Microsoft 365 organizations, configure your Skype for Business Server environment as follows:
- Ensure federation is enabled in `CsAccessEdgeConfiguration`.
- Ensure federation for the user is enabled through `ExternalAccessPolicy` (either through the global policy, site policy, or user assigned policy).
- If you are not using open federation, ensure the target domain is listed in `AllowedDomains`.

If you are using Microsoft 365 with Skype for Business Server in a hybrid configuration, configure external meetings and chat in Microsoft 365 as described in [Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md). Note that organizations that you're communicating with must also trust your organization.

## Configure external chat and calling with Skype users

To allow chatting and calls with Skype users, configure your Skype for Business Server environment as follows:
- Ensure Skype is enabled as a federated partner.
- Ensure `EnablePublicCloudAccess=true` for the user through `ExternalAccessPolicy` (either via global policy, site policy, or user assigned policy).

If you are using Microsoft 365 with Skype for Business Server in a hybrid configuration, configure external chat and calling with Skype users in Microsoft 365 as described in [Manage external meetings and chat with people and organizations using Microsoft identities](/microsoftteams/trusted-organizations-external-meetings-chat#manage-chat-and-calls-with-skype-users).

## Related topics

[Compare external and guest access](communicate-with-users-from-other-organizations.md#compare-external-access-and-guest-access)

[Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md)
