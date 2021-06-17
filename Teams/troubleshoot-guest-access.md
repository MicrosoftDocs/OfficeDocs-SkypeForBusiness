---
title: Troubleshoot problems with guest access in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: corbinm
search.appverid: MET150
description: Get help troubleshooting and fixing problems with guest access in Microsoft Teams.
f1.keywords:
- NOCSH
localization_priority: Normal
appliesto: 
- Microsoft Teams
---

# Troubleshoot problems with guest access in Microsoft Teams

- To see whether we know about your problem, check out [Support Teams in your organization](/MicrosoftTeams/troubleshoot/teams-welcome).
- To check for current support issues with guest access in Teams, go to [Teams Troubleshooting](/MicrosoftTeams/troubleshoot/).
- Guests are people outside your organization. If someone is inside your organization (including your employees, onsite contractors, or onsite agents), they can't be added as guests. The same applies to your affiliates.
- Find out about upcoming new or updated guest access features in the [Teams Roadmap](https://aka.ms/teamsroadmap).
- Tell us what you want in [Teams UserVoice](https://aka.ms/TeamsUserVoice).

[!INCLUDE [uservoice-disclaimer-note](includes/uservoice-disclaimer-note.md)]

## If your guests are seeing license errors

Guest access in Teams uses Azure Active Directory (Azure AD) Business to Business (B2B) and its licensing model. Guest access is included with all Microsoft 365 Business Standard, Office 365 Enterprise, and Office 365 Education subscriptions. No additional Microsoft 365 or Office 365 license is necessary.

> [!NOTE]
> Teams must be enabled on a guest's home tenant for guests to be able to sign in and use Teams as a guest on another (resource) tenant.

If you're seeing licensing errors, make sure to read the [Billing model for Azure AD External Identities](/azure/active-directory/external-identities/external-identities-pricing) to determine licensing requirements to meet your needs for guest access in your organization.

- Guest licenses are counted against the inviting organization. Consider this when you calculate the number of licenses you need.
- Licenses are counted against your organization whether the invited guests come from another Microsoft 365 organization or are using their personal email addresses.

## Support for B2B User types

Currently Teams only has support for State 1 and State 2 types of Guest users [as defined by Azure B2B](/azure/active-directory/b2b/user-properties).

## Related topics

[Guest access in Teams](guest-access.md)

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)