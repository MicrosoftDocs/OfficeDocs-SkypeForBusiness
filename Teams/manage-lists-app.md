---
title: Manage the Lists app for your organization
author: LanaChin
ms.author: v-lanac
ms.reviewer: anach,v-jasuk
manager: serdars
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to set up and manage the Lists app in Teams for users in your organization.
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.custom: 
---

# Manage the Lists app for your organization in Microsoft Teams

## Overview of Lists

The Lists app in Microsoft Teams helps users in your organization track information and organize work. With Lists, users can track data such as issues, assets, routines, contacts, inventory and more using customizable views, smart rules, and alerts to keep everyone on the team in sync.

In Teams, users access Lists as a tab in a channel. Click **+** to add a new tab to a channel, and then select the Lists app to get started. Users can create new lists or add existing lists. New lists can be created from scratch, from built-in templates, or by importing data from Excel. Lists is available in Teams desktop, web, and mobile clients.

### Scenarios

## What you need to know about Lists

With Lists, users get a desktop, web, and mobile experience. It's important to know that that users can't create new lists or add existing lists using Lists on the Teams mobile client. To view or edit a list on the Teams mobile client, the list must first be created or added using Lists on the Teams desktop or web client.

Lists data is stored in the SharePoint Online team site. To learn more about how SharePoint Online interacts with Teams, see [How SharePoint Online and OneDrive for Business interact with Teams](SharePoint-OneDrive-interact.md).

If users in your organization created lists using the SharePoint Lists app, those lists are automatically moved to Lists. 

Difference between SharePoint lists and Lists lists?
SharePoint admin controls for lists?  Permissions, locale, views, etc?

## Set up Lists

### Enable or disable Lists in your organization

Lists is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

1. In the left navigation of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps** .
2. Do one of the following:

    - To turn off Lists for your organization, search for the Lists app, select it, and then click **Block**.
    - To turn on Lists for your organization, search for the Lists app, select it, and then click **Allow**.

### Enable or disable Lists for specific users in your organization

To allow or block specific users in your organization from using Lists, make sure Lists is turned on for your organization on the [Manage apps](manage-apps.md) page, and then create a custom app permission policy and assign it to those users. To learn more, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

### Use an app setup policy to pin Lists to Teams

App setup policies let you customize Teams to highlight the apps that are most important for users in your organization. The apps that you set in a policy are pinned to the app bar&mdash;the bar on the side of the Teams desktop client and at the bottom of the Teams mobile clients&mdash;where users can quickly and easily access them. 

To pin the Lists app for your users, you can edit the global (Org-wide default) policy or create and assign a custom app setup policy.To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

## Search the audit log for Lists events?

You can search the audit log to view Lists activity in your organization. To learn more about how to search the audit log and to see a list of Lists activities that are logged in the audit log, see [Search the audit log for events in Teams](audit-log-events.md).

Before you can search the audit log, you have to first turn on auditing in the [Security & Compliance Center](https://protection.office.com). To learn more, see [Turn audit log search on or off](https://support.office.com/article/Turn-Office-365-audit-log-search-on-or-off-e893b19a-660c-41f2-9074-d3631c95a014). Keep in mind that audit data is only available from the point at which you turned on auditing.

## Power Automate?  Graph API?

## Related topics

