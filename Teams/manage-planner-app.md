---
title: Manage the Planner app for your organization in Microsoft Teams
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.topic: conceptual
ms.service: msteams
ms.reviewer: asobhan, andfried
ms.date: 
search.appverid: MET150
searchScope: 
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
  - Microsoft Cloud for Retail
audience: admin
description: Learn how to manage the Planner app for users in your organization.
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - m365-frontline
  - teams-1p-app-admin
  - highpri
---

# Manage the Planner app for your organization in Microsoft Teams

## Overview of Planner

The Planner app in Microsoft Teams brings together the simplicity of [Microsoft To Do](https://todo.microsoft.com/tasks/), the collaboration of Microsoft Planner, and the power of Planner premium to help your users get work done more efficiently. Users can access Planner as an app on the left side of Teams and as a tab in a channel within individual teams.

> [!NOTE]
> Prior to March 2024, this app was named Tasks by Planner and To Do.

:::image type="content" source="media/manage-planner-app.png" alt-text="Screenshot of the Planner app, showing the Assigned to me list in My Tasks." lightbox="media/manage-planner-app.png":::

## What you need to know about Planner

Planner is available as an app and as a tab in a channel. The app shows a user's individual tasks and shared tasks.

When a user opens the Planner app in Teams, they see:

- **My Day**: Shows tasks that are due today, along with any tasks that a user chooses to add to this view.
- **My Tasks**: This section includes:
  - **Private Tasks**: A dedicated place for a user to quickly create tasks in a default place.
  - **Assigned to me**: All tasks that are assigned to the user from Teams meeting notes, Microsoft Loop, Planner, and Planner premium.
  - **Flagged emails**: Emails the user flagged in Outlook show up as tasks here.
- **My Plans**: Shows all the user's To Do lists, basic plans, and premium plans.
- **New plan**: Create a new personal or shared plan directly in the app.

> [!NOTE]
> There's limited functionality when using the Planner app on Teams mobile. On mobile, users will only see plans that are added to a tab in a channel within a team.

Users can also use the Planner app to:

- Create new personal or shared plans.
- Get notifications about Planner tasks.

For organizations who want to streamline task management for frontline workers, Planner also includes capabilities that enable you to target, publish, and track tasks at scale across your frontline workforce. For example, corporate and regional leadership can create and publish task lists targeted to relevant locations, such as specific retail stores, and track progress through real-time reports. Managers can assign tasks to their staff and direct activities within their locations, and frontline workers have a prioritized list of their assigned tasks on mobile or desktop. To enable [task publishing](#task-publishing), first set up a team targeting hierarchy for your organization, which defines how all teams in the hierarchy are related to each other.

## Set up Planner

> [!IMPORTANT]
> Settings and policies that you configure for Planner for web will also apply to Planner in Teams.

### Enable or disable Planner in your organization

Planner is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Teams admin center.

1. In the left pane of the Teams admin center, go to **Teams apps** > **Manage apps**.
2. In the list of apps, do one of the following actions:

    - To turn off Planner for your organization, search for the Planner app, select it, and then select **Block**.
    - To turn on Planner for your organization, search for the Planner app, select it, and then select **Allow**.

> [!NOTE]
> If you can't find the Planner app, search for "Tasks by Planner and To Do". The app could still be in the process of being renamed.

### Enable or disable Planner for specific users in your organization

To allow or block specific users in your organization from using Planner, make sure Planner is turned on for your organization on the [Manage apps](manage-apps.md) page, and then create a custom policy for app permissions and assign it to those users. To learn more, see [Use app permission policies to control user access to apps](teams-app-permission-policies.md).

### Pin Planner to Teams

#### Use an app setup policy to pin Planner to Teams

App setup policies let you customize Teams to pin apps that are most important for your users.

To pin the Planner app for your users, you can edit the global (Org-wide default) policy or create and assign a custom policy in app setup policy. To learn more, see [Use app setup policies to pin and auto install apps for users](teams-app-setup-policies.md). 

For more information about the default app setup policy for users who are assigned an F license, see the [Tailored frontline app experience for frontline workers and managers](#tailored-frontline-app-experience-in-teams-for-frontline-workers-and-managers) section.

#### Tailored frontline app experience in Teams for frontline workers and managers

The tailored frontline app experience in Teams pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline) assigned to them. This feature is enabled by default, giving your frontline workers an out-of-the-box experience tailored to reflect workloads used by frontline employees.

As part of this experience, a handful of apps are pinned to the app bar&mdash;the bar on the side of the Teams desktop client and at the bottom of Teams mobile clients&mdash;where users can quickly and easily access them. Pinned apps include Viva Connections dashboard, Walkie Talkie, Shifts, and Planner. However, Planner might appear in the **…** menu on mobile because there are fewer app spots available in the app navigation.

To learn more, including how the experience works with app policies that you set, see [Tailor Teams apps for your frontline workers](/microsoft-365/frontline/pin-teams-apps-based-on-license?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

### A user's My Tasks is visible if the user is licensed for Exchange Online

If you don't want a user to see **My Tasks**, you can hide it. To hide **My Tasks**, [remove the user's Exchange Online license](/microsoft-365/admin/manage/remove-licenses-from-users). It's important to know that after you remove an Exchange Online license, the user no longer has access to their mailbox. Mailbox data is held for 30 days, after which the data will be removed and can't be recovered unless the mailbox is placed on [In-Place Hold or Litigation Hold](/exchange/security-and-compliance/in-place-and-litigation-holds).

We don't recommend removing an Exchange Online license for information workers, but there might be some scenarios where you can hide **My Tasks** in this way, such as for frontline workers who don't depend on email.

## Task publishing

With task publishing, your organization can [publish task lists](https://support.microsoft.com/office/publish-task-lists-to-create-and-track-work-in-your-organization-095409b3-f5af-40aa-9f9e-339b54e705df) targeted to specific locations (teams) across your organization to define and share a work plan to be completed at those locations.

- People on the publishing team, such as corporate or regional leadership, can create task lists and publish them to specific teams.
- Managers on the recipient teams can review the published task lists and assign individual tasks to team members.
- Frontline workers have a simple mobile experience to see tasks assigned to them. They can attach photos to show their work when appropriate and mark their tasks as completed.
- Publishers and managers can view reports to see assignment and completion status of tasks at each level, including by location (team), task list, and individual task.

Users create, manage, and publish task lists in the Planner app, by selecting the **My tasks & plans** dropdown menu, and then choosing **Publishing**. This menu only shows for a user if your organization [set up a team targeting hierarchy](#set-up-your-team-targeting-hierarchy) *and* the user is part of a team that's included in the hierarchy. The hierarchy determines whether the user can publish or receive task lists and view reporting for received lists.

:::image type="content" source="media/manage-planner-app-publishing.png" alt-text="Screenshot of the My tasks & plans dropdown menu, showing the Publishing option":::

### Example scenario

See this short [Task Publishing video](https://support.microsoft.com/office/publish-task-lists-to-create-and-track-work-in-your-organization-095409b3-f5af-40aa-9f9e-339b54e705df) with an example scenario.

### Set up your team targeting hierarchy

To enable task publishing in your organization, you have to first set up your team targeting schema in a .CSV file. The schema defines how all the teams in your hierarchy are related to each other and also defines the attributes that can be used to filter and select teams. After you create the schema, upload it to Teams to apply it to your organization. Members of the publishing team, such as the Retail Communications Manager in the example scenario, can then filter teams by hierarchy, attributes, or a combination of both to select the relevant teams that should receive the task lists, and then publish the task lists to those teams.

For steps on how to set up your team targeting hierarchy, see [Set up your team targeting hierarchy](set-up-your-team-hierarchy.md).

## Power Automate and Graph API

Planner supports Graph APIs for Planner and Power Automate for To Do. To learn more, see:

- [Planner tasks and plans API overview](/graph/planner-concept-overview)
- [Using Microsoft To Do with Power Automate](https://support.office.com/article/using-microsoft-to-do-with-power-automate-526e8f75-217b-46e0-9e06-44780b72c295)

## Data location

For more information about where your Planner data is stored, see [Data residency for other Microsoft services](/microsoft-365/enterprise/m365-dr-workload-other#planner).

To Do uses Exchange Online for data storage. To learn more, see [Review data storage and compliance in Microsoft To Do](https://support.microsoft.com/office/review-data-storage-and-compliance-in-microsoft-to-do-60c11889-b08b-4bfd-a7c0-1a28582b6161).

## Give feedback or report an issue
  
To send us feedback or report an issue, select **Help** near the bottom of the left pane in Teams, and then select **Report a problem**. Select **Planner**, and then enter your feedback or details about the issue you're experiencing.