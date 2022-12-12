---
title: Manage Microsoft 365 connectors and custom connectors
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 09/01/2022
ms.collection: 
  - M365-collaboration
ms.reviewer: lucarras
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn how connectors keep your team updated by frequently delivering content and updates directly into a Teams channel for services you use.
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: seo-marvel-mar2020
---

# Manage Microsoft 365 connectors and custom connectors

To keep your team updated, the connectors deliver frequently used content and service updates directly into a Teams channel. With connectors, your Teams users can receive updates from popular services such as Trello, Wunderlist, GitHub, and Azure DevOps Services. The updates are posted directly into the chat stream in their team.

Microsoft 365 connectors are used with both Microsoft Teams and Microsoft 365 groups. They make it easy for all members to stay in sync and quickly receive the relevant information. You can use the same connectors in both, Microsoft Teams and Microsoft Exchange. However, if you disable any connectors configured for a Microsoft 365 group, it also disables the ability for the Microsoft 365 group to create connectors.

Any member of a team can connect their team to popular cloud services with the connectors if the team permissions allow, and all team members are notified of activities from that service. Connectors continue to work after the member who initially set up the connector leaves. Any team member with the permissions to add or remove can modify connectors setup by other members.

## Enable or disable connectors in Teams

The Exchange Online PowerShell V2 module uses modern authentication and works with multi-factor authentication (MFA) to connect to all Exchange related PowerShell environments in Microsoft 365. Admins can use Exchange Online PowerShell to disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox. It isn't possible to disable for few specific users. Also, connectors are disabled by default for Government Community Cloud (GCC) environments.

> [!NOTE]
> Connectors are disabled by default in the Government Cloud Community (GCC) environments. To enable those, set the `ConnectorsEnabled` or `ConnectorsEnabledForTeams` parameters to `$true` with the `SetOrganizationConfig` cmdlet. Connect to the [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps&preserve-view=true).

The tenant setting overrides the group setting. For example, if an admin enables connectors for the group and disables them on the tenant, connectors for the group is disabled. To enable a connector in Teams, [connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) using modern authentication with or without MFA.

To enable or disable a connector, execute the following commands in Exchange Online PowerShell:

* To disable connectors for the tenant: `Set-OrganizationConfig -ConnectorsEnabled:$false`.
* To disable actionable messages for the tenant: `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$false`.
* To enable connectors for Teams, execute the following commands:
  * `Set-OrganizationConfig -ConnectorsEnabled:$true`
  * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
  * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

For more information on PowerShell module exchange, see [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true). To enable or disable Outlook connectors, [connect apps to your groups in Microsoft Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab).

## Publish connectors for your organization

To make a custom connector available to your organization's users, upload a custom connector app to your org's app catalog. End-users within the org can install, configure, and use the connector in a team.

> [!IMPORTANT]
> Custom connectors are not available in Government Community Cloud (GCC), Government Community Cloud-High (GCCH), and Department of Defense (DOD) environments.

To use connectors in a team or a channel, open the More Options menu from the upper right corner of a channel. From the menu, select **Connectors** and then locate or search for the required connector. Configure the selected connector if necessary.

:::image type="content" source="media/connectors-selection-ui.png" alt-text="Add connectors to your channel in Teams from the More options in the upper right corner of the channel.":::

## Update URL of a connector

The Teams connectors are transitioning to a new URL to enhance security. During transition, you'll receive a notification to update the configured connector. Update your connector at the earliest to prevent any disruption to connector services. To update your connector:

1. In the connectors configuration page, check for **Attention Required** message next to the configured connector.

   :::image type="content" source="media/teams-attention-required-message.png" alt-text="Screenshot of the Attention Required message.":::

1. To recreate the connection for incoming webhook connectors, select **Update URL** and use the generated webhook URL.

   :::image type="content" source="media/teams-update-url-option.png" alt-text="Screenshot of the Update URL button.":::

1. For other connector types, remove the connector and recreate the connector configuration. A **URL is up-to-date** message appears.

   :::image type="content" source="media/teams-url-updated.png" alt-text="Screenshot of the URL is up-to-date message.":::

## Related articles

* [Custom connectors and webhooks overview](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors)
* [Create Office 365 connectors](/microsoftteams/platform/webhooks-and-connectors/how-to/connectors-creating)
