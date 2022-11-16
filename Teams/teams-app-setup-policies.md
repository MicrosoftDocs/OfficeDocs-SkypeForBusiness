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
ms.date: 09/26/2022
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to create, edit, and manage app setup policies to pin apps, to install apps, and to allow users to upload custom apps.
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.appsetuppolicies.overview
---

# Use app setup policies to pin and auto-install apps in Teams

As an admin, you use app setup policies to install and pin apps, and control which specific users can upload custom apps. Pinning helps promote adoption of and provide quick access to the relevant apps in your organization.

* **[Pin apps](#pin-apps):** App setup policies let you choose apps to pin, set the order the apps show up for your users in the Teams app bar or the compose message area. Admins can also control whether the end-users can pin their own apps or not.

* **[Install apps](#install-apps):** App setup policies let you install the allowed apps on behalf of users when they start Teams and during meetings.

* **Upload custom apps:** App setup policies let you control which users can upload custom apps to Teams. See [Upload custom apps](teams-custom-app-policies-and-settings.md) article.

The following built-in app setup policies are available in the Microsoft Teams admin center, by default:

* **Global (Org-wide default)**: This default policy applies to all users in your organization unless you assign another policy. Edit the global policy to pin apps that are most important for your users.

* **FirstlineWorker**: This policy is for Frontline Worker. The policy cannot be customized. You can assign it to Frontline Workers in your organization.

## Pin apps

Pinning an app displays the app in the app bar in Teams client. Admins can pin app and they can allow users to pin. Pinning is a used to highlight apps that are needed the most by users and promote ease of access. Pinning works for all [types of apps in Teams](deploy-apps-microsoft-teams-landing-page.md) — Core apps, Microsoft-provided apps, third-party apps, and custom apps developed within your organization.

Admins can pin an app via an app setup policy. Apps that are pinned by admins get automatically installed for the users for whom the app is allowed. Such an app can't be uninstalled by end-users. Using an app setup policy, you can do the following tasks:

* Customize Teams for end-users to highlight the most important apps for them. You choose the apps to pin and the order that the apps display in.
* Control whether users can pin apps or not.

Apps are pinned to the app bar on the left side of the Teams desktop client and at the bottom of the Teams mobile clients. The messaging extensions are available at the bottom of the compose message area.

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

    :::image type="content" source="media/add-pinned-apps-trimmed.png" alt-text="Screenshots shows how to add pinned apps in app setup policy." lightbox="media/add-pinned-apps-large.png":::

1. Select **Add**.

1. Under the **App bar** or **Messaging extensions**, arrange the apps in the order that you want the apps to appear in Teams client.

   :::image type="content" source="media/pin-messaging-extensions.png" alt-text="A screenshot of the pinned apps and pinned Messaging Extensions in Setup policy.":::

1. Select **Save**.

> [!NOTE]
> In Teams for Education, the Assignments app is pinned by default in the global policy even though you don't see it listed in the global policy.

> [!NOTE]
> For the frontline workers in your organization, we recommend using the tailored frontline app experience. This feature pins the most relevant apps in Teams for users who have an [F license](https://www.microsoft.com/en-us/microsoft-365/enterprise/frontline). To learn more, see [Tailor Teams apps for your frontline workers](/microsoft-365/frontline/pin-teams-apps-based-on-license?bc=%2fmicrosoftteams%2fbreadcrumb%2ftoc.json&toc=%2fmicrosoftteams%2ftoc.json).

## Install apps

Using an app setup policy, an admin can achieve the following tasks:

* Install apps for end-users in their personal Teams environment.
* Install apps for end-users as [messaging extensions](/microsoftteams/platform/messaging-extensions/what-are-messaging-extensions).

The end-users can install apps on their own if the [app permission policy](teams-app-permission-policies.md) lets them install it and the app is allowed by the Teams admin. If an app is blocked, then end-users can [request admin approval](user-requests-approve-apps.md).

To install apps using an app setup policy, follow these steps:

1. Sign in to Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Select **Add**.

1. Provide a name and description for the policy.

1. Under **Installed apps**, select **Add apps**.

1. In the **Add installed apps** pane, search the apps that you want to install for users. You can also filter apps by app permission policy.

1. Select **Add**.

:::image type="content" source="media/install-apps-in-meeting.png" alt-text="A screenshot of installation of apps via app policy.":::

## Manage app setup policies

You manage app setup policies in the Microsoft Teams admin center. Use the global (Org-wide default) policy or create and assign custom policies. End-users get the global policy. If you create a custom policy, it overrides the global policy. Global admin or Teams service admin can manage these policies.

You edit the settings in the global policy to include the apps that you want. To customize Teams for different groups of users in your organization, create and assign one or more custom policies.

:::image type="content" source="media/app-setup-policies-update.png" alt-text="Screenshot showing the app setup policies page with options to manage policies or add new policies.":::

### Edit an app setup policy

You can use the Microsoft Teams admin center to edit a policy, including the global (Org-wide default) policy and custom policies that you create. After you edit or assign a policy, it can take a few hours for changes to take effect.

1. Sign in to Teams admin center and access **Teams apps** > **[Setup policies](https://admin.teams.microsoft.com/policies/app-setup)**.

1. Choose the policy you want to edit and then select **Edit**.

1. Make the changes that you want.

1. Select **Save**.

### Assign a custom policy in app setup policy to users and groups

To know how to assign policies to your end-users and to groups, see [how to assign policies to users and groups](assign-policies-users-and-groups.md).

## Considerations and limitations

* You cannot install custom apps with configurable tabs using app setup policies.

* End-users cannot uninstall an app that is installed by an admin.

* End-users can unpin an app that is pinned via app setup policy if user pinning is allowed in the policy.

* Users can change the order of their pinned apps on Teams desktop and mobile clients if the user pinning option is turned on. Users can't change the order of their pinned apps on Teams web clients.

* Admin pins always take precedence. If the User pinning option is turned on, then apps pinned by users display below the apps pinned by admins. If User pinning option is turned off, then users lose existing pins and only the apps pinned by admins are available in the app bar.

* The user pinning setting is available in the Teams admin center in Microsoft 365 Government Community Cloud (GCC) environments (GCC, GCC High and DoD), but it has no effect.

* In Teams for Education, the Assignments app is pinned by default in the global policy even though you don't see it listed in the global policy.

* There's no limit on the maximum number of pinned apps you can add to a policy. However, at least two apps must be pinned to the Teams mobile clients (iOS and Android). If a policy has fewer than two apps, the mobile clients won't reflect the policy settings, and instead will continue to use the existing configuration.

* After you edit or assign a policy, it can take a few hours for changes to take effect.

* Not all apps can be pinned to Teams through an app setup policy. Some apps may not support this functionality. To find apps that can be pinned, search for the app in the **Add pinned apps** pane. Tabs that have a personal scope (static tabs) and bots can be pinned to the Teams desktop client and these apps are available in the **Add pinned apps** pane. While the Teams app store lists all Teams apps. The **Add pinned apps** pane includes only apps that can be pinned to Teams through a policy.

* In Teams for Education, the Calling app isn't available. When you create a new custom policy in app setup policy, the Calling app is displayed in the list of apps. However, the app isn't pinned to Teams clients and Teams for Education users won't see the Calls app in Teams.

## Related articles

* [Admin settings for apps in Teams](admin-settings.md)
* [Assign policies to end-users in Teams](assign-policies-users-and-groups.md)
