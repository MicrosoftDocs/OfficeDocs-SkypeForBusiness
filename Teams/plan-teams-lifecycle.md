---
title: Plan for lifecycle management in Teams - Microsoft Teams
author: rmw2890
ms.author: MyAdvisor
manager: serdars
ms.date: 07/30/2018
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Learn about how to plan for implementing lifecycle management capabilities in Teams.
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto:
- Microsoft Teams
---

# Plan for lifecycle management in Teams

Teams provides a rich set of tools to implement any lifecycle management capabilities your organization might require. This article guides IT pros to ask the right questions to determine their requirements for lifecycle management, and how to meet them. 

Planning for lifecycle management is important, because collaboration isn’t just an activity you do once and forget. Most projects consist of a beginning, middle, and end. Teams do too, but they can be constructed and used in such a variety of ways that it’s not always obvious where they are in their lifecycle.

## Lifecycle concepts

The following concepts and definitions all affect the decisions you make for lifecycle management.

**Teams**

A team is a collection of people, content, and tools that facilitate collaboration. A team defines who its members are, and the permissions and policies that apply to those members. Teams are built on Office 365 Groups, and changes to Office 365 group membership sync to the team.

**Channels**

Channels are the collaboration spaces within a team where the actual work is done. Anyone on the team can see and participate in any of the channels, which can be extended with apps to aid the workflow. There can be up to 200 channels in a team.

**Team origins**

Teams can originate from a variety of methods, including:

-   Create the team from scratch. Add members by using individual email aliases or usernames, or expand a distribution list.
-   Create the team from an existing team, and use its channel configuration and any app configuration as a template. You can optionally also use its membership list.
-   Add a team to an existing Office 365 Group, which also gives the team access to its mailbox and SharePoint site.
-   Use the Microsoft Graph API or PowerShell cmdlets to create teams. The API can programmatically create teams based on Global Address Book attributes (region, department) or business processes (client engagements, classroom rosters).

**Team access types**

These determine who can join the team:

-   _Private_ teams are restricted to team members that the team owner(s) approve. This is a typical setting for project teams and virtual teams in a large organization.
-   _Public_ teams are open for anyone in the organization to join directly. This is useful for collaboration on topics of general interest to people in different departments working on different projects. This is a good default setting for smaller organizations.

**Team user types** 

These determine how much control a team member has:

-   _Tenant admin_ has full control over roles, permissions, directory, and apps.
-   _Team creator_ has permissions to create a group or team in the directory. The admin can constrain this user type to a subset of users. 
-   _Team owner_ manages membership and settings for the team. There can be as many as 10 team owners per team.
-   _Team member_ fully participates in team, can be allowed to create channels.
-   _Guest_ is a user who’s external to the organization. Anyone with an email address can be invited as a guest.

## IT decisions to make before getting started

Before you roll Teams out to your organization, implement any governance policies that your organization has decided it requires. These can include items like naming conventions, expiration policies, retention policies, and more.

For more information, see [Plan for governance in Teams](plan-teams-governance.md).

## Teams lifecycle stages

NEED INTRO

### Stage 1: Beginning

#### Create the team

The first step is to define the goal of the team (which can range from business processes to org structure to projects, or simply creating an open, unstructured collaboration hub). Defining the team goal goes hand in hand with identifying the right people. As far as practicable, it’s a good idea to foster open collaboration by aiming for broad membership. 

It’s optimal to identify at least two team owners, to account for absence or reassignment. Team owners invite team members, set the team picture and description, and can set permissions for individual members. 

|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Who belongs on the team?</li><li>Will the team be private or public?</li><li>Can new members add themselves or do team owners add them?</li><li>Who will have permissions to create channels or add tabs, bots, and connectors?</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Create channels.</li></ul>|


#### Set up channels

Any team owner or member with appropriate permissions can create channels in a team. It’s important to consider the goal of each channel Options include collaboration around projects, discussions of certain topics. The General channel is included by default in every team; most teams will create additional channels. It’s likely that channels will grow organically as new topics or projects arise, and discussions might outgrow the channel they began in.

To spark interest, a channel owner can post a welcome message, upload relevant documents to the Files tab, or add tabs or connectors to the channel. The owner also sets the channel description, and can “auto-favorite” important channels so they’re listed by default for all team members.

|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>How will channels be set up—by project, by topic, or ...?</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Collaborate.</li></ul>|

### Stage 2: Middle

As the teamwork begins, the team membership will likely evolve, along with the channel hierarchy. Unless the team needs to be strictly controlled and locked down, it’s a good idea to encourage exploration and even dead ends. As users get more comfortable, they can experiment with \@team mentions, marking channels as favorite, and using the General tab to get comfortable with posting. Each team is different; let usage guide the evolution of the design.

Trust, tolerance, and a spirit of collaboration grow organically as key group communications are initiated and sustained in Teams. Team members see the usefulness of group conversations over one-on-one chats. It can be quite compelling to watch a team personality develop, aided by features like Giphys and stickers. At the same time, it’s important that rogue or rude behavior be discouraged any time it occurs.

Because teams are living organisms, they occasionally need to be checked on and cared for. These are some best practices:

-   Use champions to sustain usage if it starts to flag, and also to discover and propagate creative new behaviors. 
-   Manage guests judiciously, making sure their access ends when the business need ends.
-   Let channels evolve with business needs, adding new ones as necessary and allowing old ones to fade (or deleting them, if they contain sensitive or ephemeral data).
-   Carve out new teams as larger groups or interest-based areas emerge.
-   Try different channel collaborations, such as channel meetings or tab conversations around documents.
-   If a team starts to get into a rut, consider:
    -   Driving communications into Teams versus email.
    -   Using mobile apps to increase engagement.
    -   Pruning the number of channels.

### Stage 3: End

When the work of a team has run its course, it’s important to formally acknowledge that it’s over. This gives team members a sense of closure and also prevents anyone from accessing outdated, stale information. You can use the team itself to conduct closure rituals like post-mortems and executive summaries.

You can delete teams that you know you don’t need (for example, a team created purely for testing or a team that contains sensitive data). Teams are actually deleted with a “soft delete” that IT can reverse for up to 30 days. Deleting teams doesn’t affect any chats or content that were archived in accordance with compliance policies.

You can also use expiration, retention, and archiving policies to reduce exposure from teams that aren’t active any longer or whose owners have left the organization.

|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Define what the end of a team’s life looks like.</li><li>Decide whether/how long to keep the content of a team available.</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Document best practices and lessons learned.</li><li>Archive data, if necessary.</li></ul>|

## Team and channel organization and lifecycle management example

The following example shows how a team and its channels might be structured for a typical project.

|Channel  |Tabs & Resources |
|---------|---------|
|General     |Onboarding guidance <br> Role information <br> Training videos         |
|Design     |Specifications & drawings <br> User feedback         |
|Documentation     |Product help <br> Implementation guidance         |
|Engineering     |Delivery schedule & tracking <br> Quality & reliability info         |
|Go to Market     |Marketing strategy overview <br> GTM plan          |
|Production     |Production schedule <br> Production management tool <br> Downtime alerts         |
|Research     |Competitive research <br> User feedback & experiments         |
|Strategy and Timeline     |Product vision and strategy <br> Market opportunity and timelines         |
|Support and Feedback     |Conversations on help needed <br> Customer feature request form         |


