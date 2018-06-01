---
title: Prerequisites and environmental dependencies
author: turgayo
ms.author: lolaj
manager: lehewe
ms.date: 05/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: turgayo
description: Use this guidance to learn about the prerequisites and the environmental dependencies to deploy Teams in your organization
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Technical Readiness](media/upgrade-banner-tech-readiness.png "Technical Readiness")

This article is part of the Technical Readiness stage of your upgrade journey, an activity you complete in parallel with the User Readiness stage. 

# Environmental dependencies

Teams combines multiple Office 365 services and is therefore dependent on the correct implementation and operation of these services. These services include but are not limited to SharePoint Online, Exchange Online, and OneDrive for Business.

While not all services are required, it is highly recommended to implement all of them. If you choose to not implement certain services, this will impact the functionality that Teams can offer your organization. For example, while you are not required to implement SharePoint Online, Teams does rely on SharePoint Online for certain functionality such as file sharing in group conversations. Not implementing SharePoint Online will affect functionality offered through the client.

See the following articles to learn about the prerequisites and how Teams interact with other technologies:

-   If your organization has not deployed any Office 365 workloads, see [Getting Started with Office 365 for business.](https://support.office.com/article/Get-started-with-Office-365-for-Business-d6466f0d-5d13-464a-adcb-00906ae87029)

-   If your organization has not added or configured a verified domain for Office 365, see [Verify your Office 365 domain](https://support.office.com/article/Verify-your-Office-365-domain-to-prove-ownership-nonprofit-or-education-status-or-to-activate-Yammer-87d1844e-aa47-4dc0-a61b-1b773fd4e590).

-   If your organization has not synchronized identities to Azure Active Directory, see [Identity models and authentication in Microsoft Teams](identify-models-authentication.md).

-   If your organization does not have Exchange Online, see [Understand how Exchange and Microsoft Teams interact](Exchange-Teams-interact.md).

-   If your organization does not have SharePoint Online, see [Understand how SharePoint Online and OneDrive for Business interact with Microsoft Teams](SharePoint-OneDrive-interact.md).

-   Check how [Office 365 groups and Microsoft Teams interact](Office-365-groups.md)

- If your organization is an educational institution and you use a Student Information System (SIS), [deploy School Data Sync](https://docs.microsoft.com/en-us/schooldatasync/) before deploying Microsoft Teams.
																		   
<table>
<tr><td>![](media/audio_conferencing_image9.png)<br/>Next steps</td><td>Visit [Evaluate your environment](upgrade-plan-journey-evaluate-environment.md) for properly evaluating your current environment for Teams.</td></tr>
</table>