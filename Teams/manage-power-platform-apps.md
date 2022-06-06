---
title: Manage Microsoft Power Platform apps in the Microsoft Teams admin center
author: guptaashish
ms.author: guptaashish
manager: prkosh
ms.reviewer: joglocke
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
appliesto: 
- Microsoft Teams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: In this learning path, learn how to manage access to custom apps built on Microsoft Power Platform in the Microsoft Teams admin center.
---

# Manage Microsoft Power Platform apps in the Microsoft Teams admin center

## Microsoft Power Platform apps in Teams

This article gives you an overview of how to manage [Microsoft Power Platform](https://powerplatform.microsoft.com/) apps in the Microsoft Teams admin center.

> [!NOTE]
> This article applies to custom apps created by makers in your organization using Power Apps or Power Virtual Agents. These custom apps are automatically added to Teams. This article doesn't apply to the Power Apps app or Power Virtual Agents app that are installed from the Apps page or pinned to Teams through an app setup policy. You manage those apps as you would for any other app on the [Manage apps](manage-apps.md) page, using [app permission policies](teams-app-permission-policies.md), and [app setup policies](teams-app-setup-policies.md).

[Power Apps](https://powerapps.microsoft.com) is a low-code/no-code application development environment that makers in your organization can use to build custom apps that connect to your business data. [Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) is a no-code bot building environment for makers to create powerful bots. With the integration of Microsoft Power Platform apps into Teams, organizations can streamline business processes, respond to changing business needs more rapidly to drive greater collaboration, and create and share custom solutions to be more productive.  

Microsoft Power Platform apps created by makers in your organization are automatically added to Teams. Makers can control who can access their app by using the [sharing feature in Power Apps](/powerapps/maker/canvas-apps/share-app) and the [sharing feature in Power Virtual Agents](/power-virtual-agents/admin-share-bots).

When a Microsoft Power Platform app is created or shared, users can view and install it on the Apps page by going to **Built for *Your Organization Name*** > **Built by your colleagues**. (It might take a few minutes after an app is created or shared for the app to appear here.)

:::image type="content" source="media/manage-power-platform-apps-apps-page.png" alt-text="Screenshots of Apps page, showing Microsoft Power Platform apps listed in Built by your colleagues":::

A user will see an app in **Built by your colleagues** if the app meets one of the following conditions.

|Power Apps |Power Virtual Agents  |
|---------|---------|
|<ul><li>The user created the app.</li><li>The app was shared directly with the user.</li><li>The user recently used the app. </li></ul>| <ul><li>The user created the bot.</li><li>The bot is owned by a team the user is a member of. </li></ul>        |

Users install Microsoft Power Platform apps in the same way they install any other Teams app. Keep in mind that users can only install  apps to the context to which they have permissions, for example, a team they own, a chat that they're a part of, or their personal scope.

## Manage access to Microsoft Power Platform apps in the Microsoft Teams admin center

As an admin, you can control whether Microsoft Power Platform apps are listed in **Built by your colleagues** on the Apps page in Teams. You can collectively block or allow all apps created in Power Apps or all apps created in Power Virtual Agents at the org level on the [Manage apps](manage-apps.md) page or for specific users using [app permission policies](teams-app-permission-policies.md).

The **Shared Power Apps** and **Shared Power Virtual Agent Apps** apps in your organization's app store represent all apps created on that particular platform. If you block one or both these apps at the org level or for specific users, those users can't see any apps from those platforms in **Built by your colleagues** and can't install them in Teams.  

Keep in mind that you can control access to all apps created in Power Apps and Power Virtual Agents but you can't allow or block individual apps. Makers decide who can access the apps they create through the sharing feature from within Power Apps and Power Virtual Agents. If a maker shared an app they created in Power Virtual Agents with a user and you blocked **Shared Power Virtual Agents Apps** for that user, the user won't be able to see or install any apps from that platform in Teams.

If a user is allowed to access apps from Power Apps or Power Virtual Agents, and you then block the user from accessing apps from one or both these platforms, the user can still access and use Microsoft Power Platforms apps that they installed before you blocked the app or apps. However, the user can no longer see or install any apps from those platforms in **Built by your colleagues**.

> [!NOTE]
> The **Allow interaction with custom apps** org-wide app setting on the [Manage apps](manage-apps.md) page applies to everyone in your organization and governs whether they can interact with custom apps. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users. By default, this setting is turned on. If this setting is turned off, users in your organization can't see or install any custom apps, including Microsoft Power Platform apps. To learn  more, see [Manage org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

### Allow or block Microsoft Power Platform apps for your organization

By default, **Shared Power Apps** and **Shared Power Virtual Agent Apps** are allowed for all Teams users in your organization. You can block or allow them at the org level on the [Manage apps](manage-apps.md) page of the Microsoft Teams admin center.  

1. In the left pane of the Microsoft Teams admin center, go to **Teams apps** > **Manage apps**. You must be a global admin or Teams service admin to access the page.
2. In the list of apps, do one of the following.

    :::image type="content" source="media/manage-power-platform-apps-manage-apps.png" alt-text="Screenshot of Manage apps page, showing shared Microsoft Power Platform apps":::

    - To block apps created in Power Apps or Power Virtual Agents for all users in your organization, search for **Shared Power Apps** or **Shared Power Virtual Agent Apps**, select it, and then click **Block**.
    - To allow apps created in Power Apps or Power Virtual Agents for all users in your organization, search for **Shared Power Apps** or **Shared Power Virtual Agent Apps**, select it, and then click **Allow**.

### Allow or block Microsoft Power Platform apps for specific users

To allow or block specific users in your organization from accessing apps created in Power Apps or Power Virtual Agents, create and assign one or more custom [app permission policies](teams-app-permission-policies.md).

For example, to block specific users from accessing apps created in Power Apps, create a custom app permission policy to block **Shared Power Apps**, and then assign the policy to those users.

:::image type="content" source="media/manage-power-platform-apps-app-permission-policy.png" alt-text="Screenshot of example custom app permission policy with Shared Power Apps blocked.":::

### Use audit logs to investigate Microsoft Power Platform installation activity

You can use audit logs for Teams to investigate events where users installed Microsoft Power Platform apps from the **Built by your colleagues** section of the Apps page in Teams. To do this, [search the audit log](./audit-log-events.md) for the **Installed app** Teams event (under the **AppInstalled** operation) for a user or set of users. To find apps installed from **Built by your colleagues**, look for the **TemplatedInstance** value in the **AppDistributionMode** property in a given record's details.

:::image type="content" source="media/manage-power-platform-apps-audit.png" alt-text="Screenshot of the TemplatedInstance value in the AppDistributionMode property.":::

> [!NOTE]
> You can export audit records in CSV format for easier filtering.

## Related topics

- [Share a canvas app in Power Apps](/powerapps/maker/canvas-apps/share-app)
- [Share your bot with other users](/power-virtual-agents/admin-share-bots)
- [Manage apps in the Microsoft Teams admin center](manage-apps.md)
- [Manage app permission policies in Teams](teams-app-permission-policies.md)
- [Publish a custom app submitted through the Teams App Submission API](submit-approve-custom-apps.md)
