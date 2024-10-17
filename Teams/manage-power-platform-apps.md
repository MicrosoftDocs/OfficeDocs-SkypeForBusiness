---
title: Manage Microsoft Power Platform apps in the Microsoft Teams admin center
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-apps
audience: Admin
ms.date: 08/26/2024
ms.collection: 
- M365-collaboration
appliesto: 
- Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to manage access to custom apps built using Microsoft Power Platform in the Teams admin center.
---

# Manage Microsoft Power Platform apps in the Teams admin center

This article gives you an overview of how to manage custom apps created using the [Microsoft Power Platform](https://www.microsoft.com/power-platform/) apps in the Microsoft Teams admin center. Custom apps are Teams apps that you use within your organization and are available to your org users only. Custom apps are not available on Teams app store.

> [!NOTE]
> This article doesn't apply to the `Power Apps` app or `Power Automate Actions` app that users install from the app store or admins pin using an [app setup policy](teams-app-setup-policies.md). You can manage the store apps using [app permission policies](teams-app-permission-policies.md) or [app centric management](app-centric-management.md).

[Power Apps](https://www.microsoft.com/power-platform/products/power-apps) is a low-code or no-code application development environment that app creators in your organization can use to build custom apps that connect to your business data. [Microsoft Copilot Studio](/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) is a graphical, low-code tool for both creating a custom Copilot—including building automation with Power Automate—and extending a Microsoft 365 Copilot with your own enterprise data and scenarios. With the integration of Microsoft Power Platform apps into Teams, organizations can streamline business processes, respond to changing business needs more rapidly to drive greater collaboration, and create and share custom solutions to be more productive.  

Microsoft Power Platform apps created by developers in your organization are automatically added to Teams. Developers can control who can access their app by using the [sharing feature in Power Apps](/powerapps/maker/canvas-apps/share-app) and the [sharing feature in Copilot Studio](/microsoft-copilot-studio/admin-share-bots).

When a Microsoft Power Platform app is created or shared, users can view and install it on the Apps page by going to **Copilot agents**. It take a few minutes for the app to appear in store after it is shared.

:::image type="content" source="media/manage-power-platform-apps-apps-page.png" alt-text="Screenshots of Apps page, showing Microsoft Power Platform apps category.":::

Users see an app in **Copilot agents** section in the client store, if the app meets one of the following conditions.

| Power Apps | Copilots Studio |
|------------|-----------------|
|<ul><li>The user created the app.</li><li>The app was shared directly with the user.</li><li>The user recently used the app. </li></ul>| <ul><li>The user created the bot.</li><li>The team, that a user is a member of, owns a bot. </li></ul>  |

Users install Microsoft Power Platform apps in the same way they install any other Teams app. Keep in mind that users can only install apps to the context to which they have permissions. For example, a team that a user owns, a chat that the user is a part of, or their personal scope.

## Manage access to Microsoft Power Platform apps in the Teams admin center

As an admin, you can control whether Microsoft Power Platform apps are available to users in your org or not. You can collectively block or allow all apps created in Power Apps or all apps created in Copilot Studio at the org level on the [Manage apps](manage-apps.md) page. Block `Power Apps` and `Shared Copilots` app for everyone. To block these apps for specific users, use [app permission policies](teams-app-permission-policies.md) or [app centric management](app-centric-management.md).

The **Shared Power Apps** app and **Shared Copilots** app in your org catalog represent all apps created on the platform. If you block one or both these apps for entire org or for specific users, the users can't install the app in Teams. The users can't request admin approval to allow the apps.

Keep in mind that you can control access to all apps created in Power Apps and Copilot Studio but you can't allow or block individual apps. The app creator decides who can access the apps they create through the sharing feature from within Power Apps and Copilot Studio.

If a user is allowed to access apps from Power Apps or Copilot Studio, and you then block the user from accessing apps from one or both these platforms, the user can still access and use Microsoft Power Platforms apps that they installed before you blocked the app or apps. However, the user can no longer install any new such apps.

> [!NOTE]
> The setting named **Let users interact with custom apps in preview**, in the Org-wide app setting on the [Manage apps](manage-apps.md) page, applies to everyone in your organization and governs whether they can use custom apps or not. Org-wide app settings govern the behavior for all users but don't override any app setup policies assigned to users. If this setting is turned off, users in your organization can't upload any custom apps, including Microsoft Power Platform apps. To learn more, see [Manage org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

### Allow Microsoft Power Platform apps for specific users

To allow or block specific users in your organization from accessing apps created in Power Apps or Copilot Studio, do one of the following:

* If using [app permission policies](teams-app-permission-policies.md) then create a custom policy to block **Shared Power Apps** and assign the policy to some users.

   :::image type="content" source="media/manage-power-platform-apps-app-permission-policy.png" alt-text="Screenshot of example custom policy for app permissions with Shared Power Apps blocked.":::

* If using [app centric management](app-centric-management.md) then modify the app availability to select only the desired users.

## Use audit logs to check Microsoft Power Platform installation activity

You can use audit logs for Teams to investigate events where users installed Microsoft Power Platform apps from Teams store. To do this, [search the audit log](/purview/audit-teams-audit-log-events) for the **Installed app** Teams event (under the **AppInstalled** operation) for a user or set of users. Look for the **TemplatedInstance** value in the **AppDistributionMode** property in a given record's details.

:::image type="content" source="media/manage-power-platform-apps-audit.png" alt-text="Screenshot of the TemplatedInstance value in the AppDistributionMode property." lightbox="media/manage-power-platform-apps-audit.png":::

> [!TIP]
> You can export audit records in CSV format for easier filtering.

## Related articles

* [Share a canvas app in Power Apps](/power-apps/maker/canvas-apps/share-app)
* [Share your bot with other users](/microsoft-copilot-studio/admin-share-bots)
* [Manage apps in the Microsoft Teams admin center](manage-apps.md)
* [Publish a custom app submitted through the Teams App Submission API](submit-approve-custom-apps.md)
