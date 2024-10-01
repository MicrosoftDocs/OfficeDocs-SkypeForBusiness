---
title: Preinstall Teams apps for your org users
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-apps
ms.custom: intro-get-started
audience: admin
ms.date: 07/31/2024
ms.collection: 
  - M365-collaboration
  - tier2
  - highpri
ms.reviewer: mhayrapetyan
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: How IT professionals preinstall Teams apps for users, in channels, and in meetings and manage the installation options of apps.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---
# Preinstall apps for your users

IT admins can install Microsoft Teams apps that work on Microsoft Outlook and the Microsoft 365 app (formerly known as Office.com) for some or all users in their organization. You can easily preinstall the apps on the supported hosts. Alternately, users install apps on their own if you [allow users to use apps](manage-apps.md#allow-or-block-apps). You can proactively install apps for users so that you help them discover apps easily, ensure app retention, and save user's effort to install. For example, you can install IT helpdesk or ticketing app for all new employees to provide an easy and quick way for new joiners to seek support.

## Preinstall apps in user's Teams client

Unified app management changes a few app governance methods. Previously, you used app setup policy to preinstall apps for users. If your organization is now migrated to use app centric management feature, then you use it to preinstall apps. Follow the applicable method to provide apps to your users, without them having to install apps on their own.

### Install apps using app setup policy

If you aren't using app centric management, then you preinstall apps using app setup policy. To know more, see [overview of app setup policy](teams-app-setup-policies.md). Ensure that the following prerequisites are met.

* Allow use of apps in your org using the options in the [Org-wide app settings](manage-apps.md#manage-org-wide-app-settings).
* Allow the required apps. [Admins can block an app](manage-apps.md#allow-or-block-apps) or [Developers can block their app by default](/microsoftteams/platform/concepts/deploy-and-publish/add-default-install-scope#block-apps-by-default-for-users-until-an-admin-approves).
* If an app requires permission to access organization information, [grant consent to the app permissions](manage-consent-app-permissions.md#grant-and-manage-consent-to-teams-app-permissions).
* Make the app available to the required users and groups using app permission policies.

To install apps using the policy, follow these steps:

1. Sign in to Teams admin center, access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Edit the existing global policy if your change applies to all users. Otherwise, select **Add** to create a new custom policy that you can apply to some users. Provide a name and description of the policy.

1. Under **Installed apps**, select **Add apps**.

1. In the **Add installed apps** pane, search the apps that you want to add in the Teams client of the allowed users. Select **Add**.

   :::image type="content" source="media/admin-installed-apps.png" alt-text="Screenshot showing how admins preinstall apps using app setup policy." lightbox="media/admin-installed-apps-large.png":::

### Install apps using app centric management

If your organization is using app centric management, then you preinstall apps using its UI. For more information about availability of app centric management, see [Microsoft 365 roadmap ID 394274](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=394274) and for timeline, see [Message Center post MC795355](https://admin.microsoft.com/Adminportal/Home?ref=MessageCenter/:/messages/MC795355). To start using app centric management, see [use and migrate to app centric management](app-centric-management.md).

> [!NOTE]
> If you previously used app setup policies to install apps and now migrate to app centric management, then your policy settings get automatically migrated to the new experience and we retain the user and group assignments. The rest of the settings in app setup policies remain unchanged and continues to work as before.

Before you preinstall apps using app centric management, ensure that the following prerequisites are met.

* Allow use of apps in your org using the options in the [Org-wide app settings](manage-apps.md#manage-org-wide-app-settings).
* Allow the required apps. Individual apps can be [blocked by an admin](manage-apps.md#allow-or-block-apps) or can be [blocked by the developer](/microsoftteams/platform/concepts/deploy-and-publish/add-default-install-scope#block-apps-by-default-for-users-until-an-admin-approves).
* [Grant consent to the app permissions](manage-consent-app-permissions.md#grant-and-manage-consent-to-teams-app-permissions) if an app requires permission to access organization information.

To install apps using the app centric management UI, follow these steps:

1. Log into Teams admin center and access **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps/) page. Do one of the following tasks:

   * Select an app, and click **Edit installs**. Select whom to install the app for and select **Apply**.

      :::image type="content" source="media\app-install-manage-apps-page.png" alt-text="Screenshot showing app installation option for admins on the Manage apps page." lightbox="media\app-install-manage-apps-page.png":::

   * Alternately, you can install an app from the app details page.

      1. Select **Users and groups** > **Installs** > **Install app**.
      1. Select whom to install the app for and select **Apply**. The app is made available to the selected users and groups and there's no need to separately make the app available for the same users and groups.

      :::image type="content" source="media\app-install-app-details-page.png" alt-text="Screenshot showing app installation option for admins on the app details page."  lightbox="media/app-install-app-details-page.png":::

## Install apps in an existing team

Apps in teams allow better collaboration for the users. You can also install an app in a team to improve app discovery and usage. To add apps in teams that will be created in the future, [add apps to a teams template](/microsoftteams/get-started-with-teams-templates-in-the-admin-console). To add apps in the existing teams, follow these steps.

1. On Manage apps page, search for an app and select it.

1. Select **Add to team**.

   :::image type="content" source="media/add-app-team.png" alt-text="Screenshot showing the option for admins to add an app to specific teams." lightbox="media/add-app-team.png":::

1. In the **Add to team** pane, search for the team you want to add the app to, select the team, and then select **Apply**.

## Preinstall apps in a new team using team creation template

You can create a new team for your users using a team template. Team template lets you, as an admin, to add apps in template so that the new teams that are created, have these apps available from the beginning, for the users of the team. For more info, see [add apps when creating a team template](create-a-team-template.md) and [get started with team templates](get-started-with-teams-templates-in-the-admin-console.md).

## Understand how users install apps

If the app installation prerequisites are met, [users can install apps](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77) on their own. If an app is blocked, then the users can [request admin approval](user-requests-approve-apps.md).

From the store in their Teams client, users install apps for their personal use by selecting **Add** option or install apps in their teams and channels by selecting **Add to team** option. Option to add an app to a team is available for only those apps that can work in a team scope.

## Related articles

* [How end users can install an app](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77).
* [Integrated apps in Microsoft 365 admin center](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).
* [Preinstall apps in teams and channels using a template](get-started-with-teams-templates-in-the-admin-console.md)
