---
title: Plan for lifecycle management in Teams - Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.date: 09/26/2018
ms.topic: reference
ms.service: msteams
ms.reviewer: rowille
description: Learn about how to plan for implementing lifecycle management capabilities in Teams.
localization_priority: Priority
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Plan for lifecycle management in Teams

Teams provides a rich set of tools to implement collaboration lifecycle management processes for your organization. This article guides IT pros through the right questions to determine their requirements for lifecycle management, and the tools to use to meet them. 

Planning for lifecycle management is important, because it means you’re building a plan to get your work done effectively. Most projects consist of a beginning, middle, and end. Teams do too, but they can be constructed and used in such a variety of ways that it’s not always obvious which stage of their lifecycle they’re in. Having a plan for lifecycle management will help you track your organization’s projects as they go through these stages.

> [!Tip]
> Watch the following session to learn about more about lifecycle in Microsoft Teams: [Governance, management and lifecycle in Microsoft Teams](https://aka.ms/teams-governance)


## Lifecycle concepts

The following concepts and definitions all affect the decisions you make for lifecycle management.

**Teams**

A _team_ is a collection of people, content, and tools that facilitate collaboration. A team defines who its members are, and the permissions and policies that apply to those members. Teams are built on Office 365 Groups, and changes to Office 365 group membership sync to the team. Like other Office 365 Groups, Teams come auto-provisioned with an Exchange mailbox, a SharePoint site, a OneNote notebook, and other assets within Office 365. [Learn more about Office 365 Groups](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2).

**Channels**

Channels are the collaboration spaces within a team where the actual work is done. Each channel represents a different topic or workstream within the overall team. For each channel, a folder is automatically created on the SharePoint site to store all files shared to that channel, making it easy for users to find and work on the documents they care about. Channels can also be extended with apps that are relevant to the particular workstream—for example, you can add a Power BI dashboard to a channel to track the success of one aspect of your project.

**Team access types**

These determine who can join the team:

-   _Private_ teams are restricted to team members approved by the team owner(s). This is a typical setting for project teams and virtual teams in a large organization.
-   _Public_ teams are open for anyone in the organization to join directly. This is useful for collaboration on topics of general interest to people in different departments working on different projects. This is a good default setting for smaller organizations.

**Team user types and admin roles** 

Team user types determine how much control a team member has:

-   _Team creator_ has permissions to create a group or team in the directory. The admin can constrain this user type to a subset of admins or users. For more information, see [Manage who can create Office 365 Groups](https://support.office.com/article/Manage-who-can-create-Office-365-Groups-4c46c8cb-17d0-44b5-9776-005fced8e618). 
-   _Team owner_ manages membership and settings for the team. There can be as many as 10 team owners per team.
-   _Team member_ is a member of your organization who participates in a team.
-   _Guest_ is a user who’s external to your organization. Anyone with an email address can be invited as a guest if your organization has enabled [guest access](guest-access.md).

> [!Note]
> You can learn more about team owner and team member capabilities in the article [Assign role and permissions in Microsoft Teams](assign-roles-permissions.md).

Teams admin roles determine what capabilities each admin role holder has. These are described in the following table.

<table>
 <thead>
  <tr>
    <th width="0.5%"></th>
    <th width="15.5%">Role&nbsp;&nbsp;</th>
    <th width="25%">Description</th>
    <th width="60%">Can do the following tasks, using tools as noted</th>
  </tr>
</thead>
<tbody>
   <tr>
    <td valign="top" colspan="2">Teams Service Administrator</td>
    <td valign="top">Manage the Teams service, and create and manage Office 365 Groups</td>
    <td valign="top">Manage meetings, including meeting policies, configurations, and conference bridges<sup>1</sup><br><br>Manage voice, including calling policies, phone number inventory and assignment, call queues, and auto attendants<sup>1</sup><br><br>Manage messaging, including messaging policies<sup>1</sup><br><br>Manage all org-wide settings, including federation, Teams upgrade, and Teams client settings<sup>1</sup><br><br>Manage the teams in the organization and their associated settings, including membership<sup>2</sup><br><br>View the user profile page and troubleshoot user call quality problems by using advanced troubleshooting toolset<sup>3</sup></td>
</tr>
<tr>
<td valign="top" colspan="2">Teams Communications Administrator</td>
<td valign="top">Manage calling and meetings features within the Microsoft Teams service</td>
<td valign="top">Manage meetings, including meeting policies, configurations, and conference bridges<sup>1</sup><br><br>Manage voice, including calling policies, phone number inventory and assignment, call queues, and auto attendants<sup>1</sup><br><br>View user profile page and troubleshoot user call quality problems using advanced troubleshooting toolset<sup>1</sup></td>
</tr>
<tr>
<td valign="top" colspan="2">Teams Communications Specialist</td>
<td valign="top">Troubleshoot communications issues within Teams by using basic tools</td>
<td valign="top">Access to the user profile page for troubleshooting calls in Call Analytics. Can only view user information for the specific user being searched for.<sup>3</sup></td>
</tr>
<tr>
<td valign="top" colspan="2">Teams Communications Support Engineer</td>
<td valign="top">Troubleshoot communications issues within Teams by using advanced tools</td>
<td valign="top">Access to the user profile page for troubleshooting calls in Call Analytics. Can view the full call record information.<sup>3</sup></td>
</tr>
<tr>
</tbody>
<tfoot>
<tr><td align="right"><sup>1</sup></td><td colspan="3"><a href="https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell
">PowerShell—Skype for Business module</a> or <a href="https://docs.microsoft.com/microsoftteams/manage-teams-skypeforbusiness-admin-center">Microsoft Teams admin center</a></td></tr>
<tr><td align="right"><sup>2</sup></td><td colspan="3"><a href="https://www.powershellgallery.com/packages/MicrosoftTeams/0.9.3">PowerShell—Microsoft Teams module</a> or <a href="https://docs.microsoft.com/microsoftteams/manage-teams-skypeforbusiness-admin-center">Microsoft Teams admin center</a></td></tr>
<tr><td align="right"><sup>3</sup></td><td colspan="3"><a href="https://docs.microsoft.com/microsoftteams/manage-teams-skypeforbusiness-admin-center">Microsoft Teams admin center</a> only</td>
</tr>
</tfoot>
</table>


## IT decisions to make before getting started

Before you roll Teams out to your organization, implement any governance policies that your organization has decided it requires. These can include items like naming conventions, expiration policies, retention policies, and more. Generally speaking, it’s much easier to implement these requirements prior to scaling your deployment across your organization.

For more information, see [Plan for governance in Teams](plan-teams-governance.md).

## Teams lifecycle stages

Generally speaking, a team has a purpose that’s aligned with a project or accomplishing a goal. Even if a team was formed based on a shared interest, the team membership will probably change over time and the discussion might grow stale—only to surface again in a slightly different way in a different team.

Each team has a beginning, when the team is created and the channels are set up; a middle, when the team is used and collaboration occurs to match the rhythm of the workflow; and—sometimes—an end, when the team has completed its purpose and reached the end of its useful life. 

For more information, see [Manage teams in the Microsoft Teams admin center](manage-teams-in-modern-portal.md).

### Stage 1: Beginning

#### Create the team

The first step is to define the goal of the team (which can range from business processes to org structure to projects, or simply creating an open, unstructured collaboration hub). Defining the team goal goes hand in hand with identifying the right people. As far as practicable, it’s a good idea to foster open collaboration by aiming for broad membership. 

Team owners invite team members, set the team picture and description, and can set permissions for individual members. 

> [!Tip]
>  It’s optimal to identify at least two team owners, to account for absence or reassignment.

#### Team origins

Teams can originate from a variety of methods, including:

-   Create the team from scratch. Add members by using individual email aliases or usernames, or expand a distribution list.
-   Create the team from an existing team, and use its channel configuration and any app configuration as a template. You can optionally also use its membership list.
-   Add a team to an existing Office 365 Group, which also gives the team access to its mailbox and SharePoint site.
-   Use the Microsoft Graph Teams APIs or PowerShell cmdlets to create teams. The APIs can programmatically create teams based on Global Address Book attributes (such as region or department) or business processes (client engagements or classroom rosters, for example).

Use these links to get more information about organizing your teams:

-   [Best practices for organizing teams in Teams](best-practices-organizing.md)
-   [Deploy chat, teams, channels, & apps](deploy-chat-teams-channels-microsoft-teams-landing-page.md)
-   [Deploy meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md)
-   [Deploy cloud voice](cloud-voice-landing-page.md)


|    |     |
|-----------|------------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>What’s the purpose of the team?</li><li>Who belongs on the team?</li><li>Will the team be private or public?</li><li>Can new members add themselves or do team owners add them?</li><li>Who will have permissions to create channels or add tabs, bots, and connectors?</li></ul> |
| ![An icon depicting the next steps](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Create the team.</li><li>Plan for channels.</li></ul>|


#### Set up channels

Any team owner or member with appropriate permissions can create channels in a team. It’s important to consider the goal of each channel—options include collaboration around projects, discussions of topics, or areas of common interest. By default, every team includes a General channel; most teams need more than this, and members will create additional channels. It’s likely that the set of channels will grow organically as new topics or projects arise, and discussions might outgrow the channel they began in.

To spark interest, the channel owner can post a welcome message, upload relevant documents to the **Files** tab, or add tabs or connectors to the channel. The owner also sets the channel description, and can “auto-favorite” important channels so they’re listed by default for all team members.

|    |     |
|-----------|------------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>What initial channels will be added to the team?</li><li>What guidance, if any, will be provided for adding new channels? (Will they be set up by project, by topic, or ...?)</li></ul> |
| ![An icon depicting the next steps](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Create initial channels.</li><li>Post a welcome message.</li><li>Start collaborating.</li></ul>|

### Stage 2: Middle

As the teamwork begins, the team membership probably begins to evolve, along with the channel hierarchy. Unless the team needs to be strictly controlled and locked down, it’s a good idea to encourage exploration even if it leads to dead ends. As users get more comfortable, they can experiment with \@team mentions, marking channels as favorite, and using the General channel to get comfortable with posting. Each team is different; let usage guide the evolution of the design. Monitor the usage and health of the team via Teams reporting capabilities.

Trust, tolerance, and a spirit of collaboration grow organically as key group communications are initiated and sustained in Teams. Team members see the usefulness of group conversations over one-on-one chats. Individual teams tend to develop their own personality, aided by fun features like Giphys and stickers. At the same time, it’s important that rogue or rude behavior be discouraged any time it occurs.

Because teams are living organisms, they occasionally need to be checked on and cared for. These are some best practices:

-   Use champions to sustain usage if it starts to drop, and also to discover and propagate creative new behaviors. 
-   Manage guests judiciously, making sure their access ends when the business need ends.
-   Let channels evolve with business needs, adding new ones as necessary and allowing old ones to fade (or consider archiving or deleting them if they contain sensitive or ephemeral data, based on your retention requirements).
-   Carve out new teams as larger groups or interest-based areas emerge.
-   Try different channel collaborations, such as channel meetings or tab conversations around documents.

If a team starts to get into a rut, consider:

-   Driving communications into teams as opposed to email.
-   Using mobile apps to increase engagement.
-   Pruning the number of channels.

|    |     |
|-----------|------------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Who will monitor usage to identify problems?</li><li>What metrics will be used to determine whether a team is healthy?</li><li>Identify any teams that have reached the end of their useful life.</li><li>Identify unhealthy teams that still serve a purpose but need revitalizing.</li></ul> |
| ![An icon depicting the next step](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Implement a process to monitor individual team health.</li></ul>|

### Stage 3: End

When the work of a team has run its course, it’s important to formally acknowledge that it’s over. This gives team members a sense of closure and also prevents anyone from accessing outdated, stale information. You can use the team itself to conduct closure rituals like post-mortems and executive summaries.

You can delete teams that you know you don’t need (for example, a team created purely for testing or a team that contains sensitive data). Teams are actually deleted with a “soft delete” that IT can reverse for up to 21 days (30 days for Office 365 Groups). Deleting teams doesn’t affect any chats or content that were retained in accordance with compliance policies.

You can also use expiration and retention policies in addition to archiving capabilities to reduce exposure from teams that aren’t active any longer or whose owners have left the organization.

For information about setting up expiration and retention policies, see [Overview of security and compliance in Microsoft Teams](security-compliance-overview.md).

|    |     |
|-----------|------------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Define what the end of a team’s life looks like.</li><li>Decide whether to keep the content of a team available, and for how long.</li></ul> |
| ![An icon depicting the next steps](media/audio_conferencing_image9.png)<br/>Next steps|<ul><li>Document best practices and lessons learned.</li><li>Archive data, if necessary.</li></ul>|

