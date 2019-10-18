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

I'm compiling stuff here - to sort out later.

> [!IMPORTANT]
> You may have to wait for up to 24 hours for your changes to take effect. 


To check for current support issues with guest access in Teams, go to [Teams Troubleshooting](https://docs.microsoft.com/MicrosoftTeams/troubleshoot/).

Where does this belong? (Per Corbin, this is out of date. He'll figure out where we should link instead and let me know.)
https://techcommunity.microsoft.com/t5/Microsoft-Teams/Guest-Access-Troubleshooting-Guide/m-p/119797?attachment-id=3063

Removed from guest-access:

- If you’re having trouble with guest access, check out [Known issues for Microsoft Teams](Known-issues.md).
- Find out about upcoming new or updated features in the [Teams Roadmap](https://aka.ms/teamsroadmap).
- Tell us what you want in  [Teams UserVoice](https://aka.ms/TeamsUserVoice).
- Share your experience in the Comments section below.

Removed from GA checklist:
## If your guests are seeing license errors

Guest access in Microsoft Teams uses Azure Active Directory (Azure AD) Business to Business (B2B) and its licensing model. If you’re seeing licensing errors, make sure to read the [B2B licensing guidance](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance) to understand the licensing requirements your organization has so that your users are able to invite guests to your organization.

A few things to remember:

- Guests are users outside your organization. Your employees, onsite contractors, onsite agents, and so on can't be added as guests. The same applies to your affiliates.
- Guest licenses are counted against the inviting organization. Consider this when you calculate the number of licenses you need.
- Licenses are counted against your organization whether the invited guests come from another Office 365 tenant or are using their personal email addresses.

## Related topics

[Guest access in Teams](guest-access.md)


