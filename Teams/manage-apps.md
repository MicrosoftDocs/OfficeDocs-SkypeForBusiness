---
title: Manage your apps in the Microsoft Teams admin center
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.service: msteams
ms.subservice: teams-apps
ms.custom: intro-get-started
audience: admin
ms.collection: 
  - M365-collaboration
  - m365-frontline
ms.reviewer: vaibhava
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Learn how to manage Teams apps. Learn to allow or block apps, check org-level status and app properties, upload custom apps, and manage app settings.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Manage Teams apps in the Microsoft Teams admin center

You manage apps for your organization in **Teams apps** page in the Teams admin center portal. Use the Manage apps page to view and manage all Teams apps in your organization's app catalog, cater to prominent use cases for app management, define access to apps using policies, and more.

:::image type="content" source="media/manage-apps.png" alt-text="Screenshot of the Manage apps page." lightbox="media/manage-apps.png":::

To manage apps, you use policies to control permissions for users, installation of apps, and upload of custom apps created within your organization. To understand policies, see [Overview of app policies](app-policies.md).

To use Teams admin center, you must have a Global Admin or Teams Administrator role. For details, see [Teams administrator roles](./using-admin-roles.md) and [Microsoft 365 administrator roles](/microsoft-365/admin/add-users/about-admin-roles).

> [!NOTE]
> The Manage apps page isn't available in Microsoft 365 Government Community Cloud High (GCCH) or Department of Defense (DoD) deployments of Teams.

During the creation of an app, the developers create and add an app ID to the manifest file. You can view this external app ID on the Manage apps page after you enable the column `External app ID` from the column settings. You can also view it on the app details page of a custom app. The ID is applicable for custom apps only.

## App management use cases and the available interfaces

The options to accomplish most of app management use cases are available in Teams admin center. In addition, some options are available in other portals or different pages in the Teams admin center.

App management tasks that are supported in admin center are in the table below.

| App management use cases | Link to the interface | Documentation |
|:----|:----|:----|
| Control which apps are available to users in your organization by allowing and blocking apps. You can also upload and approve custom apps. After managing apps on this page, you can use app permission and app setup policies to configure what apps are available for specific users in your organization's app store. | [Manage apps in Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps) | Current article |
| App permission policies control what apps you want to make available to Teams users in your organization. You can use the Global (Org-wide) default policy and customize it, or you can create one or more policies to meet the needs of your organization. | [Permission policies](https://admin.teams.microsoft.com/policies/app-permission) | [Manage app permission policies](teams-app-permission-policies.md) |
| App setup policies control how apps are made available to a user with the Teams app. Use the Global (Org-wide default) policy and customize it or create custom policies and assign them to a set of users. | [Setup policies](https://admin.teams.microsoft.com/policies/app-setup) | [Manage app setup policies](teams-app-setup-policies.md) |
| You can develop and upload custom apps as app packages and make them available in your organization's app store. | Org-wide app settings in [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) | [Manage custom app policies](teams-custom-app-policies-and-settings.md) |
| You can customize the Teams app store with your organization's logo, custom background, or color. | [Customize store](https://admin.teams.microsoft.com/policies/customize-appstore) | [Customize your organization's app store](customize-your-app-store.md) |
| The Teams app usage report provides information about which apps in use, active users, and other app usage information. | [Usage reports](https://admin.teams.microsoft.com/analytics/reports) | [Teams app usage report](teams-analytics-and-reports/app-usage-report.md) |
| Your users can add apps when they host meetings or chats with guests. They can also use apps shared by guests when they join meetings or chats hosted externally. The data policies of the hosting user's organization, and the data sharing practices of any third-party apps shared by that user's organization, are applied. | [External access](https://admin.teams.microsoft.com/company-wide-settings/external-communications) | [App behavior depending on types of users](non-standard-users.md) |
| With guest access, you can provide access to applications and other Teams functionality to people outside your organization, while maintaining control over your corporate data. | [Guest access](https://admin.teams.microsoft.com/company-wide-settings/guest-configuration) | [Guest access in Teams](guest-access.md) |
| Teams update policies are used to manage Teams and Office preview users that can see pre-release or preview features in the Teams app. | [Teams update policies](https://admin.teams.microsoft.com/policies/updatemanagement) | [Teams public preview](public-preview-doc-updates.md) |

App management tasks that are supported on other portals are in the table below.

| App management use cases | Link to the interface | Documentation |
|:----|:----|:----|
| Manage licenses and subscriptions of third-party apps in Microsoft 365 admin center | [Microsoft 365 admin center](https://admin.microsoft.com/#/licenses) | [Manage third-party app subscriptions](/microsoft-365/commerce/manage-saas-apps) |
| Audit Teams app events on Microsoft Purview compliance portal. | [Audit](https://compliance.microsoft.com/auditlogsearch?viewid=Async%20Search) | [Teams activities](audit-app-management-activities.md) |
| Applications can be granted permissions to your organization and its data by three methods: an admin consents to the application for all users, a user grants consent to the application, or an admin integrating an application and enabling self-service access or assigning users directly to the application. Verify the Graph permissions for apps. Verify the permissions that users provided or that the admins delegated. | [Azure AD portal](https://aad.portal.azure.com/) | [Review permissions granted to applications](/azure/active-directory/manage-apps/manage-application-permissions) |

<!---
| xxx | [Manage users](https://admin.teams.microsoft.com/users) | [Add users and assign licenses](/microsoft-365/admin/add-users/add-users?view=o365-worldwide) |  
--->

## Allow and block apps

The Manage apps page is where you allow or block individual apps at the org level. The page displays all the available app and their current org-level app status. The list of apps includes apps provided by Microsoft, by third-party developers, and by developers within your organization.

To allow or block an app:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**
1. Select an app from the list of apps. You can search by the name of the app.
1. Select **Allow** or **Block** option.

When you allow (or block) an app on the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center, the particular app is allowed (or blocked) for all users in your organization. This method differs from the app permission policy in the context that allowing (or blocking) an app via permission policy, impacts only the specific users who are assigned the policy.

A user can install and use an app only when the app is allowed via the tenant-wide setting and allowed for the user via permission policy.

## Allow the apps that are blocked by the developers

When a developer publishes an app to the Teams store, some apps might need an admin to configure the app. The admins make the app available to the end-users when the app is set up.

For example, Contoso Electronics is an app developer that created a help desk app for Microsoft Teams. Contoso Electronics wants its customers to set up certain properties of the app so that when users interact with the app, it functions as expected. Before an admin allows the application, it will show as **Blocked by publisher** in the Teams admin center and is hidden from end-users by default. After following the publisher's guidance to set up the app, you can make it available to users by changing the status to **Allowed**.

:::image type="content" source="media/blocked-by-publisher.png" alt-text="Screenshot of blocked by publisher status in Teams admin center.":::

For information about how developers block an app by default, see [enable apps to be blocked until an admin allows it](/microsoftteams/platform/concepts/design/enable-app-customization#hide-teams-app-until-admin-approves).

## Manage org-wide app settings

Use org-wide app settings to control whether users with an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt) get the tailored frontline app experience, whether users can install third-party apps, and whether users can upload or interact with custom apps in your organization. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users.

> [!NOTE]
> To learn how to use org-wide app settings in Microsoft 365 Government - Government Community Cloud High GCCH and Department of Defense (DoD) deployments of Teams, see [Manage app permission policies in Teams](teams-app-permission-policies.md).

1. On **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page, select **Org-wide app settings**. You can then configure the settings you want in the pane.

    :::image type="content" source="media/manage-apps-org-wide-app-settings.png" alt-text="Screenshot of the Org-wide app settings pane on the Manage apps page":::

1. Under **Tailored apps**, turn off or turn on **Show tailored apps**. When this setting is on, users with an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt) get the tailored frontline app experience. This experience pins the most relevant apps in Teams for frontline workers. To learn more, see [Tailor Teams apps for your frontline workers](pin-teams-apps-based-on-license.md).

    This feature is available for F licenses. Other license types will be supported in the future.
1. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    * **Allow third-party apps**: This controls whether users can use third-party apps. If you turn off this setting, your users won't be able to install or use any third-party apps and the app status of these apps is displayed as **Blocked org-wide** in the table.

        > [!NOTE]
        > When **Allow third-party apps** is off, [outgoing webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors) are still enabled for all users, but you can control them at the user level by allowing or blocking the Outgoing Webhook app through [app permission policies](teams-app-permission-policies.md). Note that if you have existing [app permission policies](teams-app-permission-policies.md) for **Microsoft apps** that use the **Allow specific apps and block all others** setting, and you want to enable outgoing webhooks for users, add the Outgoing Webhook app to the list.

        > [!NOTE]
        > Teams users can add apps when they host meetings or chats with people from other organizations. They can also use apps shared by people in other organizations when they join meetings or chats hosted by those organizations. The data policies of the hosting user's organization, as well as the data sharing practices of any third-party apps shared by that user's organization, are applied.

    * **Allow any new third-party apps published to the store by default**: This controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

1. Under **Custom apps**, turn off or turn on **Allow interaction with custom apps**. This setting controls whether users can interact with custom apps. To learn more, see [Manage custom app policies and settings in Teams](teams-custom-app-policies-and-settings.md).
1. Select **Save** for org-wide app settings to take effect.

## Related article

* [Manage Teams during the transition from Skype for Business admin center](manage-teams-skypeforbusiness-admin-center.md)
* [Manage user requests to allow apps](user-requests-approve-apps.md).
