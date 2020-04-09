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

Transition into Planner app 
Users will see Personal lists and Team lists 
Note that they will get a desktop experience and mobile experience.  If the app is installed for a user on desktop, they will also see it on mobile. 
Ability to disable Exchange license (soon to be To Do license instead) to hide personal lists 
Publishing tab only shows for a user if (a) your organization has uploaded a team hierarchy and (b) the user is in a team in the hierarchy (and can therefore either publish or can receive lists and see reporting for received lists) 
How to enable publishing by uploading a CSV (the doc you created) 
PowerAutomate and Graph APIs  for To Do and Planner - Refer to To Do and Planner documentation 
App setup policy and app permissions policy - reminders and links to that documentation 
Guest user behavior 



## Set up Tasks

### Enable or disable Tasks in your organization

Tasks is enabled by default for all Teams users in your organizaition. You can turn off or turn on the app at the org level on the Manage apps page in the Microsoft Teams admin center. 

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. In the list of apps, do one of the following:

    - To turn off Tasks for your organization, search for the Tasks app, select it, and then click **Block**.
    - To turn on Tasks for your organization, search for the Tasks app, select it, and then click **Allow**.

### Enable or disable Tasks for specific users in your organization

To allow or block specific users in your organization from using Tasks, make sure Tasks is turned on for your organization on the [Manage apps](../manage-apps.md) page, and then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](../teams-app-permission-policies.md).

### Use an app setup policy to pin Tasks to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps you set in a policy are pinned to the app bar&mdash;the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients&mdash;where users can quickly and easily access them.

You can edit the global (Org-wide default) policy or create and assign a custom app setup policy to pin the Tasks app for your users. To learn more, see [Manage app setup policies in Teams](../teams-app-setup-policies.md).