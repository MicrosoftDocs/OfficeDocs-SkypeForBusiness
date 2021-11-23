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

The Shifts connector wizard in the Microsoft 365 admin center makes it easy to integrate the Shifts app in Microsoft Teams with your workforce management (WFM) system. After a connection is set up, your frontline workers can seamlessly view and manage their schedules in your WFM system from within Shifts.

The wizard configures the [Shifts connector](shifts-connectors.md), creates a connection to your WFM system, and applies the sync settings and team mappings that you choose. Sync settings determine the features that are enabled in Shifts and schedule information that's synced between your WFM system and Shifts. Team mappings define the relationship between your WFM sites and teams in Teams. You can map to existing teams and new teams, which you can create in the wizard.

You can set up multiple connections, each with different sync settings. For example, if your organization has multiple locations with different schedule requirements, create a connection with unique sync settings for each location. Keep in mind that a WFM site can only be mapped to one team at any given time. If a WFM site is already mapped to a team, it can't be mapped to another team.

With your WFM system as the system of record, your frontline workers can see and swap shifts, manage their availability, and request time off in Shifts on their devices. Frontline managers can continue to use your WFM system or use Shifts to set up schedules.

> [!NOTE]
> We currently support [Blue Yonder](https://blueyonder.com/solutions/workforce-management). We’re working with our partners to support additional WFM systems.

In this article, we walk you through how to run the wizard to set up a Shift to Blue Yonder connection.

> [!NOTE]
> You can also use PowerShell integrate Shifts with your WFM system. To learn more, see [Use PowerShell to connect Shifts to your Blue Yonder workforce management system](shifts-connector-blue-yonder-powershell-setup.md).

## Before you begin

You must be a Microsoft 365 global admin to run the wizard.

### Prerequisites

[!INCLUDE [shifts-connector-prerequisites](../../includes/shifts-connector-prerequisites.md)]

Before you get started, make sure you have the following prerequisites:

- Blue Yonder version 2020.3, 2021.1, or 2021.2. </br>If you have 2020.3 or 2021.1, we recommend applying the 2020.3.0.4 or 2021.1.0.3 patch. The patch has a fix required for users to update their availability in Shifts.
- Blue Yonder service account name and password and service URLs. </br>If you don’t have this information, contact your Blue Yonder delivery partner or technical account manager. The account is created at the root enterprise level by a Blue Yonder enterprise administrator and must have APIAccess, Client Admin, and Store Manager access. The account and password are required to create a connection.
- Federated SSO authentication is enabled in your Blue Yonder environment. Contact your Blue Yonder delivery partner or technical account manager to make sure federated SSO is enabled. They'll need the following information:

    - federatedSSOValidationService: `https://amer.wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` where {tenantId} is your tenantId
     - proxyHeader: X-MS-AuthToken
- At least one team is set up in Teams.
- Microsoft 365 service account is added as a team owner to all teams you want to map.</br> This service account is an account that you create. Create it in Azure Active Directory (Azure AD) and assign it a Microsoft 365 license. Then, add the account as a team owner to all teams that you want to map. The Shifts connector uses this account when syncing Shifts changes from Blue Yonder.

    We recommend that you create a service account specifically for this purpose and not use your user account.
- The teams you want to map do not have any schedules. If a team has an existing schedule, [remove the schedule from the team](#remove-schedules-from-teams-you-want-to-map) before you map a Blue Yonder site to it. Otherwise, you'll see duplicate schedules.

## Prepare to run the wizard

### Remove schedules from teams you want to map

> [!NOTE]
> Complete this step if you're mapping Blue Yonder sites to existing teams that have schedules. If you're mapping to teams that don't have any schedules or if you're creating new teams to map to, you can skip this step.

Use PowerShell to remove schedules from teams.

1. Follow the steps to [set up your environment](shifts-connector-powershell-manage.md#set-up-your-environment).
1. Run the following command:

    ```powershell
    Remove-CsTeamsShiftsScheduleRecord -TeamId <Teams team ID> -DateRangeStartDate <start time> -DateRangeEndDate<end time> -ClearSchedulingGroup:$false -EntityType <the scenario entities that you want to remove, the format is @(scenario1, scenario2, ...)> -DesignatedActorId <Teams team owner ID>
    ```

    Schedule data will be removed for the date and time range that you specify.

To learn more, see Remove-CsTeamsShiftsScheduleRecord.[ADDLINK to PowerShell cmdlet]

## Run the wizard

1. In the left navigation of the [Microsoft 365 admin center](https://admin.microsoft.com/), choose **Setup**, and then select the **Frontline workers** collection or go to the **Apps and updates** section.
1. Under **Connect you workforce management system**, select **View.** Here, you can learn more about Shifts connectors and the frontline worker and manager experience when you connect Shifts to your WFM system.
1. When you're ready, select **Get started**.
1. Select **Next** to create a Blue Yonder connection.
1. On the Connection details page:

    1. Give your connection a name.
    2. Enter your Blue Yonder service account name and password and service URLs.
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
1. You’ll see a message to confirm that we received your request along with an operation ID. Make a note of the operation ID for future reference.

    The wizard sets up and creates the connection and maps the sites to the teams you selected. This process may take some time to complete. The recipients you chose will receive email notifications about setup status.

    Select **Done** to exit the wizard.

You’re on your way but you’re not done yet! Be sure to check your email. You'll receive a confirmation that we received your request along with a link to how you can check setup status.

> [!NOTE]
> If an issue or error occurs in a connection after it's set up, you'll get notified in email. Follow the instructions in the email to troubleshoot the issue.

## If you need to make changes to a connection

You can use PowerShell to make changes to a connection after it's set up. For example, you can update sync settings, team mappings, or disable a connection. You can also view connection health and settings. For step-by-step guidance, see [Link to PowerShell article]().

## Related articles

- [Shifts connectors](shifts-connectors.md)
- [Manage the Shifts app in Teams](manage-the-shifts-app-for-your-organization-in-teams.md)
