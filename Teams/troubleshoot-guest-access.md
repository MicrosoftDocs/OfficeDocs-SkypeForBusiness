---
title: Troubleshoot problems with guest access in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
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
appliesto: 
- Microsoft Teams
localization_priority: Normal
---
Troubleshoot problems with guest access in Microsoft Teams
======================================================

> [!IMPORTANT]
> You may have to wait for up to 24 hours for your changes to take effect. 


- To check for current support issues with guest access in Teams, go to [Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/).
- To see whether we know about your problem, check out [Known issues for Microsoft Teams](Known-issues.md).
- Guests are users outside your organization. If someone is inside your organization (including your employees, onsite contractors, or onsite agents), they can't be added as guests. The same applies to your affiliates.
- Find out about upcoming new or updated guest access features in the [Teams Roadmap](https://aka.ms/teamsroadmap).
- Tell us what you want in [Teams UserVoice](https://aka.ms/TeamsUserVoice).

## If your guests are seeing license errors

Guest access in Teams uses Azure Active Directory (Azure AD) Business to Business (B2B) and its licensing model. Guest access is included with all Office 365 Business Premium, Office 365 Enterprise, and Office 365 Education subscriptions. No additional Office 365 license is necessary.

If you’re seeing licensing errors, make sure to read the [Azure Active Directory B2B licensing guidance](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance) to determine licensing requirements to meet your needs for guest access in your organization.


- Guest licenses are counted against the inviting organization. Consider this when you calculate the number of licenses you need.
- Licenses are counted against your organization whether the invited guests come from another Office 365 tenant or are using their personal email addresses.

## Support for B2B User types
Currently Teams only has support for State 1 and State 2 types of Guest users [as defined by Azure B2B](https://docs.microsoft.com/azure/active-directory/b2b/user-properties).

## Related topics

[Guest access in Teams](guest-access.md)


