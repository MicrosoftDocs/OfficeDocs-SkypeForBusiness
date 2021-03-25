---
title: Apps, bots, & connectors in Microsoft Teams
ms.reviewer: 
description: Learn about apps, bots, and connectors and how to decide which to deploy in Microsoft Teams based on your organization's profile and business requirements.
ms.topic: article
author: SerdarSoysal
ms.author: serdars
manager: serdars
audience: admin
ms.date: 02/10/2021
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
localization_priority: Priority
search.appverid: MET150
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---
# Apps, bots, & connectors in Microsoft Teams

Apps let you find content from your favorite services and share it in Teams. They help you do things such as pin services at the top of a channel, chat with bots, or share and assign tasks. To learn more, read [Overview of apps in Teams](https://support.office.com/article/overview-of-apps-in-teams-747492ee-7cdd-4115-a993-8c7e7f98a3d0). 

You can add apps to your Teams deployment by using the apps provided with Microsoft Teams, by using certified third-party apps and templates, and by creating your own custom apps.

## Use Microsoft-provided apps

Teams comes with a set of built-in apps, including Lists, Tasks, Praise, Approvals, and more. We recommend that you include Teams featured apps - such as Planner - in your initial Teams rollout. Add other apps, bots, & connectors as you drive Teams adoption.

## Use third-party apps

In addition to Microsoft-provided apps, you can use Microsoft-certified third-party apps. Microsoft works with  Microsoft 365 developer partners to provide the information needed to expedite decisions about using Teams apps and add-ins. For more information, see [Microsoft Teams App Security and Compliance](/microsoft-365-app-certification/teams/teams-apps).

## Use Teams templates

You can also use [Teams templates](/microsoftteams/platform/samples/app-templates?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fMicrosoftTeams%2ftoc.json), production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub.

## Create custom apps

You can quickly build custom low-code solutions by using Teams integration with [Microsoft Power Platform](teams-power-platfom-integration.md). You can also create your own custom app to suit your business needs. For more information, see [Build apps for Microsoft Teams](/microsoftteams/platform/overview).  


## Apps deployment decisions

Teams provides a great out-of-the-box collaboration experience for your organization, and most organizations find that the default settings work for them. This article helps you decide whether to change any of the default settings, based on your organization's profile and business requirements, then it walks you through each change. We've split the settings into two groups, starting with the core set of [changes you're more likely to make](#core-deployment-decisions). The second group includes the [additional settings](#additional-deployment-decisions) you may want to configure, based on your organization's needs.

## Core deployment decisions

These are the apps settings that most organizations want to change (if the Teams default settings don't work for them).

### App availability settings 

Teams provides many apps published by Microsoft and by third parties to engage users, support productivity, and integrate commonly used business services into Teams. Get apps from the Teams Store. By default, all apps, including custom apps that you've submitted via the [Teams Store approval process](/microsoftteams/platform/publishing/apps-publish#microsoft-teams-app-approval-process), are turned on for all users. For example, users can use the Planner app to build and manage team tasks in Teams.

By default, all Microsoft-provided, third-party, and custom apps are available, and you can turn individual apps on or off. There are org-wide settings that lets you turn all third-party and/or custom apps on or off for your entire organization.

| Ask yourself | Action |
|--------------|--------|
|Will you change the default Teams apps settings? | For more information about policies and settings that you can use to manage apps in your organization, see [Admin settings for apps in Microsoft Teams](admin-settings.md).|
|||

### App permissions and other considerations

Apps are consented to by users and managed by the admin or IT pro through policies. However, for the most part, an app's permissions and risk profile are defined in the app itself. 

| Ask yourself | Action |
|--------------|--------|
|<br>Which apps do I want to allow access to? Which ones do I not want to allow access to?  | <ul><li>See [Microsoft Teams apps permissions and considerations](app-permissions.md) for a list of things you should consider when allowing access to an app, bot, tab, or connector.</li><li>See [Manage your apps in the Microsoft Teams admin center](manage-apps.md) for information about making an app available to users in your organization.</li></ul>|
|||

### Bots for private chats and channels

Bots are automated programs that respond to queries or give updates and notifications about details users find interesting or want to stay informed about. Bots allow users to interact with cloud services such as task management, scheduling, and polling in a Teams chat. Teams supports bots in private chats and channels. Administrators can control whether the use of bots is allowed in a Microsoft 365 or Office 365 organization.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom bots in my organization?|For more information about adding bots, see [Add bots for private chats and channels in Microsoft Teams](/microsoftteams/platform/bots/what-are-bots). For information about turning custom bots on or off, see [Admin settings for apps in Microsoft Teams](admin-settings.md).|
|||

### Built-in and custom tabs

Owners and team members can add tabs to a channel, private chat, and group chat to help integrate their cloud services. Add tabs to help users access and manage the data they need or use the most. In channels, the Conversations and Files tabs are created by default. In every private chat, the Conversations, Files, Organization, and Activity tabs are created by default. In addition to these built-in tabs, you can design and add custom tabs. To learn about turning Teams apps on or off for your organization, read [Admin settings for apps in Teams](admin-settings.md).

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow custom tabs in my organization?|For more information, see [Use built-in and custom tabs in Teams](built-in-custom-tabs.md).|
|||

### Custom connectors

Connectors keep your team current by delivering content and updates from services you frequently use directly into a channel. With connectors, your Teams users can receive updates from popular services such as Twitter, Trello, Wunderlist, GitHub, and Azure DevOps Services in their Teams chats.

| Ask yourself | Action |
|--------------|--------|
|Do I want to allow users to create custom connectors?|For more information, see [Use custom connectors in Teams](office-365-custom-connectors.md).|
|||

## Additional deployment decisions

You may want to change these settings, based on your organization's needs and configuration.

### Activity reports

You can use activity reports to see how users in your organization are using Teams. For example, if some don't use Teams yet, they might not know how to get started or understand how they can use Teams to be more productive and collaborative. Your organization can use the activity reports to decide where to prioritize training and communication efforts. To view activity reports, you must be a global admin in Microsoft 365 or Office 365, Teams service admin, or Skype for Business admin.

| Ask yourself | Action |
|--------------|--------|
| <br>Who needs to see the activity reports, and do they have the correct permissions to view them? |<ul><li>If you don't want to assign an admin role to a user, you can [assign the Reports reader role](teams-activity-reports.md#reports-reader-role).</li><li>See [Roles and permissions](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) and [View and assign roles](/azure/active-directory/users-groups-roles/directory-manage-roles-portal) for information about assigning admin roles in Azure Active Directory.</li></ul> |
|||

### App templates

App templates are production-ready apps for Microsoft Teams that are community driven, open-source, and available on GitHub. Each contains detailed instructions for deploying and installing that app for your organization, providing a ready-to-use app that you can install and begin using immediately. The complete source code is available as well, so you can explore it in detail, or fork the code and alter it to meet your specific needs.

| Ask yourself | Action |
|--------------|--------|
| Do I want to install any Teams app templates, such as Icebreaker? |To learn more, read [App templates for Teams](/microsoftteams/platform/samples/app-templates?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=MicrosoftTeams%2ftoc.json).|
|||