---
title: Manage app setup policies in Microsoft Teams
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.subservice: teams-apps
ms.service: msteams
audience: Admin
ms.date: 07/31/2024
ms.reviewer: mhayrapetyan
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to pin apps, install apps, and allow users to upload custom apps by creating, editing, and managing app setup policies.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.appsetuppolicies.overview
---

# Use app setup policies to pin and install apps for users

As an admin, you use app setup policies to install and pin apps and control which users can upload custom apps in personal or team context. Pinning helps promote adoption of apps for the users and it provides quick access to the relevant apps. To know more, see [app setup policy](app-policies.md).

* **[Pin apps in Teams client](#pin-apps):** App setup policies let you choose apps to pin, set the order the apps show up for your users in the Teams app bar or the compose message area. Admins can also control whether the users can pin their own apps or not.

* **[Installs apps in Teams client](#install-apps-to-teams-client-of-your-users):** App setup policies let you add the allowed apps on behalf of users when they start Teams and during meetings. For organizations using app centric management, this functionality is available in [app centric management UI](install-teams-apps.md#install-apps-using-app-centric-management).

* **Upload custom apps:** App setup policies let you control which users can upload custom apps to Teams. See [Upload custom apps](teams-custom-app-policies-and-settings.md) article.

The following built-in app setup policies are available in the Microsoft Teams admin center, by default:

* **Global (Org-wide default)**: This default policy applies to all users in your organization unless you assign another policy. Edit the global policy to pin apps that are most important for your users.

* **FirstlineWorker**: This policy is for Frontline Worker. The policy can't be customized. You can assign it to Frontline Workers in your organization.

## Pin apps

Using app pinning functionality, you can highlight apps that users need the most; make such apps available for users instantly; and make it available in the use's context. App pinning promotes ease of access and improves app adoption in your organization. Admins can pin apps and they can allow users to pin apps. If an admin pins an app, the app is added and pinned in the Teams client of the allowed users only. Pinning respects other governance controls and apps aren't available to users who aren't allowed to use the app.

You can pin apps in the following UIs for the users:

* **App bar**: Users can easily access it and use it.
* **Message extension**: Users can quickly use it when composing their messages.
* **Meeting extension**: Meeting attendees can view it without leaving the meeting and quickly collaborate using the app. The functionality to pin apps in meetings is available only in Teams classic and not in the [new Teams client](new-teams-desktop-admin.md). The in-meeting bar displays only two apps and the rest of the apps, if added, display under the **More** option.

Apps that you pin to the app bar, show on the app bar on the left side of the Teams desktop client and at the bottom of the Teams mobile client.

| Teams desktop client                                                                                      | Teams mobile client                                                                |
|-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| ![Screenshot showing the app bar in Teams desktop client.](media/app-setup-policies-desktop-app-bar.png). | ![Screenshot showing the app bar in Teams mobile client.](media/mobile-app-ui.png) |

Apps that you pin in a meeting show at the top of the meeting window. Beyond two apps, the other apps display in the More option.

   :::image type="content" source="media/polls-user-meeting.png" alt-text="Screenshot showing a meeting room and apps pinned to the top bar in the meeting room." lightbox="media/polls-user-meeting-large.png":::

To modify the pinned apps for everyone in your organization, edit the existing `Global (Org-wide default)` policy. To modify the pinned apps for specific users, create a new app setup policy and assign it to the specific users.

1. Sign in to Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Select **Add**.

1. Provide a name and description for the policy.

1. Optionally, turn on **User pinning** to allow users to pin apps and change the order of the pinned apps.

1. Under **Pinned apps**, select **Add apps**.

1. In the **Add pinned apps** pane, search for the apps you want to add, and then select **Add**. Apps get added only to the scopes that the apps support.

    :::image type="content" source="media/add-pinned-apps-trimmed.png" alt-text="Screenshot shows how to add pinned apps in app setup policy." lightbox="media/add-pinned-apps-large.png":::

1. Arrange the apps in the order that you want the apps to appear in Teams client. You can change the sequence independently under **App bar**, **Messaging extensions**, and **Meeting extensions**. You can remove apps from a scope.

   :::image type="content" source="media/pinned-apps.png" alt-text="Screenshot of the pinned apps and options to change their order.":::

1. Select **Save**.

> [!NOTE]
> In Teams for Education, the [Assignments app](expand-teams-across-your-org/assignments-in-teams.md) is pinned by default even though you don't see it listed in the Global policy.

> [!TIP]
> For the frontline workers in your organization, we recommend using the tailored frontline app experience. This feature pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/en-us/microsoft-365/enterprise/frontline). To learn more, see [Tailor Teams apps for your frontline workers](/microsoft-365/frontline/pin-teams-apps-based-on-license?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

## Install apps to Teams client of your users

If your organization uses app centric management functionality, then [use Manage apps page to install apps for users](install-teams-apps.md). Otherwise, continue to preinstall apps using app setup policies.

The below message on app setup policy page indicates that your org is using app centric management functionality.

:::image type="content" source="media/acm-setup-policy-change.png" alt-text="Screenshot showing updated setup policy page without the app installation option.":::

If your organization isn't using app centric management, then continue to [use app setup policy to install apps](install-teams-apps.md#install-apps-using-app-setup-policy).

## Use app setup policy to allow independent bots

Developers can create bots as part of [Microsoft Bot Framework](https://dev.botframework.com/). Developers can incorporate these bots in a Teams app for use in Teams or developers can share these bots as independent bots that users can use anywhere else, including in Teams client. As an admin, you not only govern Teams apps that contain bots but you can also let your users use independent bots.

Teams classic and in [new Teams](new-teams-desktop-admin.md) support the following bot scenarios based on the admin center settings:

* Independent bots don't work if custom app upload isn't allowed.
* Independent bots work if [custom app upload is allowed](teams-custom-app-policies-and-settings.md).
* Any bot that is a part of a Teams app works if admin [allows the app](manage-apps.md#allow-or-block-apps) in the organization.

:::image type="content" source="media/use-bots-setup-policy.png" alt-text="Flowchart showing a decision making flow for admins to know how they can allow their users to use independent bots." lightbox="media/use-bots-setup-policy-large.png":::

> [!TIP]
> We recommend that you get a Teams app created to use bots in your organization. Having a bot incorporated in a Teams app, offers many governance controls to you as an admin.

## Manage app setup policies

You can manage the app setup policies in the Microsoft Teams admin center. Use the Global (Org-wide default) policy or create and assign custom policies. Global policy applies to all users unless you assign a custom policy to some users. Custom policy overrides the global policy. A Teams Administrator or an admin with a higher role can manage these policies.

You can edit the settings in the global policy to include the apps that you want. To customize Teams for different groups of users in your organization, create and assign one or more custom policies.

:::image type="content" source="media/app-setup-policies-update.png" alt-text="Screenshot shows the app setup policies page with options to manage policies or add new policies.":::

### Edit an app setup policy

You can use the Microsoft Teams admin center to edit a policy, including the **Global (Org-wide default)** policy and custom policies that you create. After you edit or assign a policy, it can take a few hours for changes to take effect. To edit an app setup policy, follow these steps:

1. Sign in to the Teams admin center and go to **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Choose the policy you want to edit and then select **Edit**.

1. Make the changes that you want.

1. Select **Save**.

### Assign a custom policy in app setup policy to users and groups

To know how to assign policies to your users and to groups, see [how to assign policies to users and groups](assign-policies-users-and-groups.md) and [admin center UI for group assignments](https://admin.teams.microsoft.com/policies/app-setup/grouppolicyassignments). Groups are distribution list groups, mail-enabled security groups, security groups, and Microsoft 365 groups and are created in [teams and groups UI in admin center](https://admin.microsoft.com/Adminportal/Home#/groups).

A user can have more than one policy assigned either directly or as a part of different groups. However, only one policy is effective at a time for a user. To know what policy applies, see [precedence of applied policies](/microsoftteams/policy-assignment-overview#which-policy-takes-precedence).

## View the policies already applied to the user

You can use the Teams admin center to check the policies that are assigned to a user. To view the policies, follow these steps:

1. Sign in to the Teams admin center and go to **Users** > **[Manage users](https://admin.teams.microsoft.com/users)**.
1. Search for and select the user by clicking to the left of the user name.
1. Select **View policies** under the **Policies assigned** column.

    :::image type="content" source="media/manage-users-view-policies.png" alt-text="Screenshot that shows the option to view the existing policies applied to the user.":::

## Change the existing policies for a user

To change the existing policies applied to a user, follow these steps:

1. Sign in to the Teams admin center and go to **Users** >  **[Manage users](https://admin.teams.microsoft.com/users)**.
1. Search for and select the user by clicking to the left of the user name and then select **Edit settings**.
1. Select the policy you want to change, and then select **Apply**.

    :::image type="content" source="media/manage-users-edit-settings.png" alt-text="Screenshot that shows the options to change the existing policies.":::

To unassign a custom policy from a user, you can set each policy to **Global (Org-wide default)**.

You can change the existing policies for a user using PowerShell. For more information, see [assign policies to users and groups](assign-policies-users-and-groups.md).

## Unassign app setup policies in bulk

When you unassign policies in bulk, you're removing policy assignments that were assigned to individual users through direct assignment. To unassign setup policies in bulk, follow these steps:

1. Sign in to Teams admin center and go to **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.
1. Select the policy by clicking to the left of the policy name, and then select **Bulk unassign users** from **Manage users** menu.

    :::image type="content" source="media/app-setup-policy-manage-users.png" alt-text="Screenshot that shows the bulk unassign users option from the manage user menu.":::

1. Choose the policy that you want to unassign and select **Load data** to get the number of users who are currently assigned to that policy.

    :::image type="content" source="media/unassign-app-setup-policies-load-data.png" alt-text="Screenshot of the bulk unassign policies page with the load data option.":::

1. Select **Unassign**, and then select **Confirm**.

## Considerations and limitations

* You can't add custom apps with configurable tabs using app setup policies.

* Users can't remove an app from their client if an admin adds it. The `Uninstall` option for an app in the app bar isn't available.

* Users can unpin an app that is pinned via app setup policy if user pinning is allowed in the policy.

* Users can change the order of their pinned apps on Teams desktop and mobile clients if the user pinning option is turned on. Users can't change the order of their pinned apps on Teams web client.

* Admin pins always take precedence. If the user pinning option is turned on, then apps pinned by the users display below the apps pinned by the admins. If the user pinning option is turned off, then the users lose existing pins and only the apps pinned by the admins are available in the app bar.

* The user pinning setting is available in the Teams admin center in Microsoft 365 Government Community Cloud (GCC) environments (GCC, GCC High, and DoD), but it has no effect.

* There's no limit on the maximum number of pinned apps that you can add to a policy. However, at least two apps must be pinned to the Teams mobile client (iOS and Android). If a policy has fewer than two apps, the mobile client doesn't reflect the policy settings. Instead, the mobile client continues to use the existing configuration.

* After you edit or assign a policy, it can take a few hours for changes to take effect. Also, the rollback takes a few hours to take effect if you choose to roll back the policy application.

* The functionality to pin apps in meetings is available only in Teams classic and not in the [new Teams client](new-teams-desktop-admin.md). The in-meeting bar displays only two apps and the rest of the apps, if added, display under the More option.

* Not all apps can be pinned to Teams through an app setup policy. Some apps don't support this functionality. To find apps that can be pinned, search for the app in the **Add pinned apps** pane. Tabs that have a personal scope (static tabs) and bots can be pinned to the Teams desktop client and these apps are available in the **Add pinned apps** pane. While the Teams app store lists all Teams apps, the **Add pinned apps** pane includes only apps that can be pinned to Teams through a policy.

* In Teams for Education, the [Assignments app](expand-teams-across-your-org/assignments-in-teams.md) is pinned by default even though it isn't listed in the Global policy.

* In Teams for Education, the `Calling` app isn't available. When you create a new custom policy in the app setup policy, the `Calling` app is displayed in the list of apps. However, Teams for Education users can't see the `Calls` app in Teams client as it isn't pinned.

## Related article

* [Assign policies to users in Teams](assign-policies-users-and-groups.md)
* [How to use apps in meetings](https://support.microsoft.com/office/use-apps-in-microsoft-teams-meetings-62bca572-ba7e-4e21-9190-a47c61319739)
