---
title: Manage Microsoft 365 connectors and custom connectors
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 02/14/2024
ms.collection: 
  - M365-collaboration
ms.reviewer: vivg
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

Connectors in Microsoft Teams deliver content and service updates directly from third-party services into a Teams channel. By using connectors, users can receive updates from popular services such as Azure DevOps Services, Trello, Wunderlist, GitHub, and more. Connectors post these updates directly into the chat stream. This functionality makes it easy for all the team members to stay in sync and quickly receive the relevant information.

Teams and Microsoft 365 groups use connectors. You can use the same connectors in Teams and Microsoft Exchange.

Any team member can add a connector to a channel, if the team permissions allow it. The updates from the service, that the connector fetches information from, notifies all the team members. Any team member with the permissions to add or remove can modify connectors setup done by other members.

## Enable or disable connectors in Teams

The Exchange Online PowerShell v2 module uses modern authentication and works with multifactor authentication (MFA) to connect to all Exchange related PowerShell environments in Microsoft 365. Admins can use Exchange Online PowerShell to disable connectors for an entire organization or a specific group mailbox. If a connector is disabled, it affects all users in that org or mailbox. You can't disable a connector for a few specific users.

The organization setting overrides the group setting. For example, if an admin enables connectors for the group and disables the same connectors for the organization, then the connectors are disabled for the group. To enable a connector in Teams, [connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps#connect-to-exchange-online-powershell-using-modern-authentication-with-or-without-mfa&preserve-view=true) using modern authentication with or without MFA.

To enable or disable a connector, execute the following commands in Microsoft Exchange Online PowerShell:

1. Open PowerShell as an administrator.
1. Use the command `Import-Module ExchangeOnlineManagement` to import the Microsoft Exchange module.
1. To disable connectors in your organization, use the command `Set-OrganizationConfig -ConnectorsEnabled:$false`.
1. To connect the admin account, use the command `Connect-ExchangeOnline -UserPrincipalName UPN -ExchangeEnvironmentName O365USGovGCCHigh`. Replace `UPN` with your User Principal Name.
1. To enable connectors for Teams, use the following commands. To disable connectors or actionable messages, set the value to `false` instead of `true` in the following commands.

   * `Set-OrganizationConfig -ConnectorsEnabled:$true`
   * `Set-OrganizationConfig -ConnectorsEnabledForTeams:$true`
   * `Set-OrganizationConfig -ConnectorsActionableMessagesEnabled:$true`

For more information about PowerShell module exchange, see [Set-OrganizationConfig](/powershell/module/exchange/Set-OrganizationConfig?view=exchange-ps&preserve-view=true). To enable or disable Outlook connectors, [connect apps to your groups in Microsoft Outlook](https://support.microsoft.com/topic/connect-apps-to-your-groups-in-outlook-ed0ce547-038f-4902-b9b3-9e518ae6fbab). To know more about User Principal Name (UPN), see [what is UPN in Microsoft 365](/entra/identity/hybrid/connect/plan-connect-userprincipalname#what-is-userprincipalname).

> [!NOTE]
> It takes up to 24 hours for these changes to propagate.

## Publish connectors for your organization

To make a custom connector available to your organization's users, upload a custom connector app to your org's app catalog. Users within the org can install, configure, and use the connector in a team.

> [!IMPORTANT]
> Custom connectors are not available in Government Community Cloud (GCC), Government Community Cloud-High (GCCH), and Department of Defense (DOD) environments.

To use connectors in a team or a channel, open the More Options menu from the upper right corner of a channel. From the menu, select **Connectors** and then locate or search for the required connector. Configure the selected connector if necessary.

:::image type="content" source="media/connectors-selection-ui.png" alt-text="Screenshot that shows add connectors to your channel in Teams from the More options in the upper right corner of the channel.":::

## Use connectors in GCC or GCCH

Connectors are disabled by default in the Government Cloud Community (GCC) and Government Community Cloud-High (GCCH) environments. To let your users use connectors in GCC or GCCH environments, follow these steps:

1. You must [enable connectors in Teams](#enable-or-disable-connectors-in-teams).

1. To set the parameters, connect to the [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps&preserve-view=true).

1. To use an incoming webhook in Teams, create a custom app using the following `manifest.json`. To use icons in the custom app, follow the [guidelines to create app icons](/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines#app-icons).

    ``` json
    {
      "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
      "manifestVersion": "1.5",
      "id": "203a1e2c-26cc-47ca-83ae-be98f960b6b2",
      "version": "1.0.0",
      "packageName": "com.incomingwebhook.microsoft",
      "developer": {
        "name": "Microsoft Corporation",
        "websiteUrl": "https://go.microsoft.com/fwlink/?linkid=837668",
        "privacyUrl": "https://privacy.microsoft.com/privacystatement",
        "termsOfUseUrl": "https://www.microsoft.com/servicesagreement"
      },
      "description": {
        "full": "The Incoming Webhook connector enables external services to notify you about activities that you want to track.",
        "short": "Send data from a service to your Microsoft 365 group in real time. "
      },
      "icons": {
        "outline": "outline.png",
        "color": "color.png"
      },
      "connectors": [
        {
          "connectorId": "203a1e2c-26cc-47ca-83ae-be98f960b6b2",
          "scopes": ["team"]
        }
      ],
      "name": {
        "full": "Incoming Webhook",
        "short": "Incoming Webhook"
      },
      "accentColor": "#FFFFFF",
      "permissions": ["identity", "messageTeamMembers"]
    }
    ```

1. [Upload the custom app](teams-custom-app-policies-and-settings.md#upload-a-custom-app-using-teams-admin-center) in your Teams admin center.

## Considerations when using Connectors in Teams

* Connectors are disabled by default in the Government Cloud Community (GCC) environments and Government Community Cloud-High (GCCH). To enable connectors, set the `ConnectorsEnabled` or `ConnectorsEnabledForTeams` parameters to `$true` with the `SetOrganizationConfig` cmdlet. To set the parameters, connect to the [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps&preserve-view=true).

* If the user who added a connector to a team leaves the team, the connector continues to work.

* You can't configure new connections for the following connectors:

  * Aha!
  * Airbrake
  * Aircall
  * App Links
  * AppSignal
  * Beanstalk
  * Bitbucket
  * Buddy
  * Buildkite
  * CATS
  * Chatra
  * CircleCI
  * CodeShip
  * Constant Contact
  * GetResponse
  * Ghost Inspector
  * Groove
  * Heroku
  * Honeybadger
  * Intercom
  * Logentries
  * Mailchimp
  * Microsoft Forms
  * Opsgenie
  * PagerDuty
  * Papertrail
  * Pivotal Tracker
  * Raygun
  * Runscope
  * SatisMeter
  * Semaphore
  * Sentry
  * Simple In/Out
  * Stack Exchange
  * SUBVERSION
  * TestFairy
  * Travis CI
  * Trello
  * Uptodown
  * Userlike
  * Wrike
  * XP-Dev
  * Zendesk

## Related articles

* [Understand connectors and webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors)
* [Create Microsoft 365 connectors](/microsoftteams/platform/webhooks-and-connectors/how-to/connectors-creating)
