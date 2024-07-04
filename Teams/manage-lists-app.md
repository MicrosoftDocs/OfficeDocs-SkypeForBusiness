---
title: Manage the Lists app for your organization
author: lana-chin
ms.author: v-chinlana
manager: jtremper
ms.reviewer: mmulpuru
ms.date: 07/04/2024
ms.topic: conceptual
audience: admin
ms.service: msteams
search.appverid: MET150
searchScope:
  - Microsoft Teams
  - Microsoft Cloud for Healthcare
  - Microsoft Cloud for Retail
description: Learn how to manage the Lists app in Teams for users in your organization.
f1.keywords:
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - microsoftcloud-healthcare
  - microsoftcloud-retail
  - m365initiative-lists
  - m365-frontline
  - teams-1p-app-admin
  - highpri
appliesto: 
  - Microsoft Teams
ms.custom:
---

# Manage the Lists app for your organization in Microsoft Teams

## Overview of Lists

The Lists app in Microsoft Teams helps users in your organization track information, organize work, and manage workflows. With Lists, users can track data such as issues, assets, routines, contacts, inventory, incidents, loans, patients, and more. Users do this by using customizable views, rules, and alerts to keep everyone on the team in sync. The Lists app is available in Teams desktop, web, and mobile clients.

In Teams, users access Lists as a tab in a channel. Select **+** to open the tab gallery and add a new Lists app tab instance to a channel to get started.

:::image type="content" source="media/lists-tab.png" alt-text="The Lists app in the tab gallery in Teams." lightbox="media/lists-tab.png":::

Users can create new lists or pin existing lists from within the same team or from a different SharePoint site that they have access to. New lists can be created from scratch or from built-in templates. They can also be based on the structure of an existing list or by importing data from an Excel workbook. 

:::image type="content" source="media/lists-create-list.png" alt-text="The Lists app added as a tab in a channel, showing options for creating a new list." lightbox="media/lists-create-list.png":::

## Templates

Templates in Lists are tailored to common information tracking scenarios for users. Each template comes with a predefined list structure, form layouts, and formatting options at both a list view and a details view level to help users get started quickly. After selecting a template, users get a preview of what the list will look like, along with some sample data.

:::image type="content" source="media/lists-template-example.png" alt-text="The Event itinerary template in Lists." lightbox="media/lists-template-example.png":::

Here's some examples of how teams in your organization can use the predefined templates in Lists:

- Track issues and bring them to closure using the Issue tracker template.
- Organize all your event details with the Event itinerary template.
- Use the Patients template to record the needs and status of patients for health teams in your healthcare organization to monitor and coordinate care.
- Track the status of loan applications with the Loans template.

## Example scenario

A local post office is responsible for sorting and delivering mail in their district. Each morning, the post office has a team huddle to review daily goals, share announcements, and discuss known incidents.

After the huddle, mail carriers pick up their mail and start their delivery route. Incidents can occur along a route, for example, a vehicle accident, dog-related issue, or social unrest protest. When mail carriers encounter an incident, they use Teams on their mobile devices to record the incident details, which are tracked in a list in the team channel. Everyone on the team, including mail carriers in the field, can see this information and stay informed.

Before moving to Teams, mail carriers had to go back to the post office to complete a hard-copy form to report an incident, which was then entered in an Excel spreadsheet. Teams gives mail carriers a mobile first, experience where they can use Lists to report incidents in the field as they happen, share incident details with team members, have conversations about them on the channel, and drive incidents to resolution.

## What you need to know about Lists

### Lists is available in every team and channel

Lists is preinstalled for all Teams users and is available directly in the tab gallery of every team and channel. This means that users don’t have to go to the Teams app store to install it.

### Lists and SharePoint

Lists data is stored in the SharePoint team site. To learn more about how SharePoint interacts with Teams, see [Overview of Teams and SharePoint integration](SharePoint-OneDrive-interact.md).

Permissions set in SharePoint apply to lists created in the Lists app. By default, lists inherit permissions from the site to which they belong. These permissions govern the types of actions that users can do, such as whether they can create or edit lists. To learn more, see [Permission levels in SharePoint](/sharepoint/understanding-permission-levels) and [On-premises SharePoint Server user permissions and permission levels](/sharepoint/sites/user-permissions-and-permission-levels).

In certain scenarios, you might want to restrict what actions users can do in lists. For example, a person on a team edits a list view that shouldn't, which changes it for all team members. With restrictions, you can allow only the team owner or certain team members to edit list views. To learn more, see [Customize permissions for a SharePoint list or library](https://support.microsoft.com/office/customize-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782#ID0EAACAAA=Online,_2019,_2016,_2013).

> [!NOTE]
> At this point, owner and member permissions in a team aren't linked in any way to permissions in the team site that govern the behavior of lists or the Lists app. However, based on customer feedback and usage, this will be considered for a future iteration.  

### Limitations

With Lists, users get a desktop, web, and mobile experience. It's important to know that users can't create new lists or pin existing lists using Lists on the Teams mobile client yet. To view or edit a list on the Teams mobile client, a list must first be created or added using Lists in the Teams desktop or web client.

Guests can't create or delete a list. They can add list items to existing lists, start new conversations about list items, and reply to existing conversations about list items.

### Lists and the SharePoint app

If users in your organization created lists using the SharePoint app, those lists are automatically moved to Lists without any action needed from the user. To get the best and richest lists integration experience in Teams, use the Lists app and pin your existing lists.

## Set up Lists

### Enable or disable Lists in your organization

Lists is enabled by default for all Teams users in your organization. You can turn off or turn on the app at the org level on the [Manage apps](manage-apps.md) page in the Microsoft Teams admin center.

1. In the left pane of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**.
2. Do one of the following:

    - To turn off Lists for your organization, search for the Lists app, select it, and then select **Block**.
    - To turn on Lists for your organization, search for the Lists app, select it, and then select **Allow**.

### Enable or disable Lists for specific users in your organization

To allow or block specific users in your organization from using Lists, make sure Lists is turned on for your organization on the [Manage apps](manage-apps.md) page, and then create a custom policy for app permissions and assign it to those users. To learn more, see [Use app permission policies to control user access to apps](teams-app-permission-policies.md).

## Search the audit log for list events

Lists are enabled with enterprise level auditing. You can search for lists and list item events in the audit log in the Microsoft Purview portal or the Microsoft Purview compliance portal. To learn more, see [Search the audit log](/purview/audit-search).

For a list of audit events that are relevant to the Lists app in Teams, see [SharePoint list activities](/purview/audit-log-activities#sharepoint-list-activities).

Before you can search the audit log, you have to first turn on auditing in the Microsoft Purview portal or the Microsoft Purview compliance portal. Keep in mind that audit data is only available from the point at which you turned on auditing.

## Power Automate, Power Apps, and Graph API

Lists supports [Power Automate](/power-automate/flow-types) for workflows and [Power Apps](/powerapps/maker/canvas-apps/customize-list-form) for list forms. Developers can use the [Lists API](/sharepoint/dev/sp-add-ins/working-with-lists-and-list-items-with-rest) to connect list data as a source through Microsoft Graph.

## Lists data

The Lists app is based on SharePoint and Lists data is stored in the SharePoint team site. For more information, see [Data Residency for SharePoint and OneDrive](/microsoft-365/enterprise/m365-dr-workload-spo).

## Give feedback or report an issue
  
To send us feedback or report an issue, select **Settings and more** (**…**) in Teams, and then choose **Help** > **Give feedback**. Enter your feedback or details about the issue you're experiencing. Indicate at the beginning of your feedback report that you're sending feedback about Lists so we can easily identify Lists issues.

## Related articles

- [Lists help documentation](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db)
