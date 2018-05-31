---
title: Plan for your upgrade - Prerequisites
author: turgayo
ms.author: lolaj
manager: lehewe
ms.date: 05/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: turgayo
description: Use this guidance to learn about the prerequisites to deploy Teams in your organization
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

![Technical Readiness](media/upgrade-banner-tech-readiness.png "Technical Readiness")

This article is part of the Technical Readiness stage of your upgrade journey, an activity you complete in parallel with the User Readiness stage. 

# Environmental dependencies

Teams combines multiple Office 365 services and is therefore dependent on the correct implementation and operation of these services. These services include but are not limited to SharePoint Online, Exchange Online, and OneDrive for Business.

While not all services are required, it is highly recommended to implement all of them. If you choose to not implement certain services, this will impact the functionality that Teams can offer your organization. For example, while you are not required to implement SharePoint Online, Teams does rely on SharePoint Online for certain functionality such as file sharing in group conversations. Not implementing SharePoint Online will affect functionality offered through the client.

Go to the following articles to learn about the requirements:
- [Office 365 groups and Microsoft Teams ](Office-365-groups.md)
- [How SharePoint Online and OneDrive for Business interact with Microsoft Teams](SharePoint-OneDrive-interact.md) 
- [How Exchange and Teams interact ](Exchange-Teams-interact.md)