---
title: App centric management to manage user access to Teams apps
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 02/21/2024
ms.reviewer: mhayrapetyan
description: Manage access to Teams apps using app centric management.
f1.keywords:
- NOCSH
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Use app centric management to manage apps

> [!IMPORTANT]
> If your Teams admin center does not have this feature, it'll receive the feature later. We recommend that you continue to [use app permission policies to control user access to apps](teams-app-permission-policies.md).

App centric management functionality introduces a new way to control how you control access to Teams apps for users and groups. It replaces app permission policies. This functionality lets you specify which users and groups can use each app and you can control it on a per-app basis.

When you start using this functionality, we retain your existing app access that you defined using permission policies. Users continue to have access to only those apps that you've allowed for them.

You can manage access to apps for individual users, supported groups, or everyone in the organization. You have complete control over who can or can't add and use apps in your organization. You can also control the access to new apps that we publish to Teams app store.

## Difference between permission policy and app centric management

Previously, when using permission policies, you determined access to apps using the following three settings:

* Org-wide setting for third-party apps. It applies at an org-level and controls if all third-party apps are available for every user or not.
* App status. It applies at an app-level and controls if it's available to any user or not.
* Permission policy. It applies at a user-level and controls if a specific user is permitted to use an app or not.

App centric management feature simplifies these settings. Each app contains its access definition using a list of users and groups that you assign to the app. It lets you manage each app individually based on your user's needs and organization's compliance and risk posture.

When using this functionality, you determine access to apps using one of the following options for each app:

* **Everyone in the organization**.
* **Specific users or groups**: Only the users and groups that you select can use the app. The supported group types are security groups, Microsoft 365 groups, dynamic user membership groups, nested groups, and the distribution lists.
* **No one**.

The method to block or allow an app changes with this functionality. In the past, to allow access to a user, you'd add the app as an allowed app in a policy and assign that policy to the user. Using this functionality, you just modify the app assignments of an app to allow a user. Also, you don't have to create multiple policies for different combinations across allowed apps and permitted users.

## Add or modify app assignments

To assign users or groups to an app, follow these steps:

1. In Teams admin center, go to the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page, search for the required app, and select the app name to open its app details page.

1. Select the **Assignments** tab.

1. Select **Assign** or **Assign app**.

1. Select the required option from **Manage who can install this app** menu. When assigning users or groups, search for the user or the group from the **Search for users or groups** menu. Select **Apply**.

    :::image type="content" source="media/acm-add-modify-access.png" alt-text="Screenshot showing how to create app assignments from the app details page.":::

1. To remove one or more users or groups from an app, select the rows and select **Remove**.

    :::image type="content" source="media/acm-remove-access.png" alt-text="Screenshot showing how to remove an existing app assignment from the app details page.":::

> [!NOTE]
> You can view and modify the assignments for a blocked app but your assignments apply only when you [allow the app](manage-apps.md#allow-or-block-apps).

## Settings for app availability and how your assignments are preserved

In addition to allowing or blocking apps and creating app assignments, you can also control the default app assignments of any new apps. You can control the default app assignments for each app type. For new organizations, the default setting is set to let users install apps by default. For existing organizations, [old settings are mapped to new access settings](#mapping-between-old-permission-policies-and-new-app-assignments).

To change this default setting, access [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page, select **Actions** > **Org-wide app settings**, and modify the required settings.

The Org-wide app settings apply to:

* All the new apps made available in Teams app store.
* All the existing apps that you didn't actively manage, that is, you didn't change the assignments of.

:::image type="content" source="media/acm-org-wide-app-settings.png" alt-text="Screenshot showing the org-wide app settings in an organization that uses app centric management feature.":::

The Org-wide app settings don’t apply to:

* All apps that have user assignment set to Specific users and groups and saved by you.
* All apps that were assigned to Everyone or to No one and saved individually.
* Any apps in blocked state.

Consider a scenario where you started using the feature and all apps were assigned to everyone. Now, you changed an app's assignment to a specific group or users. After saving this app assignment, if you change the Org-wide app setting titled **Let users install and use available apps by default**, then this particular app continues to be assigned to the specific group or users. Your change to the org-wide app setting applies only to those apps for which you didn't change assignments. Further, if you again change the **Let users install and use available apps by default** setting, the assignments of all other apps are again impacted, except the app that you actively managed.

## View apps in your organization

You can view all apps in the catalog and easily access the app assignments from the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page. You can sort and filter using all three types of app assignments. To get a handy list of Microsoft-provided apps, see [list of Microsoft created apps](apps-in-teams.md#list-of-apps-created-by-microsoft).

:::image type="content" source="media/acm-app-filter.png" alt-text="Screenshot showing how to filter apps by combining various criteria such as assignments, app type, and app status.":::

### View and modify apps assigned to a user

On the **[Manage users](https://admin.teams.microsoft.com/users)** page, select a user to open the user details page, and select the **Apps** tab. The tab lists the apps that the user has access to. To easily locate the type of access for an app, you can search for the name of the app.

:::image type="content" source="media/acm-manage-user-apps-tab.png" alt-text="Screenshot showing how to view all the apps that a user has access to, from the Manage users page.":::

Each app displays the assignment type, which indicates how the user was assigned to the app: through assignment to everyone, direct user assignment, or through a group. The list shows only those apps that are assigned to the user and that are allowed in the organization for use. Apps assigned to no one and app that are blocked in the organization don't appear in this list.

You can remove app assignment for a user. Select an app that is directly assigned to the user and select **Remove**. You can’t remove assignments for a user if the app is available to everyone or to a group.

## Mapping between old permission policies and new app assignments

When your tenant's admin center receives this feature, the following updates are made to the app access. The access to apps doesn't change and the update only maps your existing permission policies to new assignments.

| App permission policy and org settings earlier | Org-wide app settings while using this feature |
|------------------------------------------------|------------------------------------------------|
|  Global permission policy for Microsoft apps was `Allow all` or Global permission policy for Microsoft apps was `Block an app(s), allow all others`  |  `Allow users install available apps by default` for Microsoft apps is set to on |
|  Global permission policy for Microsoft apps was `Block all` or Global permission policy for Microsoft apps was `Allow app(s), Block all others` | `Allow users install available apps by default` for Microsoft apps is set to off |
|  Third party app setting in the Org-wide app settings was set to on; New third-party app setting in the org-wide setting was set to on; Global permission policy for third party apps was `Allow all`; or Global permission policy for third party apps was `Block an app(s), allow all others`  |  `Allow users install available apps by default` for third party apps is set to on |
|  Third party app setting in the Org-wide app settings was set to off; New third-party app setting in the org-wide setting was set to off; Global permission policy for third party apps was `Block all`; or Global permission policy for third party apps was `Allow app(s), Block all others` | `Allow users install available apps by default` for third party apps is set to off |
|  Global permission policy for Custom apps was `Allow all` or Global permission policy for Custom apps was `Block an app(s), allow all others` | `Allow users install available apps by default` for custom apps is set to on |
|  Global permission policy for custom apps was `Block all` or Global permission policy for custom apps was `Allow app(s), Block all others` | `Allow users install available apps by default` for custom apps is set to off |

| App status earlier | Global permission policy definition earlier | App assignments while using the new feature |
|--------------------|---------------------------------------------|---------------------------------------------|
| Blocked            | Blocked                                     | No one can install                          |
| Blocked            | Allowed                                     | No one can install                          |
| Allowed            | Blocked                                     | No one can install                          |
| Allowed            | Allowed                                     | Everyone                                    |

> [!NOTE]
> You can't access, edit, or use permission policies after switching to this feature.

## Related article

* [Use app permission policies to control user access to apps](teams-app-permission-policies.md)
