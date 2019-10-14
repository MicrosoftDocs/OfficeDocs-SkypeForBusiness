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


Link to Claudia's tshoot page, maybe scope to GA?

Where does this belong?
https://techcommunity.microsoft.com/t5/Microsoft-Teams/Guest-Access-Troubleshooting-Guide/m-p/119797?attachment-id=3063

Removed from GA checklist:
## If your guests are seeing license errors

Guest access in Microsoft Teams uses Azure Active Directory (Azure AD) Business to Business (B2B) and its licensing model. If you’re seeing licensing errors, make sure to read the [B2B licensing guidance](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance) to understand the licensing requirements your organization has so that your users are able to invite guests to your organization.

A few things to remember:

- Guests are users outside your organization. Your employees, onsite contractors, onsite agents, and so on can't be added as guests. The same applies to your affiliates.
- Guest licenses are counted against the inviting organization. Consider this when you calculate the number of licenses you need.
- Licenses are counted against your organization whether the invited guests come from another Office 365 tenant or are using their personal email addresses.

## Understand the limitations for guests

The guest experience has limitations by design. Review [Understand the limitations for guests](guest-access.md#understand-the-limitations-for-guests) to be sure you're not trying to fix something that isn't a problem.

## Related topics

[Guest access in Teams](guest-access.md)


