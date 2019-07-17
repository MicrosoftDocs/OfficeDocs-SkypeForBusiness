---
title: Apps, bots, & connectors in Microsoft Teams
ms.reviewer: 
description: Use these deployment resources to help you deploy apps in Microsoft.
ms.topic: article
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/28/2019
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
localization_priority: Priority
search.appverid: MET150
appliesto: 
- Microsoft Teams
---
# Apps, bots, & connectors in Microsoft Teams

Apps let you find content from your favorite services and share it right in Teams. They help you do things such as pin services at the top of a channel, chat with bots, or share and assign tasks. To learn more, read [Overview of apps in Teams](https://support.office.com/article/overview-of-apps-in-teams-747492ee-7cdd-4115-a993-8c7e7f98a3d0).

We recommend that you include our featured apps - such as Planner - in your initial Teams rollout. Add other apps, bots, & connectors as you drive Teams adoption.

## Apps deployment decisions

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

## Core deployment decisions

These are the apps settings that most organizations want to change (if the Teams default settings don't work for them).

### App availability settings 

Teams provides a number of apps published by Microsoft and by third parties to engage users, support productivity, and integrate commonly used business services into Teams. Get apps from the Teams Store. By default, all apps, including custom apps that you've submitted via the [Teams Store approval process](https://docs.microsoft.com/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process), are turned on for all users. For example, users can use the Planner app to build and manage team tasks in Teams.

By default, all Microsoft-provided and custom apps are available, and you can turn individual apps on or off. There's an org-wide setting that lets you turn all custom apps on or off for your entire organization.

| Ask yourself | Action |
|--------------|--------|
|Will you change the default Teams apps settings? | For more information about policies and settings that you can use to manage apps in your organization, see [Admin settings for apps in Microsoft Teams](admin-settings.md).|
|||

### App permissions and other considerations

Apps are consented to by users and managed by the admin or IT pro through policies. However, for the most part, an app's permissions and risk profile are defined in the app itself. 

| Ask yourself | Action |
|--------------|--------|
|<br>Which apps do I want to allow access to? Which ones do I not want to allow access to?  | <ul><li>See [Microsoft Teams apps permissions and considerations](app-permissions.md) for a list of things you should consider when allowing access to an app, bot, tab, or connector.</li><li>See [Publish apps in the Teams tenant apps catalog](tenant-apps-catalog-teams.md) for information about making an app available to users in your organization.</li></ul>|
|||

### Bots for private chats and channels

Bots are automated programs that respond to queries or give updates and notifications about details users find interesting or want to stay informed about. Bots allow users to interact with cloud services such as task management, scheduling, and polling in a Teams chat. Teams supports bots in private chats and channels. Administrators can control whether the use of bots is allowed in an Office 365 tenant.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom bots in my Office 365 tenant?|For more information about adding bots, see [Add bots for private chats and channels in Microsoft Teams](add-bots.md). For information about turning custom bots on or off, see [Admin settings for apps in Microsoft Teams](admin-settings.md).|
|||

### Built-in and custom tabs

Owners and team members can add tabs to a channel, private chat, and group chat to help integrate their cloud services. Add tabs to help users access and manage the data they need or use the most. In channels, the Conversations and Files tabs are created by default. In every private chat, the Conversations, Files, Organization, and Activity tabs are created by default. In addition to these built-in tabs, you can design and add custom tabs. To learn about turning Teams apps on or off for your organization, read [Admin settings for apps in Teams](admin-settings.md).

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom tabs in my Office 365 tenant?|For more information, see [Use built-in and custom tabs in Teams](built-in-custom-tabs.md).|
|||

### Office 365 and custom connectors

Connectors keep your team current by delivering content and updates from services you frequently use directly into a channel. With connectors, your Teams users can receive updates from popular services such as Twitter, Trello, Wunderlist, GitHub, and Azure DevOps Services in their Teams chats.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow users to create custom connectors?|For more information, see [Use Office 365 and custom connectors in Teams](office-365-custom-connectors.md).|
|||

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Activity reports

You can use activity reports to see how users in your organization are using Teams. For example, if some don’t use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. To view activity reports, you must be a global admin in Office 365, Teams service admin, or Skype for Business admin.

| Ask yourself | Action |
|--------------|--------|
| Do I want to install any Teams app templates, such as Icebreaker? |To learn more, read [App templates for Teams](https://docs.microsoft.com/microsoftteams/platform/samples/app-templates?toc=MicrosoftTeams/toc.json&bc=/microsoftteams/breadcrumb/toc.json).|
|||

### App templates

App templates are production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub. Each contains detailed instructions for deploying and installing that app for your organization, providing a ready-to-use app that you can install and begin using immediately. The complete source code is available as well, so you can explore it in detail, or fork the code and alter it to meet your specific needs.

| Ask yourself | Action |
|--------------|--------|
| <br>Who needs to see the activity reports, and do they have the correct permissions to view them? |<ul><li>If you don't want to assign an admin role to a user, you can [assign the Reports reader role](teams-activity-reports.md#reports-reader-role).</li><li>See [Roles and permissions](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) and [View and assign roles](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal) for information about assigning admin roles in Azure Active Directory.</li></ul> |
|||



## Next steps
- [Drive adoption](adopt-microsoft-teams-landing-page.md) of featured apps, such as Planner.
- [Roll out meetings & conferencing](deploy-meetings-microsoft-teams-landing-page.md)
- [Roll out cloud voice](cloud-voice-landing-page.md)


