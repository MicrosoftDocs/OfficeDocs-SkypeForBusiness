---
title: View cross-team and per-team analytics in Teams
author: LanaChin    
ms.author: v-lanac
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: rahulmi
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- M365-collaboration
description: Learn about cross-team analytics and per-team analytics in Teams, which let users see usage data for teams that they are members of.
appliesto: 
- Microsoft Teams
---
# View cross-team and per-team analytics in Teams

In Microsoft Teams, users can view analytics for teams that they are members or owners of. This information gives users insight into usage patterns and activity on their teams. Users can see data such as the number of active users, posts, replies, and guests in each team.

Cross-team analytics gives users a broad overview of usage data for all teams that they are a member or owner of in a single list view. This includes active user and message counts and trend lines for team activity. 

Per-team analytics gives users a more granular view of usage data for a specific team. This includes temporal-based charts for active user and message counts plus deeper breakdowns of user types and activity trends. Users can filter the view to see data for a specific channel in a team or all channels in a team.

## View analytics for all teams that you're a member or owner of

1. In Teams, at the bottom of the teams list, next to **Join or create a team**, click **Manage teams**.
2. Click the **Analytics** tab, and then select a date range to show usage data for all teams that you're a member or owner of.

    ![cross-team-and-per-team-analytics-cross-team.png](../media/cross-team-and-per-team-analytics-cross-team.png)

    |Item |Description  |
    |--------|-------------|
    |**Name**   |Name of the team. |
    |**Active users**   |Number of active users on the team and trend line of team activity during the specified time period. 
    |**People**   |Total number of people on the team in the specified time period. This includes team owners, team members, and guests.|
    |**Guests**   |Number of guests on the team during the specified time period. |
    |**Post**   |Number of unique messages posted in team chat during the specified time period. |
    |**Reply**   |Number of unique replies in team chat during the specified time period. |
    |**Type**   |Whether the team is a private team or public team.|

## View analytics for a team that you're a member or owner of

1. In Teams, go to the team that you want, click **More options (...)**, and then click **Manage team**.
2. Click the **Analytics** tab.
3. To view data for all channels in the team, select **All Channels**. To view data for a specific channel, select that channel.
4. Select a date range.  

    ![cross-team-and-per-team-analytics-per-team.png](../media/cross-team-and-per-team-analytics-per-team.png)

    |Item |Description  |
    |--------|-------------|
    |**Summary**   |Summary of team activity including the following:<ul><li>**Users**: Total users</li> <li>**Posts**: Number of unique messages posted in team chat during the specified time period</li><li>**Replies**: Number of unique replies in team chat during the specified time period.</li> <li>**Apps**: Number of apps</li><li>**Meetings**: Number of Teams meetings scheduled during the specified time period</li> <li>**SharePoint files**: Size of all files shared in channel conversations during the specified time period.</li> </ul> |
    |**Active users**   |Number of active and inactive users.|
    |**Role**   |Numbers of users by role, including team owners, team members, and guests.|
    |**Active users** chart  |Number of active users by date. Hover over the dot on a given date to see the number of active users on that date.|
    |**Messages** chart  |Number of unique messages posted in team chat by date. Hover over the dot on a given date to see the number of unique messages posted on that date.|
    |**Meetings** chart  |Number of meetings scheduled by date. Hover over the dot on a given date to see the number of meetings scheduled on that date.|
    
> [!NOTE]
> We define active users as users who perform an intentional action in the desktop client, mobile client, and web client. Examples of an intentional action include starting a chat, placing a call, sharing a file, editing a document within teams, participating in a meeting, and so on. We strip out passive actions like auto boot, minimizing a screen, or closing the app. We also de-dupe all actions across a single user ID.

## Related topics

- [Teams analytics and reporting](teams-reporting-reference.md)
