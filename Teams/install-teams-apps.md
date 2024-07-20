---
title: Preinstall Teams apps or let users install apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-apps
ms.custom: intro-get-started
audience: admin
ms.date: 07/19/2024
ms.collection: 
  - M365-collaboration
  - tier2
  - highpri
ms.reviewer: mhayrapetyan
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Preinstall Teams apps or let users install apps and manage the installation options for an app.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---
# Install or remove Teams apps as an admin

IT admins can install Teams apps for some or all users in their organization. Developers can create some Teams apps to work on Outlook and Microsoft 365 Apps (formerly office.com). You can easily preinstall the apps on all the supported hosts. Alternately, you can let users install apps on their own. A few supported apps can also be auto-installed if a user uses it outside teams.

The prerequisites for app installation are:

* Allow use of apps in your org using the options in Org-wide app settings.
* Make the app available to the required users using either app centric management or permission policies.
* [Grant consent to the app permissions](manage-consent-app-permissions.md#grant-and-manage-consent-to-teams-app-permissions) if an app requires permission to access organization information.

If you complete the prerequisites, then users can install the apps themselves. However, you can proactively install apps for users so that you help them discover apps easily, ensure app retention, and save user's effort to install. For example, you can install IT helpdesk or ticketing app for all new employees to provide an easy and quick way for new joiners to seek support.

## Install apps for users using app centric management

> [!IMPORTANT]
> Previously, you installed apps using app setup policy. We are gradually moving this functionality to app centric management via [Microsoft 365 roadmap ID 394274](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=394274). For timelines and other details, see [Message Center post MC795355](https://admin.microsoft.com/Adminportal/Home?ref=MessageCenter/:/messages/MC795355). Your app setup policy settings to install apps get automatically migrated to the new experience and we retain the user and group assignments. The rest of the settings in app setup policies remain unchanged and continues to work as before.

If you're using app centric management, then follow these steps to install apps for your users. Otherwise, continue to use an [app setup policy to install apps](teams-app-setup-policies.md#install-apps-to-teams-client-of-your-users).

1. Log into Teams admin center and access **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps/) page. Select an app, and click **Edit installs**. Select whom to install the app for and select **Apply**.

   :::image type="content" source="media\app-install-manage-apps-page.png" alt-text="Screenshot showing app installation option for admins on the Manage apps page.":::

1. Alternately, you can install an app from the app details page.

   1. Select **Users and groups** > **Installs** > **Install app**.
   1. Select whom to install the app for and select **Apply**.

   :::image type="content" source="media\app-install-app-details-page.png" alt-text="Screenshot showing app installation option for admins on the app details page."  lightbox="media/app-install-app-details-page.png":::

1. Optionally, you can let apps install automatically by enabling [auto-install approved apps feature](auto-install-approved-apps.md). It works for a few specific apps, only if you allow the use of apps by making it available, and only if a user uses the app outside Teams.

## Install apps for users using app setup policy

To install apps for your users using an app setup policy, follow these steps:

1. Sign in to Teams admin center, access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Edit the existing global policy if your change applies to all users. Otherwise, select **Add** to create a new custom policy that you can apply to some users. Provide a name and description of the policy.

1. Under **Installed apps**, select **Add apps**.

1. In the **Add installed apps** pane, search the apps that you want to add in the Teams client of the allowed users. Select **Add**.

   :::image type="content" source="media/admin-installed-apps.png" alt-text="Screenshot showing how admins preinstall apps using app setup policy." lightbox="media/admin-installed-apps-large.png":::

## Choose app rollout and adoption method based on your organization needs

As an admin you can't just allow apps and authorize users to use the apps, you can also make roll out and adoption smoother for the admin team and for your organization's users. To facilitate friction-free app rollout and adoption, Teams provides conceptual guidance and suggestions to app developers so that [developers can enable admins to drive adoption](/microsoftteams/platform/promote-app-adoption#understand-how-you-can-drive-app-adoption). Also, Teams admin center provides various features that help you evaluate apps, allow apps, auto-install apps, pin apps for users, and so on.

We recommend a few approaches that can cater to your organization’s need and the recommendations are based on the following guiding principles:

* Respect and support IT and security requirements around app permissions, access, and availability across all options.
* Improve app adoption so that the authorized users can use the app in Teams as soon as the app is required and continue their work efficiently.
* Don’t interrupt or burden the users who aren’t using the app.

| Org needs | Admin actions | Impact | Benefits | Supported [app types](apps-in-teams.md#types-of-teams-apps) |
|:----------|:--------------|:-------|:---------|:------------------------------------------------------------|
| Priority apps that are a must-see and must-use for a department or the org. | Install and [pin apps](teams-app-setup-policies.md). | App icon shows in [app bar](teams-app-setup-policies.md#pin-apps) for authorized users. | High visibility, faster adoption, and longer retention by users. No actions needed for end-users. | All apps |
| Apps that are good-to-have for a department or the org | Install apps but don't pin it. | App shows at the bottom of or in the overflow of the [app bar](teams-app-setup-policies.md#pin-apps). | Makes it easy for users to discover apps and doesn't change their app bar. | All apps |
| Priority apps for a team | Include the [apps in a custom team template](create-a-team-template.md). | Apps show in the header of any team that uses the template. | Makes it easy for users to discover apps and doesn't change their app bar but applicable only for a team. | Microsoft-provided apps |
| Apps already in use outside Teams, for example web apps | Automatically install the apps using [Auto install approved apps feature](auto-install-approved-apps.md). | If users use the app outside of Teams, it gets added to their Teams client and shows in the app bar. Permissions or data access doesn't change. | Align with the user intent to use the app with no extra user action required. | Applicable for only [these apps](auto-install-approved-apps.md#apps-requiring-setup-before-deployment-to-users) |

## Auto install approved apps

Auto install approved apps feature automatically adds approved apps in Teams client of the allowed users. The functionality respects all admin governance controls, so it's made available only for the users who you allow to use the app. Also, the feature installs only those apps that a user uses outside Teams. It reduces manual intervention to add an app and improves user productivity by preventing context-switching. To know more about the feature, see [Auto install approved apps in Teams](auto-install-approved-apps.md).

## Install apps in a team

Apps in teams allow better collaboration for the users. You can also install an app in a team to improve app discovery and usage. To add apps in teams that will be created in the future, [add apps to a teams template](/microsoftteams/get-started-with-teams-templates-in-the-admin-console). To add apps in the existing teams, follow these steps.

1. On Manage apps page, search for an app and select it.

1. Select **Add to team**.

   :::image type="content" source="media/add-app-team.png" alt-text="Screenshot showing the option for admins to add an app to specific teams.":::

1. In the **Add to team** pane, search for the team you want to add the app to, select the team, and then select **Apply**.

## How users install apps

If the app installation prerequisites are met, [users can install apps](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77) on their own. If an app is blocked, then the users can [request admin approval](user-requests-approve-apps.md).

From the store in their Teams client, users use the **Add to team** option to install an app to a team. This option is available only for the apps that can be installed in a team scope. The option isn't available for apps that can only be installed in the personal scope.

## Stop app usage and remove apps

As an admin, to prevent users from adding and using an app in Teams, you can do one or more of the following:

* For any type of apps, [block it for entire org](manage-apps.md#allow-or-block-apps).
* You can [revoke the granted consent to app permissions](manage-consent-app-permissions.md#revoke-granted-consent-to-permissions), if any, so that the app or its users don't have access to the organization's data.
* For any type of apps, prevent a few users from accessing the app by using either [permission policies](teams-app-permission-policies.md#create-an-app-permission-policy) or by using [app centric management](app-centric-management.md).
* [Delete a custom app](teams-custom-app-policies-and-settings.md#delete-custom-apps-from-your-organizations-catalog) from your organization's store. You can't remove any app that is available in Teams app store.
* Global admin can [block apps that work across multiple surfaces](/microsoft-365/admin/manage/teams-apps-work-on-outlook-and-m365) or [block Teams-only apps](/microsoft-365/admin/manage/teams-apps-work-only-on-teams) from the Integrated Apps page in Microsoft 365 admin center.

You can't stop use of some [Core apps](apps-in-teams.md#types-of-teams-apps) provided by Microsoft that are critical for Teams to work.

> [!CAUTION]
> Blocked apps may still have access to data from the teams that the apps were added to. To turn off app data access, a Global Administrator, an Application Administrator, or a Cloud Application Administrator must [turn off user sign-in in the Microsoft Entra admin center](/azure/active-directory/manage-apps/disable-user-sign-in-portal?pivots=portal).

## Related articles

* [How end users can install an app](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77).
* [Integrated apps in Microsoft 365 admin center](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).
* [Preinstall apps in teams](/microsoftteams/get-started-with-teams-templates-in-the-admin-console)
