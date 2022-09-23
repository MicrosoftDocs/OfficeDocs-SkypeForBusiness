---
title: Know about apps in Microsoft Teams
ms.reviewer: 
description: Learn about apps and decide what apps to allow in Teams based on your organization's profile and business requirements.
ms.topic: article
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-collaboration
  - m365-frontline
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020; intro-overview; intro-hub-or-landing
---
# Understand Microsoft Teams apps

Apps are a great way to bring together your workplace tools and services and collaborate with others. Apps help end-users be more productive, collaborative, and effective in their day-to-day tasks. Organizations use apps to connect with their customers, provide services, and share information. Examples are end-users using a pinned Calendar app in Teams to quickly collaborate with others, an app with bots functionality informing users of the quality of a web service in a Teams channel, and an app to share and assign tasks to various end-users in a channel.

Our extensive [catalog](https://appsource.microsoft.com/en-US/marketplace/apps?product=office%3Bteams&page=1) of validated and secure apps in Teams Store provides end-users access to the tools and services that your organization needs every day. Microsoft Teams apps are web-based SaaS apps that don't need to be deployed. End-users can use apps in Teams based only on the [permissions provided by you](app-policies.md). As an admin, you use enterprise-grade policies to allow or block any app for your organization's users. You control the availability of apps for each user across the various contexts such as meeting, chats, and channels.

This article helps you understand the types of apps and where from your users access those apps. To learn more about the use of apps, read [Overview of apps for end-users](https://support.office.com/article/overview-of-apps-in-teams-747492ee-7cdd-4115-a993-8c7e7f98a3d0).

The different types of apps that your end-users can use in Teams are:

* [Core apps that are part of Teams](#core-apps).
* Other [apps created by Microsoft](#microsoft-provided-apps).
* [Third-party apps](#third-party-apps-validated-by-microsoft) by partners (validated by Microsoft).
* [Custom apps](#custom-apps) created by your own organization.

## Core apps

Some Teams functionalities such as activity feed, teams, chat, calendar, calls, files, and assignments (education tenants) are available by default and pinned by default for ease of access for end-users. For frontline workers, only activity, shifts, chat, and calling are available and pinned. As an admin, you can modify this default behavior using [setup policy](/microsoftteams/teams-app-setup-policies).

:::image type="content" source="media/core-apps-pinned1.png" alt-text="Core apps are the apps pinned in Teams by default." lightbox="media/core-apps-pinned2.png":::

## Microsoft-provided apps

Microsoft provides many apps to improve productivity and collaboration. You and end-users can find these apps by looking for Microsoft listed as the Publisher in Teams admin center or listed as Provider in the Teams store.

Teams comes with a set of built-in apps, including Lists, Tasks, Praise, Approvals, and more. We recommend that you include the featured apps—such as Planner—in your initial Teams rollout.

:::image type="content" source="media/microsoft-apps-in-tac1.png" alt-text="Screenshot of Microsoft apps in Teams admin center." lightbox="media/microsoft-apps-in-tac2.png":::

## Third-party apps validated by Microsoft

In addition to Microsoft-provided apps, you can use Microsoft-validated third-party apps. Microsoft validates the functionality and security of these apps before making these apps available in Teams store. To understand the benefits of app validation, see [validation of third-party apps](overview-of-app-validation.md).

:::image type="content" source="media/3p-apps-in-teams.png" alt-text="Screenshot of an example of third-party apps in the Teams' store.":::

## Custom apps

Apps created by developers in your organization are called custom apps (or Line of Business apps). Your organization may commission the creation of custom apps for org-specific requirements. You have the control to allow or block such apps for entire organization or for specific users. Developers in your organization can build custom low-code solutions by using Teams integration with [Microsoft Power Platform](/microsoftteams/platform/samples/teams-low-code-solutions).

After an admin allows the use of custom apps, end-users can find such apps by selecting **Built for your org** in the left navigation of Teams store.

:::image type="content" source="media/built-for-your-org1.png" alt-text="Screenshot of custom apps in Teams' store in the Teams' desktop app." lightbox="media/built-for-your-org2.png":::

For more information, see [Understand and manage custom and sideloaded apps](custom-app-overview.md).

## About App Templates

Using the app development methods, Microsoft creates and provides functional and production-ready sample apps. Collectively, these apps are called App templates for Teams and are provided to:

* Illustrate a few collaboration use cases in Teams.
* Showcase app development best practices and methods.
* Provide open-source apps that developers can extend to create their own apps.

Your organization developers customize App Templates with simple changes to the provided source code. You provide these apps as custom apps for your end-users, to meet any organization needs.

To know more, see [Microsoft Teams App Templates](https://adoption.microsoft.com/microsoft-teams/app-templates/).

## Understand app capabilities

The Microsoft Teams platform offers a large variety of features. Each feature is a way of interacting with users that makes the Teams app capability relevant to the users need. Capabilities are the core functionalities that can be built in an app to enable integration and interaction.

:::row:::
    :::column span="":::
    :::column-end:::
    :::column span="3":::
        :::image type="content" source="media/teams-app-capabilities-group.png" alt-text="Graphic that shows the app capabilities of a Microsoft Teams app." border="false":::
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

To provide rich experiences that allow end-users to work inside Teams, app developers use the following app capabilities.

* **Bots**: Bots are also referred to as a chatbot or conversational bot. It's an app that executes simple and repetitive tasks. A bot interaction can be a quick question and answer, or it can be a complex conversation that provides access to services or assistance. Users can have a conversation with a bot in a personal chat,  channel, or group chat. For more information, see [Bots in Microsoft Teams](/microsoftteams/platform/bots/what-are-bots).

  Teams supports bots in private chats and channels. Administrators can control whether the use of bots is allowed in a Microsoft 365 or Office 365 organization.For information about turning custom bots on or off, see [Admin settings for apps in Microsoft Teams](admin-settings.md).

* **Tabs**: Tabs are Teams-aware webpages pinned at the top of a channel or a chat. Tabs let you interact with content and services with a web-like experience. They're simple HTML <iframe\> tags that point to domains declared in the app manifest and can be added as part of a channel inside a team, group chat, or personal app for an individual user. For more information, see [Microsoft Teams tabs](/microsoftteams/platform/tabs/what-are-tabs).

  In every private chat, the Conversations, Files, Organization, and Activity tabs are created by default. In addition to these built-in tabs, developers can design and add custom tabs. To learn about turning Teams apps on or off for your organization, see [Use built-in and custom tabs in Teams](/microsoftteams/platform/tabs/what-are-tabs).

* **Webhooks and connectors**: Webhooks and connectors help to connect the web services to channels and teams in Microsoft Teams. Webhooks are user defined HTTP callback that notifies users about any action that has taken place in the Teams channel. It's a way for an app to get real time data. Connectors allow users to subscribe to receive notifications and messages from your web services. For more information, see [Webhooks and connectors](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors).

  To allow users to use custom connectors in Teams, see [Use custom connectors in Teams](office-365-custom-connectors.md).

* **Messaging extensions**: Messaging extensions are shortcuts to insert app content or to act on a message without end-users having to navigate away from the conversation.   Users can search or initiate actions in an external system from the compose message area, the command box, or directly from a message. For more information, see [Message extensions](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions?tabs=dotnet).

* **Meeting extensions**: Users can enhance the meeting experience by integrating tabs, bots, and message extensions within meetings and make meetings more productive. You can identify various participant roles and user types, get meeting events, and generate in-meeting dialogs. For more information, see [Apps for Teams meetings](/microsoftteams/platform/apps-in-teams-meetings/teams-apps-in-meetings).

* **Cards**: Cards provide users with various visual, audio, and selectable messages and help in conversation flow. Task modules help you create modal pop-up experiences in Microsoft Teams. They're useful for starting and completing the tasks, or displaying rich information like videos or Power business intelligence (BI) dashboards. For more information, see [Cards and task modules](/microsoftteams/platform/task-modules-and-cards/cards-and-task-modules).

There are several ways you can interact with apps and services in Teams:

* Chat with a bot: Bots provide answers, updates, and assistance in a channel. Users can chat with bots in a one-on-one chat, group chat, or in a channel. They can help with task management, scheduling, and more.

  :::image type="content" source="media/chat-bot.gif" alt-text="Gif that shows a sample chat bot in Microsoft Teams.":::

* Share content on a tab: Tabs help users share content and functionality from your favorite services in a channel. They can connect users to Microsoft services (like Excel or SharePoint), other services (like Asana, YouTube, and Zendesk), or to a website of your choice.

  > [!NOTE]
  > Tabs in channels can be seen by everyone on the team. Tabs in chats can only be seen by the people in that chat.

* Get updates from a connector: Connectors send updates and information directly to a channel. Get automatic updates from your favorite services like Trello, JIRA, Twitter, RSS feeds, GitHub, and more.

* Add rich content to your messages: Find content from different services and send it straight to a message. Users can share weather reports, daily news, images, and videos with anyone they're talking to. Messages sometimes include buttons for interacting with the app. For example, a daily weather report could include an option to download the forecast for the entire week.

To view common use cases mapped to Teams capabilities, see [Map your use cases to Teams app capabilities](/microsoftteams/platform/concepts/design/map-use-cases).

<!--- TBD: Admins do many considerations and decisions around app adoption and app governance. These are to be covered in a separate article. Commenting the below content for now as part of this article revamp.

## Apps deployment decisions

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

## Core deployment decisions

These are the apps settings that most organizations want to change (if the Teams default settings don't work for them).

### App availability settings

Teams provides many apps published by Microsoft and by third parties to engage users, support productivity, and integrate commonly used business services into Teams.
Get apps from the Teams Store. By default, all apps, including custom apps that you've submitted via the [Teams Store approval process](/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process), are turned on for all users. For example, users can use the Planner app to build and manage team tasks in Teams.

By default, all Microsoft-provided, third-party, and custom apps are available, and you can turn individual apps on or off. There are org-wide settings that let you turn all third-party and/or custom apps on or off for your entire organization.

| Ask yourself | Action |
|--------------|--------|
|Will you change the default Teams apps settings? | For more information about policies and settings that you can use to manage apps in your organization, see [Admin settings for apps in Microsoft Teams](admin-settings.md).|

### App permissions and other considerations

Apps are consented to by users and managed by the admin or IT pro through policies. However, app permissions and risk profile are defined in the app itself.

| Ask yourself | Action |
|--------------|--------|
|<br>Which apps do I want to allow access to? Which ones do I not want to allow access to?  | <ul><li>See [Microsoft Teams apps permissions and considerations](app-permissions.md) for a list of things you should consider when allowing access to an app, bot, tab, or connector.</li><li>See [Manage your apps in the Microsoft Teams admin center](manage-apps.md) for information about making an app available to users in your organization.</li></ul>|

--->

<!--- TBD: Rewrite this to talk about bots and tabs as a capability of apps. Admins do not govern bots, tabs, etc. Admins only govern apps that contain capabilities such as connectors, bots, etc. This writeup gives an impression that admins manage apps + bots + tabs + connectors, etc.

### Bots for private chats and channels

Bots are automated programs that respond to queries or give updates and notifications about details users find interesting or want to stay informed about. Bots allow users to interact with cloud services such as task management, scheduling, and polling in a Teams chat. Teams supports bots in private chats and channels. Administrators can control whether the use of bots is allowed in a Microsoft 365 or Office 365 organization.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom bots in my organization?|For more information about adding bots, see [Add bots for private chats and channels in Microsoft Teams](/microsoftteams/platform/bots/what-are-bots). For information about turning custom bots on or off, see [Admin settings for apps in Microsoft Teams](admin-settings.md).|

### Built-in and custom tabs

Owners and team members can add tabs to a channel, private chat, and group chat to help integrate their cloud services. Add tabs to help users access and manage the data they need or use the most. In channels, the Conversations and Files tabs are created by default. In every private chat, the Conversations, Files, Organization, and Activity tabs are created by default. In addition to these built-in tabs, you can design and add custom tabs. To learn about turning Teams apps on or off for your organization, read [Admin settings for apps in Teams](admin-settings.md).

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom tabs in my organization?|For more information, see [Use built-in and custom tabs in Teams](/microsoftteams/platform/tabs/what-are-tabs).|

### Custom connectors

Connectors keep your team current by delivering content and updates from services you frequently use directly into a channel. With connectors, your Teams users can receive updates from popular services such as Trello, Wunderlist, GitHub, and Azure DevOps Services in their Teams chats.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow users to create custom connectors?|For more information, see [Use custom connectors in Teams](office-365-custom-connectors.md).|

--->

<!--- TBD: Activity reports is not part of app overview. Commenting for now. To be reused in a different article later.

### Activity reports

You can use activity reports to see how users in your organization are using Teams. For example, if some don't use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. To view activity reports, you must be a global admin in Microsoft 365 or Office 365, Teams service admin, or Skype for Business admin.

| Ask yourself | Action |
|--------------|--------|
| Who needs to see the activity reports, and do they have the correct permissions to view them? |<ul><li>If you don't want to assign an admin role to a user, you can [assign the Reports reader role](teams-activity-reports.md#reports-reader-role).</li><li>See [Roles and permissions](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) and [View and assign roles](/azure/active-directory/users-groups-roles/directory-manage-roles-portal) for information about assigning admin roles in Azure Active Directory.</li></ul> |

--->

## Related articles

* [Learn more about App Templates for Teams](/microsoftteams/platform/samples/app-templates).

* [Admin settings for apps in Teams](admin-settings.md)

* [Manage your apps in the Microsoft Teams admin center](manage-apps.md)
