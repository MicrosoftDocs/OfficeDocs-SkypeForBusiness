---
title: Manage Microsoft 365 connectors and custom connectors
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 01/30/2023
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

Connectors in Microsoft Teams deliver content and service updates directly from third-party services into a Teams channel. Using connectors, the users receive updates from popular services such as Trello, Wunderlist, GitHub, and Azure DevOps Services. The updates are posted directly into the chat stream. This functionality makes it easy for all the team members to stay in sync and quickly receive the relevant information.

Microsoft 365 connectors are used with both Teams and Microsoft 365 groups. You can use the same connectors in Teams and Microsoft Exchange.

<!--- However, if you disable any connectors configured for a Microsoft 365 group, it also disables the ability for the Microsoft 365 group to create connectors. --->

If the team permissions allow it, any member of a team can add a connector in the team, and all team members are notified of activities from that service. Any team member with the permissions to add or remove can modify connectors setup by other members.

## Enable or disable connectors in Teams

The Exchange Online PowerShell v2 module uses modern authentication and works with multi-factor authentication (MFA) to connect to all Exchange related PowerShell environments in Microsoft 365. Admins can use Exchange Online PowerShell to disable connectors for an entire tenant or a specific group mailbox, affecting all users in that tenant or mailbox. It isn't possible to disable for a few specific users.

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

## Considerations when using Connectors in Teams

* Connectors are disabled by default in the Government Cloud Community (GCC) environments. To enable those, set the `ConnectorsEnabled` or `ConnectorsEnabledForTeams` parameters to `$true` with the `SetOrganizationConfig` cmdlet. Connect to the [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps&preserve-view=true).

* If the user who added a connector to a team leaves the team, the connector continues to work.

* Jenkins connector is scheduled for release on Feb 28, 2023.

* The following connectors aren't available for use January 2023 onwards:

  * Aha!
  * Airbrake
  * Aircall
  * App Links
  * AppSignal
  * Beanstalk
  * Bing News
  * Bitbucket
  * Bitbucket Server
  * Buddy
  * BugSnag
  * Buildkite
  * CATS
  * Chatra
  * CircleCI
  * CodeShip
  * Constant Contact
  * GetResponse
  * Ghost Inspector
  * Google Analytics
  * Groove
  * Heroku
  * Honeybadger
  * Intercom
  * Logentries
  * Mailchimp
  * Microsoft Forms
  * New Relic
  * Opsgenie
  * PagerDuty
  * Papertrail
  * Pingdom
  * ivotal Tracker
  * Raygun
  * Rollbar
  * Runscope
  * SatisMeter
  * Semaphore
  * Sentry
  * SharePoint News
  * Simple In/Out
  * Stack Exchange
  * status.io
  * SUBVERSION
  * Team Foundation Server (TFS)
  * TestFairy
  * Travis CI
  * Trello
  * Uptodown
  * Userlike
  * Wrike
  * XP-Dev
  * Zendesk

## Update URL of a connector

The Teams connectors are transitioning to a new URL to enhance security. During transition, you'll receive a notification to update the configured connector. Update your connector at the earliest to prevent any disruption to connector services. To update your connector:

1. In the connectors configuration page, check for **Attention Required** message next to the configured connector.

   :::image type="content" source="media/teams-attention-required-message.png" alt-text="Screenshot of the Attention Required message.":::

1. To recreate the connection for incoming webhook connectors, select **Update URL** and use the generated webhook URL.

   :::image type="content" source="media/teams-update-url-option.png" alt-text="Screenshot of the Update URL button.":::

1. For other connector types, remove the connector and recreate the connector configuration. A **URL is up-to-date** message appears.

   :::image type="content" source="media/teams-url-updated.png" alt-text="Screenshot of the URL is up-to-date message.":::

## Related articles

* [Overview of custom connectors and webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors)
* [How to create Office 365 connectors](/microsoftteams/platform/webhooks-and-connectors/how-to/connectors-creating)
