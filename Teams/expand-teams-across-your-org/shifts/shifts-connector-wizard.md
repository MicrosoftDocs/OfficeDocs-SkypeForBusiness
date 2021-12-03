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

The Shifts connector wizard in the Microsoft 365 admin center makes it easy to integrate the Shifts app in Microsoft Teams with your workforce management (WFM) system. After you set up a connection, your frontline workers can seamlessly view and manage their schedules in your WFM system from within Shifts.

The wizard configures the Shifts connector, creates a connection to your WFM system, and applies the sync settings and team mappings that you choose. Sync settings determine the schedule information that's synced between your WFM system and Shifts. Team mappings define the sync relationship between your WFM sites and teams in Teams. You can map to existing teams and new teams, which you can create in the wizard.

You can set up multiple connections, each with different sync settings. For example, if your organization has multiple locations with different schedule requirements, create a connection with unique sync settings for each location. Keep in mind that a WFM site can only be mapped to one team at any given time. If a WFM site is already mapped to a team, it can't be mapped to another team.

With your WFM system as the system of record, your frontline workers can see and swap shifts, manage their availability, and request time off in Shifts on their devices. Frontline managers can continue to use your WFM system to set up schedules.

Currently, the wizard supports the [Microsoft Teams Shifts connector for Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder). This connector enables you to integrate Shifts with Blue Yonder to manage your schedules and keep them up to date. In this article, we walk you through how to run the wizard to set up a connection to Blue Yonder through the connector.

> [!NOTE]
> You can also use PowerShell to integrate Shifts with Blue Yonder. To learn more, see [Use PowerShell to connect Shifts to your Blue Yonder workforce management system](shifts-connector-blue-yonder-powershell-setup.md).

## Before you begin

You must be a Microsoft 365 global admin to run the wizard.

### Prerequisites
<a name="prerequisites"> </a>
[!INCLUDE [shifts-connector-prerequisites](../../includes/shifts-connector-prerequisites.md)]

- The teams you want to map don't have any schedules. If a team has an existing schedule, [remove the schedule from the team](#remove-schedules-from-teams-you-want-to-map) before you map a Blue Yonder site to it. Otherwise, you'll see duplicate schedules.

## Remove schedules from teams you want to map
<a name="remove_schedules"> </a>

> [!NOTE]
> Complete this step if you're mapping Blue Yonder sites to existing teams that have schedules. If you're mapping to teams that don't have any schedules or if you're creating new teams to map to, you can skip this step.

Use PowerShell to remove schedules from teams.

1. First, you'll need to install the PowerShell modules and get set up. Follow the steps to [set up your environment](shifts-connector-powershell-manage.md#set-up-your-environment).
1. Run the following command:

    ```powershell
    Remove-CsTeamsShiftsScheduleRecord -TeamId <Teams team ID> -DateRangeStartDate <start time> -DateRangeEndDate<end time> -ClearSchedulingGroup:$false -EntityType <the scenario entities that you want to remove, the format is @(scenario1, scenario2, ...)> -DesignatedActorId <Teams team owner ID>
    ```

    Schedule data will be removed for the date and time range that you specify.

To learn more, see Remove-CsTeamsShiftsScheduleRecord.

## Run the wizard

### Get started

1. In the left navigation of the [Microsoft 365 admin center](https://admin.microsoft.com/), choose **Setup**, and then select the **Frontline workers** collection or go to the **Apps and updates** section.
1. Under **Connect you workforce management system**, select **View.** Here, you can learn more about Shifts connectors and the frontline worker and manager experience when you connect Shifts to your WFM system.
1. When you're ready, select **Get started**.
1. Select **Next** to create a Blue Yonder connection.

### Enter connection details
<a name="connection_details"> </a>

1. On the Connection details page, give your connection a unique name. It can't be longer than 128 characters or have any special characters.
1. Enter your Blue Yonder service account name and password and service URLs.
1. When you're done, select **Next** to test the connection with the settings you entered.

### Choose sync settings
<a name="sync"> </a>

On the Sync settings page, you choose the information to sync from Blue Yonder to Shifts, whether Shifts users can make changes to the data, and the sync frequency.

1. Enter your Microsoft 365 system account.
<a name="email"> </a>

1. Under **Email notification recipients**, choose who receives email notifications about this connection. You can add individual users and groups. The email notifications contain information about connection setup status and any issues or errors that may occur after the connection is set up.
1. Under **Schedule and shifts**, choose the Blue Yonder data that Shifts users can see or change, and then set the sync frequency.
1. Under **Requests**, choose the types of requests that Shifts users can see and create.
1. When you're done choosing your settings, select **Create connection**.

### Map Blue Yonder sites to teams
<a name="sites"> </a>

Choose the Blue Yonder sites you want to connect to Shifts. You can select up to 100 sites.
<a name="team_mapping"> </a>

Then, map each Blue Yonder site that you selected to a team in Teams. You can map a site to an existing team or you can create a new team.
#### To map a site to an existing team:
<a name="search_teams"> </a>

1. Select the checkbox next to the site name.
2. In the pane, search for the team, and then select it. Keep in mind that teams that are already mapped to a site don't show up in the search.
3. Choose the time zone and closest city.

#### To map a site to a new team:

1. Select the checkbox next to the site name.
2. In the pane, choose **Create a new team**, and then:
    1. Enter a name for your team, choose a privacy setting, and add one or more team owners.
    2. Add users to the team. You can also add groups.
    3. Choose whether to create your team from scratch or from a team template. Team templates come with predefined channels and tabs, which optimize the team for a particular business need or project.
3. Choose the time zone and closest city.

### Review and finish

Review your settings. If you need to make changes to any site mappings, choose **Edit** to do so. When you're ready, select **Finish**.

You’ll see a message to confirm that we received your request along with an operation ID. Make a note of the operation ID for future reference.

The wizard sets up and creates the connection and maps the sites to the teams you selected. This process may take some time to complete. The recipients you chose will receive email notifications about setup status.

Select **Done** to exit the wizard.

You’re on your way but you’re not done yet! Be sure to check your email. You'll receive a confirmation that we received your request along with a link to how you can check setup status.

> [!NOTE]
> If an issue or error occurs in a connection after it's set up, you'll get notified in email. Follow the instructions in the email to troubleshoot the issue.

## If you need to make changes to a connection
<a name="update_connection"> </a>

After a connection is set up, you use PowerShell to make changes to it. For example, you can update sync settings, team mappings, and disable a connection by turning off sync. For step-by-step guidance, see [Use PowerShell to manage your Shifts connection to Blue Yonder](shifts-connector-powershell-manage.md).

## Related articles

- [Shifts connectors](shifts-connectors.md)
- [Use PowerShell to manage your Shifts connection to Blue Yonder](shifts-connector-powershell-manage.md)
- [Manage the Shifts app in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
