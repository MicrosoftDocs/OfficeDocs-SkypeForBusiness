---
title: Best practices for creating and organizing teams in Microsoft Teams
ms.reviewer: pbethi
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
description: Learn about best practices for organizing teams in Microsoft Teams to meet your organization's needs.
f1.keywords:
- NOCSH
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

Best practices for creating and organizing teams in Microsoft Teams
======================================================

Teams are collections of people who gather together around a common goal. This group of people may be within a department or across the organization. What brings them together is the outcome they are driving toward. Members of a team may work at a different pace or create assets differently, but in our experience they often collaborate quickly with each other, a process we call "high velocity teamwork."  

Before creating a team, think about the goal, project, or work items and who in your organization can help deliver it collaboratively. Once you've identified them, add these people or groups to a team to start collaborating. Because membership can change over time, it's a good idea to designate multiple owners for each team. For more information, see [Managing teams](https://support.office.com/article/Teams-and-Channels-df38ae23-8f85-46d3-b071-cb11b9de5499).

Take a look at this short video to see some examples of how to structure cross-organizational or single purpose teams:

> [!VIDEO https://www.youtube.com/embed/hjJWtoaRJeE]

## Add teams gradually

When you first roll out Teams, we recommend starting with a small number of teams and team members. Add new people or groups as you go. The great thing with Teams is that, when you add new people or groups, they can quickly get up to speed on what's already been discussed, as the conversations and files are available to users regardless of when they join. Avoid the temptation to create a bunch of different teams that have the same set of members; instead, create channels in a single team.

## Create channels to focus discussions

Once you've created your team, it’s a good idea to start to think about the different projects and types of conversations you need to support. Create initial channels so people know where to contribute and to find existing conversations. Use descriptive channel names, to make it easy for people to know where to go for each conversation. Add tools (such as OneNote, Power BI, or Planner) as tabs to a channel so members have everything they need, right in the channel. You can also add a commonly used web page as a tab to a channel. 

Learn more about [working in teams](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499#ID0EAABAAA=Work_in_teams) with these quick tips for end users. 

Best practice: Create teams with a larger set of members and more channels. Minimize the number of teams that require a person's participation. Channels within a team should be thought of as topics or workstreams to aid the team in organizing their work to deliver on their joint objectives. There is no specific number of channels that should be created. Each team should craft channels based on their work, priorities, and style. 

Use standard channels for conversations that everyone on the team can contribute to. Take advantage of [Private channels in Teams](private-channels.md) when you need a focused collaboration space with a select group of members.

Larger organizations may want to create teams as "templates" to standardize the information they capture about specific types of work. This is useful for strategic customer management, classroom management, health care scenarios, claim management, incident management and other scenarios appropriate to a specific industry. To learn more, check out [Get started with Teams templates](get-started-with-teams-templates.md) and [Teams templates for small and medium businesses](smb-templates.md).

## Use the General channel

By default, the **General channel** is created for you when you create the team. There are many useful purposes for this channel:

- Use it to share an overview of what the team wants to achieve such as a project charter or who's who in the team.
- Use it for new team member onboarding and other high-level information that a new team member would find useful.
- Use it for announcements, or configure the SharePoint News connector to post your modern status reports to this channel.  
- For new or single purpose teams, it may be the only channel at the beginning as you decide how Teams can best support your goals.

You can't remove, rename, or unfavorite the General channel. Channels appear in alphabetical order (with the General channel at the top). In teams with many channels, use **Hide** or **Show** to display the channels you use the most.

To learn more, peruse the **Work in channels** tab on the [Teams and channels](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499#ID0EAABAAA=Work_in_channels) page.

## Create teams for managers and their direct reports

When you roll out Teams, rather than launching with a "blank slate" (no teams or channels), we strongly recommend that you set up a base framework of teams and channels. This helps to prevent "team sprawl," where users create numerous teams when they should be creating channels in existing teams. To help you get started with a well-designed teams and channels structure, we've created a PowerShell script that creates a team for each of your 1st and 2nd line people managers, with each manager's direct reports as team members. This is a "point-in-time" script (it doesn't update your teams or channels automatically when people are added or removed from an organization). But it's a valuable tool you can use to impose some order on your Teams structure from the start. This script reads your Azure AD, gets a list of managers and their direct reports. It uses this list to create one team per people manager. 

### How to use the PowerShell script 

Start by running the ExportManagers script (which assumes you've already run the Connect-AzureAd and Connect-MicrosoftTeams PowerShell modules). ExportManagers creates a tab-delimited file (ExportedManagerDirects.txt) that lists all managers with their direct reports. 

**LOLA GET SCREEN CAP OF A SAMPLE LIST**

Then, run New-TeamsFromManagers. This script reads in the ExportedManagerDirects.txt file and creates a team for each manager, with that manager's direct reports as members. If any manager or direct isn't enabled for Teams, the script skips them and doesn't create a team. (Review the report, then rerun the script after you've turned on Teams for anybody who needs it. The script won't create a 2nd team for any manager it's already created a team for.)

For each team, the script creates a General and "Just for fun" channel. 

## Consider setting up moderation in your channels

Team owners can turn on moderation for a channel to control who can start new posts and reply to posts in that channel. When you set up moderation, you can choose one or more team members to be moderators. (Team owners are moderators by default.) For more information, see [Set up and manage channel moderation in Microsoft Teams](manage-channel-moderation-in-teams.md).

## Related topics

[Create an org-wide team in Teams](create-an-org-wide-team.md)
