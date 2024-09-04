---
title: Grant and manage consent to Teams app permissions
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: how-to
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 09/04/2024
ms.reviewer: Orion.OMalley
description: Manage consent to Teams apps permissions to access the required org information.
f1.keywords:
- NOCSH
ms.localizationpriority: medium
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Grant and manage consent to Teams app permissions

Use of Teams apps can provide an incredible boost to the productivity of and collaboration between your organization's users. Teams apps bring information at the tips of your users, without any context switching, and help them do great work. As an admin, you play a critical role to empower your users with the right type of apps while balancing your company's need for security and compliance. Once you decide to approve the use of an app, you must make sure that the app adoption is smooth for the users.

A crucial part is to grant consent to the permissions that an app needs to work. You consent for approved apps so that each user in your organization doesn't have to review permissions and consent individually, when they start the app. A few examples of permissions requested by apps include the ability to read information stored in a team, read a user's profile, and send an email on behalf of users. To learn more about permissions and consent, see [Permissions and consent in the Microsoft identity platform endpoint](/azure/active-directory/develop/v2-permissions-and-consent).

To safeguard company's needs and adhere to its policies, only Global Administrators can grant consent to apps permissions on behalf of all users in your organization. The option to view details and requirement to grant consent applies to custom and third-party apps, and not to the [apps provided by Microsoft](apps-in-teams.md#types-of-teams-apps).

## View Microsoft Graph permissions requested by an app

On the [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps) page, the **Permissions** column indicates whether an app has permissions that need consent. Select the **View details** link for an app to view the various permissions and access to organization's information that the app requests. The option to view details and grant consent applies to custom and third-party apps, and not to the [apps provided by Microsoft](apps-in-teams.md#types-of-teams-apps).

## Grant org-wide admin consent to an app's permissions

Granting consent to such permissions allows an app to access your organization's information. Carefully review the permissions requested by the app before you grant consent. For more information, see [Teams apps permissions and consent](app-permissions.md). Only Global Administrators can grant consent to the Graph permissions that an app requests. Teams Administrators can view the required permissions in admin center. The option to view details and grant consent applies to custom and third-party apps, and not to the [apps provided by Microsoft](apps-in-teams.md#types-of-teams-apps).

To view and grant consent for all users in your organization, follow these steps:

1. In Teams admin center, access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Search for the required app and then do one of the following actions:
    * Select the **View details** link in the Permissions column of the app, to open the **Permissions** tab.
    * Select the app name to go to the app details page and select the **Permissions** tab.

1. Under **Org-wide permissions**, select **Review permissions and consent**.

    :::image type="content" source="media/app-grant-consent-option.png" alt-text="Screenshot showing the option to grant consent to Graph permissions requested an app.":::

1. In the dialog that opens, review the permissions requested by the app.

    :::image type="content" source="media/app-grant-consent-dialog.png" alt-text="Screenshot showing the dialog that accepts consent for the permissions requested by an app.":::

1. If you agree with the permissions requested by the app, select **Accept** to grant consent. A confirmation in the permissions tab let's you know that consent is available for the app. The app now has access to the specified resources for all users in your organization for whom the app is allowed. Users aren't prompted now to review the permissions.

   :::image type="content" source="media/app-grant-consent-confirmation.png" alt-text="Screenshot showing a confirmation after you grant consent to app permissions.":::

> [!NOTE]
> In the new version of the app, if the developer adds extra permissions that require admin consent, then users are not able to use the app until you [grant consent to the updated app](#grant-consent-to-new-graph-permissions-after-an-app-update).

## Let users grant consent to low risk Graph permissions

You can configure user consent settings to let users consent to selected permissions (recommended approach) and use apps that require only these specific permissions without needing admin consent.

This approach works together with permissions classification in Microsoft Entra ID portal. The classification let admins define some Delegated Graph permissions as low risk permissions within their organization. Admins decide which low risk permissions based on their organization's risk posture. As a safety measure, you can't categorize Application permissions low risk.

You can configure user consent settings in way that lets users to:

* Not be able to consent to any apps and hence use only admin-approved apps.
* Consent to selected permissions (recommended approach) and use app that required only these specific permissions.

The recommended approach works together with permissions classification. The classification let admins define some or all of the Delegated Graph permissions as low risk permissions within their organization. Admins decide low risk permissions based on their organization's risk posture. As a safety measure, you can't categorize Application permissions low risk. Application permissions require only an admin to consent. For more information, see [configure how users consent to applications](/azure/active-directory/manage-apps/configure-user-consent?pivots=portal) and [how to classify permissions as low or high risk](/azure/active-directory/manage-apps/configure-permission-classifications?pivots=portal).

The roles that can accomplish this configuration are Global Administrator, Application Administrator, or Cloud Application Administrator. We recommend using a lower privilege role such as Application Administrator.

## Check and verify granted consent to permissions

After you grant consent to permissions of an app, a confirmation in the **Permissions** tab to let you know that consent is available for the app permissions. If you want to view details of each app permissions, follow these steps:

1. Log in to [Microsoft Entra admin center](https://entra.microsoft.com).

1. Select **Applications** > [**Enterprise applications**](https://entra.microsoft.com/#view/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/~/AppAppsPreview).

1. Select an application to view its permissions. Select **Permissions** in the applications page.

   :::image type="content" source="media/consented-perms-entra.png" alt-text="Screenshot showing Entra UI used to view and manage the granted consent to an app's permissions." lightbox="media/consented-perms-entra-large.png":::

1. Select a permission to know more details about it.

   :::image type="content" source="media/graph-permission-details.png" alt-text="Screenshot showing details of a selected permission.":::

## Revoke granted consent to permissions

To revoke the consent that you granted to an app previously, follow these steps:

1. In the Permissions tab, select the **Microsoft Entra ID** link to open the app's permissions in Microsoft Entra admin center.
1. In the **Admin consent** tab, choose the permission you would like to revoke and then select the ellipses `...`.
1. Select **Revoke Permission** and then select **Yes, revoke** in the confirmation dialog.

   :::image type="content" source="media/consented-perms-entra-revoke.png" alt-text="Screenshot showing the option to revoke a Graph permission of an app from the Microsoft Entra admin center.":::

After you revoke consent to some permissions, you can regrant consent. See [Grant org-wide admin consent to an app's permissions](#grant-org-wide-admin-consent-to-an-apps-permissions).

## Grant consent to new Graph permissions after an app update

Developers update apps to add new functionality, enhance existing functionality, or fix bugs. Some app updates may add new permissions that weren't part of the previous version of the app. If the developer adds any new permissions that require admin consent, you must consent to the new permissions. Reconsent flow is the same as described in [Grant org-wide admin consent to an app's permissions](#grant-org-wide-admin-consent-to-an-apps-permissions).

To know about app changes that require consent from a user or an admin, see [conditions when an app update requires consenting](apps-update-experience.md). Depending on your organization's configuration, users may be able to grant consent to some types of permissions.

## View resource-specific consent permissions of an app

Resource-specific consent (RSC) permissions let an app access and modify a team's or a user's data. RSC permissions are granular and specific to the Teams team in which an app is added. A few examples of RSC permissions are the ability to create and delete channels in a team, get the settings for a team, and create and remove channel tabs.

RSC permissions are defined in the app manifest and not in Microsoft Entra admin center. Team owners can grant consent for such permissions when they add the app to a team or a chat. To know more, see [Resource-specific consent (RSC)](/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

You can view RSC permissions for an app in the **Permissions** tab of the app details page. The RSC permissions are listed along with the other permissions under the sections of Application and Delegated permissions.

## Let resource owners consent to RSC permissions

Admins can configure whether users can let apps access their groups' or teams' data or not. Global Administrators can change the **Group owner consent for apps accessing data** settings in Microsoft Entra ID, to [let users consent to RSC permissions](/entra/identity/enterprise-apps/configure-user-consent-groups#manage-group-owner-consent-to-apps-by-directory-settings).

If you don't let group owner consent for apps, then users can't consent to RSC permissions in an app, if RSC permissions are used.

## Related articles

* [View and understand app permissions](app-permissions.md)
* [Microsoft Graph permissions reference including RSC permissions](/graph/permissions-reference).
* [Configure the admin consent workflow in Microsoft Entra ID portal](/entra/identity/enterprise-apps/configure-admin-consent-workflow)
