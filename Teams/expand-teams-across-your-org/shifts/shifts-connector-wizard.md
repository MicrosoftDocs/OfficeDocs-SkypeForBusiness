---
title: Use the Shifts connector wizard to connect your workforce management system
author: lanachin
ms.author: v-lanachin
ms.reviewer: 
manager: samanro
ms.topic: article
audience: admin
ms.service: msteams
search.appverid: MET150
description: Learn how to use the Shifts connector wizard to integrate Shifts in Teams to your workforce management system.
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_FLW
appliesto: 
  - Microsoft Teams
---

# Use the Shifts connector wizard to connect your workforce management system

## Overview

The Shifts connector wizard in the Microsoft 365 admin center makes it easy to integrate the Shifts app in Microsoft Teams with your workforce management (WFM) system. After the connection is set up, your frontline workers can seamlessly view and manage their schedules from your WFM system using Shifts.

The wizard configures the Shifts connector, creates a connection to your WFM system, and applies the sync settings and team mappings that you choose. Sync settings determine the features that are enabled in Shifts and schedule information that's synced between your WFM system and Shifts. Team mappings define the relationship between your WFM sites and teams in Teams. You can map to existing teams and new teams, which you can create in the wizard.

You can set up multiple connections, each with different sync settings. For example, if your organization has multiple locations with different schedule requirements, create a connection with unique sync settings for each location. Keep in mind that a WFM site can only be mapped to one team at any given time. If a WFM site is already mapped to a team, that site can't be mapped to another team.

With your WFM system as the system of record, your frontline workers can see and swap shifts, manage their availability, and request time off in Shifts on their devices. Frontline managers can continue to use your WFM system or Shifts to set up schedules.

> [!NOTE]
> We currently support [Blue Yonder](https://blueyonder.com/solutions/workforce-management). We’re working with our partners to support additional WFM systems.

This article walks you through how to run the wizard to create a Shifts to Blue Yonder connection.

## Before you begin

You must be a Microsoft 365 global admin or Shifts connector admin to run the wizard. Before you get started, make sure you meet the following prerequisites:

- Blue Yonder version 2020.3 and 2021
- At least one team set up in Teams
- If a team has an existing schedule, you'll have to remove the schedule from the team before you can map it. Otherwise, you'll see duplicate schedules.  

You'll also need to know your Blue Yonder service account name and password and service URLs. If you don’t have this information, contact your Blue Yonder delivery partner or technical account manager.

## Run the wizard

1. In the left navigation of the [Microsoft 365 admin center](https://admin.microsoft.com/), choose **Setup**, and then select the **Frontline workers** collection or go to the **Apps and updates** section.
1. Under **Connect you workforce management system**, select **View.** Here, you can learn more about Shifts connectors and the frontline worker and manager experience when you connect Shifts to your workforce management system.
1. When you're ready, select **Get started**.
1. Select **Next** to create a Blue Yonder connection.
1. On the Connection details page:

    1. Give your connection a name.
    2. Enter your Blue Yonder service account name and password and service URLs.

        |Service URL |Description  |
        |---------|---------|
        |Federated authentication URL   |         |
        |Cookie authentication URL    |         |
        |Employee self-service URL    |         |
        |Retail web URL   |         |
        |Administration API URL   |         |

    3. Select **Next** to test the connection with the settings you entered.

1. On the Sync settings page, you choose the information to sync from Blue Yonder to Shifts, whether Shifts users can make changes to the data, and the sync frequency.
    1. Enter your Microsoft 365 system account.
    2. Choose who receives email notifications about this connection. You can add individual users and groups. The email notifications contain information about connection setup status. Use this information to troubleshoot any errors that may occur.
    3. Under **Requests**, choose the types of requests that Shifts users can see and create.
    4. Under **Schedule and shifts**, choose the data that Shifts users can see or change.
    5. Under **Sync frequency**, specify how often data is synced between Blue Yonder and Shifts.
    6. When you're done choosing your settings, select **Create connection**.

1. Choose the Blue Yonder sites you want to connect to Shifts. You can select up to 100 sites.
1. Map each Blue Yonder site that you selected to a team in Teams. You can map a site to an existing team or you can create a new team.

    To map a site to an existing team:

    1. Select the check box next to the site name.
    2. In the pane, search for the team, and then select it. Keep in mind that teams that are already mapped to a site don't show up in the search.
    3. Choose the time zone and closest city.

    To map a site to a new team:

    1. Select the check box next to the site name.
    2. In the pane, choose **Create a new team**, and then:
        1. Enter a name for your team, choose a privacy setting, and add one or more team owners.
        2. Add users to the team. You can also add groups.
        3. Choose whether to create your team from scratch or from a team template. Team templates come with predefined channels and tabs, which optimize the team for a particular business need or project.
    3. Choose the time zone and closest city.

1. Review your settings. If you need to make changes to any site mappings, choose **Edit** to do so. <br/>
 When you're ready, select **Finish**.
1. You’ll see a message to confirm that we received your request and are working on it, along with an operation ID. Make a note of the operation ID for future reference. We refer to it in the email notifications.

    The wizard sets up and creates the connection and maps the sites to the teams you selected. It may take some time to complete. The recipients you chose will receive email notifications about connection setup status.

    Select **Done** to exit the wizard.

1. You’re on your way but you’re not done yet! Next, check out the [What to do after running the wizard](#what-to-do-after-running-the-wizard) section of this article.


## What to do after running the wizard

After you run the wizard:

- Check your email. You'll receive a confirmation that we received your request along with a link to how you can check the status. If an error occurred, you'll get notified. Follow the instructions in the email to troubleshoot the issue.

## Related articles

- [Manage the Shifts app in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
