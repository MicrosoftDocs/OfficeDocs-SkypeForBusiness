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

Planning for lifecycle management is important because collaboration isn't just an activity you do once and forget. Most projects have a beginning, a middle, and an end, and each phase requires different management ACTIVITIES.

## Lifecycle concepts
[PLACEHOLDER] need intro text


### Teams and channels
[PLACEHOLDER] need intro text


|team  |channel  |
|---------|---------|
|Collection of people, content and tools that faciliate collaboration     |Collaboration space within a team where work (and fun!) happens    |
|Defines membership, visibility, permissions and policies    |Visible and open to anyone in the team to participate         |
|Built on Office 365 modern groups, changes made to O365 Groups will sync to the team    |Can be extended with apps         |
|     |Up to 200 lifetime channels per team         |


### Team origins
[PLACEHOLDER] need intro text

|Origin |Description  |
|---------|---------|
|From scratch     |Create the team and add members via email, username, or DL expansion         |
|From another team     |Use another team as template for channel config, app config, and (optionally) members         |
|Office 365 Group     |Add Teams to existing Group (which has a mailbox and site) – same membership         |
|API or PowerShell     |Use Graph APIs or PowerShell cmdlets to create teams. APIs can be used to programmatically create teams based on GAL attributes (region, department), business processes (client engagements, classroom rosters)
         |

### Team access types
[PLACEHOLDER] need intro text

|Private (default)  |Public |
|---------|---------|
|Owner(s) must approve new members     |Anyone in the organization can join directly         |
|Use this for typical project teams, v-teams     |Use this for interest-based teams that cross org and project boundaries         |
|     |Good default for smaller organizations         |

### Team user types
[PLACEHOLDER] need intro text

|User type  |Description |
|---------|---------|
|Tenant admin     |Full control over roles, permissions, directory, apps         |
|Team creator     |Use with permissions to create a group/team in the directory <br> Can be constrained to subset of users by admin (if so desired)         |
|Team owner     |Up to 10 per Team <br> Manages membership and settings for the team         |
|Team member     |Fully participates in team, may be allowed to create channels         |
|Guest     |Users external to the organization <br> Anyone with an email address can be invited as a guest         |

## IT Decisions to make before getting started

To make sure that your organization is using Teams following organizational requirements, prior to rolling Teams out to your organization, you should implement any required governance policies. This typically includes items like naming conventions, expiration policies, retention policies and more. 

For more details on planning for governance in Teams, see [Plan for governance in Teams](plan-teams-governance.md).

## Teams lifecycle stages

[PLACEHOLDER] Need to determine if this layout is best and if so, where do we introduce decision points and next steps? Likely need more hear around what automation can be used, and reporting to determine what lifecycle actions to take.

### Stage 1: Forming
#### Create the team
- Understand team goal
    - Identify the right “tribe” with a bias toward openness
    - Options: business processes, org structure, projects, existing collaboration entities e.g. SharePoint site, DLs, Outlook Groups? Organic growth?
    - Less is more. Creating broader teams fosters open collaboration
- Decide on access – who can join, who can discover?
    - Public facilitates open collaboration, private if access needs to be controlled
- Ownership model
    - At least 2 owners to facilitates management and handle owners leaving team or organization
- Add members
    - Invite users who need to be a part of the team, can be internal or external (guests)
- Settings
    - Set team picture and add description
    - Set member permissions: who can manage channels, apps, tabs, connectors … 


#### Setup channels
- Understand channel goal
    - Setup channels for collaboration around projects, topics or disciplines
    - General comes by default, add at least one more relevant for team
    - Can grow organically as team gets used more and discussions outgrow existing channels
- Seed with messages, content and apps
    - Put in a welcome message
    - Upload relevant documents to Files tab
    - Add more tabs - office documents (need to be uploaded to files first), web site via URL (https only) or any of the other available tabs (Planner, Power BI, Stream video channel etc)
    - Add connectors to deliver content automatically into the channel (Twitter, Trello, GitHub …)
- Set a description for the channel
- Auto-favorite important channels so they show up on the team list by default


### Stage 2: Storming
- Evolve and explore team config and channel hierarchy
    - Allow users to create and modify channels, encourage exploration and dead ends
    - Experiment with @team @channel mentions, favorited channels, posting in General
    - Let usage guide design – each team is different
    - Settings available for owners who need to create teams that are more locked down
    - Delete channel
- Build trust, tolerance and a spirit of collaboration
    - Initiate and sustain key group communications in Teams
    - Encourage open conversations in channels vs private / 1:1 chats
    - Use “fun” features (giphy, stickers) to develop a team personality
    - Establish the right behaviors for the team (and organization)


### Stage 3: Norming
[PLACEHOLDER] (see above) - how to differentiate? 

### Stage 4: Performing
- A team is a living organism
    - Use champions to sustain usage, also to discover and propagate new behaviors
    - Managing guests judiciously – set a timeframe for a guest’s engagement tied to business needs
    - Ensure team ownership is up-to-date
- Channels should evolve with business needs
    - Create new channels for new projects and topics, allow old channels to fade
        - Delete sensitive or ephemeral ones
        - Carve out new teams as larger groups/areas emerge
    - Use owner-favorited to maintain a steady awareness baseline
    - Try different channel collaborations like channel meetings or tab conversations around documents
- Re-norming required if team starts failing/gets into a rut (restart, re-kickoff)
    - Drive communications into Teams vs. email
    - Use mobile and apps to increase engagement
    - Prune channels if necessary


### Stage 5: Adjourning
- Wrap up work when the team has run its course
    - Formally define closure – to help team members and future searchers
    - Use the team for normal project closure rituals e.g. post-mortems, executive summaries
- Delete teams that are no longer needed (test teams, sensitive content)
    - Team delete is actually a "soft delete" that IT can reverse for up to 30 days
    - Doesn’t impact compliance-archived chats and content
- Use expiration policies to reduce exposure from inactive teams, departed owners
    - In-App expiration


## Team and channel organization and lifecycle management example

[PLACEHOLDER] need to write a walk-thru of how this example team had its lifecycle managed from 'cradle to grave'

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


