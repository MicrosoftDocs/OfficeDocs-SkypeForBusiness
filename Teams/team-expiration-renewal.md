---
title: Team expiration and renewal in Microsoft Teams
author: LanaChin    
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: abhisgu
localization_priority: Normal
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
description: Learn about team expiration and renewal and how to use Office 365 Group expiration policy to automatically clean up unused teams in Microsoft Teams.
appliesto: 
- Microsoft Teams
---
# Team expiration and renewal in Microsoft Teams

Organizations with a large number of teams often have teams that are never actually used. This can happen because of several reasons including product experimentation, short-term team collaboration, or team owners leaving the organization. Over time, such teams can accumulate and create a burden on tenant resources.  

To curb the number of unused teams, as an admin, you can use [Office 365 Group expiration policy](https://docs.microsoft.com/office365/admin/create-groups/office-365-groups-expiration-policy) to automatically clean up unused teams. Because teams are backed by groups, group expiration policies automatically apply to teams as well.

When you apply an expiration policy to a team, a team owner receives a notification for team renewal 30 days, 15 days and 1 day before the team's expiration date. When the team owner receives the notification, they can click **Renew Now** to renew the team.

![Screenshot of the Renew Now button to renew a team in team settings](media/team-expiration.png "Screenshot of the Renew Now button to renew a team in team settings")

If the team owner doesn't renew the team, the team is put in a "soft-deleted" state, which means it can be restored within the next 30 days.

## Team auto-renewal

There can be times when a team owner is unable to renew the team perhaps because they forgot to renew or were away when renewal was due. In these scenarios, a team in active use can get deleted because of expiration policies that apply to the team.  

To prevent accidental deletion, you can set up auto-renewal in the group expiration policy. When auto-renewal is set up, any team that has at least one channel visit from any team member before its expiration date is automatically renewed without any manual intervention from the team owner.
