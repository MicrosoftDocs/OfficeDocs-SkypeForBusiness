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

# Manage the Lists app for your organization in Microsoft Teams - WORK IN PROGRESS

## Overview of Lists

The Lists app in Microsoft Teams helps users in your organization track information and organize work. With Lists, users can track data such as issues, assets, routines, contacts, inventory, and more using customizable views, rules, and alerts to keep everyone on the team in sync.

In Teams, users access Lists as a tab in a channel. Click **+** to add a new tab to a channel, and then select the Lists app to get started. Users can create new lists or add existing lists. New lists can be created from scratch, from ready-made templates, or by importing data from Excel. Lists is available in Teams desktop, web, and mobile clients.

![Screenshot of how to create a list in the Lists app](media/lists-create-list.png)

Templates in Lists are tailored to common information tracking scenarios. Each template comes with a predefined structure, forms, and formatting to help users get started quickly. After selecting a template, users get a preview of what the list will look like, along with sample data. Here's a few examples of how teams in your organization can use templates in Lists:

- Track issues and bring them to closure using the Issue tracker template.
- Organize all your event details with the Event itinerary template.
- Record the needs and status of patients so care teams in your healthcare organization can monitor and coordinate care.
- Track the status of loan applications with the Loans template.

To learn more about using Lists, see [LINK TO END-USER DOC].

### Example scenario

A local post office is responsible for sorting and delivering mail in their district every day. Each morning the post office has a team huddle to discuss daily goals, announcements, and known incidents, which are displayed on a cork board.  

After their huddle, mail carriers pick up their mail and start their delivery route. While delivering mail, incidents can occur in the form of a vehicle accident, dog incident, or social unrest protest. Postal carriers don’t have a secure and compliant way to share incident information with colleagues. When an incident occurs, they have go back to the post office to complete a hard-copy form to report an incident which is entered in an Excel spreadsheet.  

Lists in Teams gives post carriers a mobile first, experience where they can report incidents in the field, share incident information with colleagues, and manage incident information in a list view. 

## What you need to know about Lists

Lists is pre-installed for all Teams users and is available directly in the tab gallery of every team and channel. This means that users don't have to go to the Teams app store to install it.

With Lists, users get a desktop, web, and mobile experience. It's important to know that users can't create new lists or add existing lists using Lists on the Teams mobile client. To view or edit a list on the Teams mobile client, a list must first be created or added using Lists on the Teams desktop or web client.

Lists data is stored in the SharePoint Online team site. To learn more about how SharePoint Online interacts with Teams, see [How SharePoint Online and OneDrive for Business interact with Teams](SharePoint-OneDrive-interact.md).

If users in your organization created lists using the SharePoint Lists app, those lists are automatically moved to Lists without any action needed from the user.

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

To pin the Lists app for your users, you can edit the global (Org-wide default) policy or create and assign a custom app setup policy. To learn more, see [Manage app setup policies in Teams](teams-app-setup-policies.md).

## Search the audit log for list events

You can search the audit log to view list activity in your organization. To learn more, see [Search the audit log in the Security & Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance#sharepoint-list-activities).

Before you can search the audit log, you have to first turn on auditing in the [Security & Compliance Center](https://protection.office.com). Keep in mind that audit data is only available from the point at which you turned on auditing.

## Power Automate, Power Apps, and Graph API

Lists supports [Power Automate](https://preview.flow.microsoft.comconnectors/shared_sharepointonline/?slug=sharepoint) for workflows and [Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form) for list forms. Developers can use the [Lists API](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/working-with-lists-and-list-items-with-rest) to connect list data as a source through Microsoft Graph.

## Related topics

