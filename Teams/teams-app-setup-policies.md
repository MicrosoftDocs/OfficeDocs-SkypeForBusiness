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
ms.date: 06/27/2023
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

# Use app setup policies to pin and auto-install apps for users

As an admin, you use app setup policies to install and pin apps and control the specific users who can upload custom apps. Pinning helps promote adoption of and provide quick access to the relevant apps in your organization.

* **[Pin apps](#pin-apps):** App setup policies let you choose apps to pin, set the order the apps show up for your users in the Teams app bar or the compose message area. Admins can also control whether the users can pin their own apps or not.

* **[Install apps](#install-apps):** App setup policies let you install the allowed apps on behalf of users when they start Teams and during meetings.

* **Upload custom apps:** App setup policies let you control which users can upload custom apps to Teams. See [Upload custom apps](teams-custom-app-policies-and-settings.md) article.

The following built-in app setup policies are available in the Microsoft Teams admin center, by default:

* **Global (Org-wide default)**: This default policy applies to all users in your organization unless you assign another policy. Edit the global policy to pin apps that are most important for your users.

* **FirstlineWorker**: This policy is for Frontline Worker. The policy can't be customized. You can assign it to Frontline Workers in your organization.

## Pin apps

Admins can pin apps and they can allow users to pin apps. Pinning an app displays the app in the app bar in Teams client. Pinning is a used to highlight apps that are needed the most by users and promote ease of access. Pinning works for all [types of apps in Teams](apps-in-teams.md)—Core apps, Microsoft-provided apps, third-party apps, and custom apps developed within your organization.

Admins can pin an app via an app setup policy. Apps pinned by admins get automatically installed but only for the users for whom the app is allowed. Users can't install such an app. Using an app setup policy, you can do the following tasks:

* Customize Teams for users to highlight the most important apps for them. You choose the apps to pin and the order that the apps display in.
* Control whether users can pin apps or not.

Apps are pinned to the app bar on the left side of the Teams desktop client and at the bottom of the Teams mobile client. The messaging extensions are available at the bottom of the compose message area.

|Teams desktop client  |Teams mobile client |
|---------|---------|
|![Screenshot showing the app bar in Teams desktop client.](media/app-setup-policies-desktop-app-bar.png).  |   ![Screenshot showing the app bar in Teams mobile client.](media/mobile-app-ui.png)      |

To pin apps using an app setup policy, follow these steps:

1. Sign in to Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Select **Add**.

1. Enter a name and description for the policy.

1. Optionally, turn on **User pinning** to allow users to pin apps and change the order of the pinned apps.

1. Under **Pinned apps**, select **Add apps**.

1. In the **Add pinned apps** pane, search for the apps you want to add, and then select **Add**.

    :::image type="content" source="media/add-pinned-apps-trimmed.png" alt-text="Screenshot shows how to add pinned apps in app setup policy." lightbox="media/add-pinned-apps-large.png":::

1. Select **Add**.

1. Under the **App bar** or **Messaging extensions**, arrange the apps in the order that you want the apps to appear in Teams client.

   :::image type="content" source="media/pin-messaging-extensions.png" alt-text="Screenshot of the pinned apps and pinned Messaging Extensions in the setup policy.":::

1. Select **Save**.

> [!NOTE]
> In Teams for Education, the Assignments app is pinned by default in the global policy even though you don't see it listed in the global policy.

> [!NOTE]
> For the frontline workers in your organization, we recommend using the tailored frontline app experience. This feature pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/en-us/microsoft-365/enterprise/frontline). To learn more, see [Tailor Teams apps for your frontline workers](/microsoft-365/frontline/pin-teams-apps-based-on-license?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

## Install apps

Using an app setup policy, an admin can achieve the following tasks:

* Install apps for the users in their personal Teams environment.
* Install apps for the users as [messaging extensions](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions).

The users can install apps on their own if the [app permission policy](teams-app-permission-policies.md) lets them install it and an admin has allowed the app. If an app is blocked, then the users can [request admin approval](user-requests-approve-apps.md).

To install apps using an app setup policy, follow these steps:

1. Sign in to Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Select **Add**.

1. Provide a name and description for the policy.

1. Under **Installed apps**, select **Add apps**.

1. In the **Add installed apps** pane, search the apps that you want to install for users. You can also filter apps by app permission policy.

1. Select **Add**.

:::image type="content" source="media/install-apps-in-meeting.png" alt-text="Screenshot of installation of apps via app policy.":::

## Manage app setup policies

You can manage the app setup policies in the Microsoft Teams admin center. Use the global (Org-wide default) policy or create and assign custom policies. Users get the global policy and if you create a custom policy, it overrides the global policy. A Global Administrator or a Teams Administrator can manage these policies.

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

After you unassign policies, you can review operation details in the [Activity log](https://admin.teams.microsoft.com/activity-log).

## Considerations and limitations

* You can't install custom apps with configurable tabs using app setup policies.

* Users can't uninstall an app if an admin has installed it.

* Users can unpin an app that is pinned via app setup policy if user pinning is allowed in the policy.

* Users can change the order of their pinned apps on Teams desktop and mobile clients if the user pinning option is turned on. Users can't change the order of their pinned apps on Teams web client.

* Admin pins always take precedence. If the user pinning option is turned on, then apps pinned by the users display below the apps pinned by the admins. If the user pinning option is turned off, then the users lose existing pins and only the apps pinned by the admins are available in the app bar.

* The user pinning setting is available in the Teams admin center in Microsoft 365 Government Community Cloud (GCC) environments (GCC, GCC High, and DoD), but it has no effect.

* In Teams for Education, the Assignments app is pinned by default in the global policy even though you don't see it listed in the global policy.

* There's no limit on the maximum number of pinned apps you can add to a policy. However, at least two apps must be pinned to the Teams mobile client (iOS and Android). If a policy has fewer than two apps, the mobile client won't reflect the policy settings, and instead will continue to use the existing configuration.

* After you edit or assign a policy, it can take a few hours for changes to take effect. Also, the rollback takes a few hours to take effect if you choose to rollback the policy application.

* Not all apps can be pinned to Teams through an app setup policy. Some apps may not support this functionality. To find apps that can be pinned, search for the app in the **Add pinned apps** pane. Tabs that have a personal scope (static tabs) and bots can be pinned to the Teams desktop client and these apps are available in the **Add pinned apps** pane. While the Teams app store lists all Teams apps, the **Add pinned apps** pane includes only apps that can be pinned to Teams through a policy.

* In Teams for Education, the Calling app isn't available. When you create a new custom policy in the app setup policy, the Calling app is displayed in the list of apps. However, the app isn't pinned to Teams clients and Teams for Education users won't see the Calls app in Teams.

## Related article

* [Assign policies to users in Teams](assign-policies-users-and-groups.md)
