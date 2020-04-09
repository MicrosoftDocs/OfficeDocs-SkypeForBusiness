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

The Tasks app in Teams  

- Set up a team hierarchy to publish tasks to large sets of teams across your organization.
- Users can create personal tasks and see their assigned team tasks to manage and prioritize work.
- 

- Transition into Planner app 
- Users will see Personal lists and Team lists 
- Note that they will get a desktop experience and mobile experience.  If the app is installed for a user on desktop, they will also see it on mobile. 
- Ability to disable Exchange license (soon to be To Do license instead) to hide personal lists 
- How to enable publishing by uploading a CSV (the doc you created) 
- PowerAutomate and Graph APIs  for To Do and Planner - Refer to To Do and Planner documentation 
- Guest user behavior - Guest users won't see the Tasks app on desktop but they will on mobile. They'll see the tabs in both places.

With Tasks in Teams, now customers can drive consistent execution of store operations at scale across all of an organization's locations. Corporate and regional leadership can send task lists targeted to the relevant locations, such as specific retail stores, and track their progress through automatic real-time reports. Managers have tools to easily direct activities within their stores, and Firstline Workers have a simple prioritized list available via their personal or company-issued device showing them exactly what to do next. Tasks targeting, publishing, and reporting is coming to Teams in the first half of this year. Assign task lists to users.

Tasks in Teams integrates both To Do and Planner, so individuals who frequently divide their attention across personal and team tasks will have a view that includes both.  For users of To Do and Planner, it is also a great way to access tasks while communicating with a team, without having to switch apps.

Tasks is available as an app and as a tab in individual teams. The Tasks app shows users all their personal tasks from To Do and team tasks Planner. The tab is for teams tasks, so it links directly to Planner. Users won't be able to add a To Do tab to a channel but any tasks that are assigned to a user in Planner show up in To Do. 

The **Published lists** tab only shows for a user if your organization uploaded a team hierarchy and the user is in a team that's defined in the hierarchy. If a user is in a team in the hierarchy, they can publish or receive tasks lists and view reporting for received lists.

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
## Publishing tasks

### Scenario

