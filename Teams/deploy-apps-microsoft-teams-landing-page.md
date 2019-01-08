---
title: Deploy apps, bots, and connectors in Microsoft Teams
description: Use these deployment resources to help you deploy apps in Microsoft.
layout: LandingPage
ms.topic: landing-page
author: LolaJacobsen
ms.author: lolaj
manager: serdars
layout: LandingPage
ms.date: 01/08/2019
ms.service: msteams
ms.collection: Teams_ITAdmin_Help
search.appverid: MET150
appliesto: 
- Microsoft Teams
---
# Deploy apps, bots, and connectors in Microsoft Teams

Apps let you find content from your favorite services and share it right in Teams. They help you do things like pin services at the top of a channel, chat with bots, or share and assign tasks. To learn more, read [Overview of apps in Teams](https://support.office.com/article/overview-of-apps-in-teams-747492ee-7cdd-4115-a993-8c7e7f98a3d0).

We recommend that you roll out apps, bots, and connectors throughout your Teams deployment. 

## Apps deployment decisions

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether you need to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups starting with the core set of [changes you are more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, again based on your organization's needs.

### Core deployment decisions

These are the settings that most organizations want to change (if the Teams default settings don't work for the organization).

#### App availability settings 

Teams provides a number of Microsoft-provided and third-party apps to engage your users and provide additional productivity capabilities and integration of commonly used business services into Teams. These apps are available in the Teams Store. The default configuration is that the these apps are enabled for users to explore and use. For example, users can use the Planner app to build and manage team tasks in a very effective manner. The out-of-the-box configuration enables the Teams default apps as well as external apps that have been submitted via the [Teams Store approval
process.](https://docs.microsoft.com/en-us/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process)

By default, all Microsoft-provided and external apps are available, but you can configure Teams so that external apps are not enabled.

| Ask yourself | Action |
|--------------|--------|
|Will you change the default teams apps settings? | For more information about configuring the availability of external apps, see [Admin settings for apps in Microsoft Teams.](https://docs.microsoft.com/en-us/microsoftteams/admin-settings).|
|||

#### App permissions and other considerations

Apps are consented to by users and managed by IT from a policy perspective. However, for the most part, an app's permissions and risk profile are defined by the permissions and risk profiles of the capabilities it contains. 

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow access to this app within my organization? | For more information, see [Microsoft Teams apps permissions and considerations](app-permissions.md) for a list of things you should consider when allowing access to an app, bot, tab, or connector.|
|||

#### Bots for private chats and channels

Bots are automated programs that respond to queries or give updates and notifications about details users find interesting or want to stay informed about. Bots allow users to interact with cloud services like task management, scheduling, and polling, through chat conversations in Microsoft Teams. Microsoft Teams support bots in private chats and channels within a team. Administrators can control whether the use of bots is allowed or prohibited within the Office 365 tenant.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom bots in my Office 365 tenant?|For more information, see [Add bots for private chats and channels in Microsoft Teams](add-bots.md).|
|||

#### Built-in and custom tabs

Owners and team members can add tabs to a channel, private chat, and group chat to help integrate their cloud services. Tabs can be added to help users easily access and manage the data they need or interact with the most. In channels, the Conversations and Files tabs are automatically created by default. In every private chat, the Conversations, Files, Organization, and Activity tabs are automatically created by default. In addition to these built-in tabs, you can design and add custom tabs. <note: I'm not sure that admins can turn off this feature>

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom tabs in my Office 365 tenant?|For more information, see [Use built-in and custom tabs in Teams](built-in-custom-tabs.md).|
|||

#### Office 365 and custom connectors

Connectors keep your team current by delivering content and updates from services you frequently use directly into a channel. With connectors, your Microsoft Teams users can receive updates from popular services such as Twitter, Trello, Wunderlist, GitHub, and VSTS within the chat stream in their team.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow users to create custom connectors?|For more information, see [Use Office 365 and custom connectors in Teams](office-365-custom-connectors.md).|
|||

### Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

#### Activity reports

You can use activity reports to see how users in your organization are using Microsoft Teams. For example, if some don’t use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. You must have admin permissions or be assigned the Reports reader role to view activity reports.

| Ask yourself | Action |
|--------------|--------|
| Who needs to see the activity reports, and do they have the correct role to view them? | If the user doesn't have an admin role, [assign the Reports reader role](teams-activity-reports.md#reports-reader-role). |
|||

#### Inline message translation

Inline message translation lets users automatically translate Teams messages into the language specified by their personal language settings for Office 365. The inline message translation feature is turned off by default.

| Ask yourself | Action |
|--------------|--------|
| Would the translation feature help my users? | To turn on inline message translation, see [Use inline message translation in Teams](inline-message-translation-teams.md).|
|||



