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
ms.date: 07/26/2024
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
# Install apps as an admin

IT admins can install Microsoft Teams apps that work on Microsoft Outlook and the Microsoft 365 app (formerly known as Office.com) for some or all users in their organization. You can easily preinstall the apps on the supported hosts. Alternately, you can let users install apps on their own. The prerequisites for app installation are:

* Allow use of apps in your org using the options in the Org-wide app settings.
* Allow the required apps. Individual apps can be [blocked by an admin](manage-apps.md#allow-or-block-apps) or can be [blocked by the developer](/microsoftteams/platform/concepts/deploy-and-publish/add-default-install-scope#block-apps-by-default-for-users-until-an-admin-approves).
* [Grant consent to the app permissions](manage-consent-app-permissions.md#grant-and-manage-consent-to-teams-app-permissions) if an app requires permission to access organization information.
* Make the app available to the required users using either app centric management or permission policies.

## Preinstall apps in user's Teams client

Unified app management changes a few app governance methods. Previously, you used app setup policy to preinstall apps for users. If your organization is now migrated to use app centric management feature, then you use it to preinstall apps. Follow the applicable method to provide apps to your users, without them having to install apps on their own.

### Install apps using app setup policy

To install apps for your users using an app setup policy, follow these steps:

1. Sign in to Teams admin center, access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Edit the existing global policy if your change applies to all users. Otherwise, select **Add** to create a new custom policy that you can apply to some users. Provide a name and description of the policy.

1. Under **Installed apps**, select **Add apps**.

1. In the **Add installed apps** pane, search the apps that you want to add in the Teams client of the allowed users. Select **Add**.

   :::image type="content" source="media/admin-installed-apps.png" alt-text="Screenshot showing how admins preinstall apps using app setup policy." lightbox="media/admin-installed-apps-large.png":::

### Install apps using app centric management

> [!IMPORTANT]
> Previously, you installed apps using app setup policy. We are gradually moving this functionality to app centric management via [Microsoft 365 roadmap ID 394274](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=394274). For timelines and other details, see [Message Center post MC795355](https://admin.microsoft.com/Adminportal/Home?ref=MessageCenter/:/messages/MC795355). Your app setup policy settings to install apps get automatically migrated to the new experience and we retain the user and group assignments. The rest of the settings in app setup policies remain unchanged and continues to work as before.

If you're using app centric management, then follow these steps to install apps for your users. Otherwise, continue to use an [app setup policy to install apps](teams-app-setup-policies.md#install-apps-to-teams-client-of-your-users).

1. Log into Teams admin center and access **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps/) page. Select an app, and click **Edit installs**. Select whom to install the app for and select **Apply**.

   :::image type="content" source="media\app-install-manage-apps-page.png" alt-text="Screenshot showing app installation option for admins on the Manage apps page." lightbox="media\app-install-manage-apps-page.png":::

1. Alternately, you can install an app from the app details page.

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

You can create a new team for your users using a team template. Team template lets you, as an admin, to add apps in template so that the new teams that are created, have these apps available from the beginning, for the users of the team. for more info, see [add apps when creating a team template](create-a-team-template.md) and [get started with team templates](get-started-with-teams-templates-in-the-admin-console.md).

## Understand how users install apps

If the app installation prerequisites are met, [users can install apps](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77) on their own. If an app is blocked, then the users can [request admin approval](user-requests-approve-apps.md).

From the store in their Teams client, users use the **Add to team** option to install an app to a team. This option is available only for the apps that can be installed in a team scope. The option isn't available for apps that can only be installed in the personal scope.

## Related articles

* [How end users can install an app](https://support.microsoft.com/office/add-an-app-to-microsoft-teams-b2217706-f7ed-4e64-8e96-c413afd02f77).
* [Integrated apps in Microsoft 365 admin center](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).
* [Preinstall apps in teams](/microsoftteams/get-started-with-teams-templates-in-the-admin-console)
