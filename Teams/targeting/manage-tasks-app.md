---
title: Manage the Tasks app for your organization in Microsoft Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: andfried
search.appverid: MET150
description: 
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Manage the Tasks app for your organization in Microsoft Teams

[!INCLUDE [preview-feature](../includes/preview-feature.md)]

## Overview of Tasks

The Tasks app brings a cohesive task management experience to Microsoft Teams, integrating personal tasks powered by To Do and team tasks powered by Planner into a single, comprehensive view. Users can access Tasks as an app on the left side of Teams and as a tab within individual teams. The **Personal lists** and **Team lists** in Tasks let users view and manage all their personal and team tasks and prioritize work.

[PLACEHOLDER FOR SCREENSHOT]

With Tasks in Teams, you can target, publish, assign, and track tasks at scale across your organization. For example, with these capabilities, corporate and regional leadership can create and publish task lists to relevant locations, such as retail stores, and track progress through real-time reports. Managers can assign tasks to their staff and direct activities within their stores, and employees have a prioritized list of their assigned tasks. Before people can target and publish tasks lists, you'll first need to set up a team targeting hierarchy for your organization, which defines how all teams in the hierarchy are related to each other.

[PLACEHOLDER FOR SCREENSHOT]

## What you need to know about Tasks

Tasks is available as an app and as a tab within individual teams. As we initially roll out this feature, the app will be named **Tasks by Planner and To Do** in Teams. Later on, the app name will change to **Tasks**. Keep in mind that the app comprises all personal tasks from To Do and team tasks from Planner whereas the tab shows only team tasks.

With Tasks, users get a desktop, web, and mobile experience. If Tasks is installed on the Teams desktop client, users will also see it on their Teams web and mobile clients. The exception is guest users. It's important to know that guests can only access Tasks from the Teams mobile client. Guests won't see Tasks on Teams desktop or web clients.

**Personal lists** show tasks  ???.  **Team lists** show tasks that the whole team is working on. If you don't want users to see Personal lists, you can hide it. To do this, [remove the user's Exchange Online license](https://docs.microsoft.com/microsoft-365/admin/manage/remove-licenses-from-users). Note that after you remove an Exchange Online license, the user no longer has access to their mailbox. Mailbox data is held for 30 days, after which the data will be removed and can't be recovered unless the mailbox is placed on [In-Place Hold or Litigation Hold](https://docs.microsoft.com/exchange/security-and-compliance/in-place-and-litigation-holds).

## Set up Tasks

### Enable or disable Tasks in your organization

Tasks is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](../manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. In the list of apps, do one of the following:

    - To turn off Tasks for your organization, search for the Tasks app, select it, and then click **Block**.
    - To turn on Tasks for your organization, search for the Tasks app, select it, and then click **Allow**.

### Enable or disable Tasks for specific users in your organization

To allow or block specific users in your organization from using Tasks, make sure Tasks is turned on for your organization on the [Manage apps](../manage-apps.md) page, and then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](../teams-app-permission-policies.md).

### Use an app setup policy to pin Tasks to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar&mdash;the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients&mdash;where users can quickly and easily access them.

To pin the Tasks app for your users, you can edit the global (Org-wide default) policy or create and assign a custom app setup policy. To learn more, see [Manage app setup policies in Teams](../teams-app-setup-policies.md).

## Tasks publishing

With Tasks in Teams, organizations can drive consistent execution of store operations at scale across all locations. Corporate and regional leadership can send task lists targeted to relevant locations, such as retail stores, and track their progress through real-time reports. Managers can direct activities within their stores, and employees have a prioritized list of their assigned work.

Corporate headquarters can target, assign, and track tasks across locations. Firstline Workers can view tasks assigned to them and across the store.

Scenario: Communications manager creates lists of tasks that need to be completed and choose the set of store teams that should each receive a copy of the tasks. When selecting store teams, can filter by hierarchy, attributes, or a combination of both. Hierarchy and attributes can be completely customized for the organization . Store managers assign the tasks to team members (Charts view, schedule view, board view, list view) apply a filter, and team members (store associate) can prioritize and manage the work assigned to them. Mark task as complete. Communications manager can see percentage of store teams that have assigned and completed tasks. Can drill down to a specific task to see the status within different parts of the organization, drilling down all the way to a specific team. Similarly, see a drill down for the list as a whole to understand assigned and completed status at each level of the organization, including a specific team. Can see each task in the task list of a team Reportingu nderstand the tasks as a whole to understand assignment and completion status of tasks at each level of the organization, can drill down to , specific tasks. Can see status of each 

The **Published lists** tab only shows for a user if your organization uploaded a team hierarchy and the user is in a team that's defined in the hierarchy. If a user is in a team in the hierarchy, they can publish or receive task lists and view reporting for received lists.

## Power Automate and Graph API

Tasks supports Power Automate for To Do and Graph APIs for Planner. To learn more, see:

- [Planner tasks and plans API overview](https://docs.microsoft.com/graph/planner-concept-overview)
- [Using Microsoft To Do with Power Automate](https://support.office.com/article/using-microsoft-to-do-with-power-automate-526e8f75-217b-46e0-9e06-44780b72c295)