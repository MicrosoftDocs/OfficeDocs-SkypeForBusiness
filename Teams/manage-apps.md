---
title: Manage your apps in the Microsoft Teams admin center
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-apps
ms.custom: intro-get-started
audience: admin
ms.date: 09/04/2024
ms.collection: 
  - M365-collaboration
  - tier2
  - highpri
ms.reviewer: mhayrapetyan
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Learn how to manage Teams apps. Learn to allow or block apps, check org-level status and app properties, upload custom apps, and manage app settings.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# Overview of app management and governance in Teams admin center

In the Teams admin center, we provide a few dedicated pages to manage your apps with granularity and complete control. You manage apps for your organization in the **Manage apps** page in the Teams admin center portal. Use the URL [https://admin.teams.microsoft.com/policies/manage-apps](https://admin.teams.microsoft.com/policies/manage-apps) to view and govern all Teams apps that are available in your organization's app catalog, define access to apps using policies, cater to prominent use cases for app management, and more.

:::image type="content" source="media/manage-apps.png" alt-text="Screenshot showing the Manage apps page in Teams admin center." lightbox="media/manage-apps.png":::

To use Teams admin center, you must have a Teams Administrator role. For details, see [Teams administrator roles](./using-admin-roles.md) and [Microsoft 365 administrator roles](/microsoft-365/admin/add-users/about-admin-roles). Some admins with a higher privilege role can accomplish app governance tasks but we recommend using the lower privilege role when possible.

App developers [extend Microsoft 365 Copilot](/microsoft-365-copilot/extensibility/) by creating Copilot agents, for example, Microsoft Teams message extension or a Power Platform connector. These Copilot agents increase user productivity across daily tasks and workflows. Admins manage Copilot agents in the [Integrated apps page](/microsoft-365/admin/manage/manage-plugins-for-copilot-in-integrated-apps) of the Microsoft 365 admin center.

> [!NOTE]
> You can only view and manage apps that are deployed in the same release channel as your tenant is. For example, if your tenant is in the general release channel then you can't manage apps that are deployed in the private or public preview channels. This isn't an issue for apps that are released to the general release channel.

## App management use cases and the available interfaces

The options to accomplish most of app management use cases are available in Teams admin center. In addition, some options are available in other portals or different pages in the Teams admin center.

App management tasks that are supported in admin center are in the table below.

| App management use cases | Link to the interface | Documentation |
|:-------------------------|:----------------------|:--------------|
| Control which apps are available to users in your organization by allowing and blocking apps. You can also upload and approve custom apps. After managing apps on this page, you can use app permission and app setup policies to configure what apps are available for specific users in your organization's app store. | [Manage apps in Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps) | Current article |
| App permission policies control what apps you want to make available to Teams users in your organization. You can use the Global (Org-wide) default policy and customize it, or you can create one or more policies to meet the needs of your organization. | [Permission policies](https://admin.teams.microsoft.com/policies/app-permission) | [Manage app permission policies](teams-app-permission-policies.md) |
| App setup policies control how apps are made available to a user with the Teams app. Use the Global (Org-wide default) policy and customize it or create custom policies and assign them to a set of users. | [Setup policies](https://admin.teams.microsoft.com/policies/app-setup) | [Manage app setup policies](teams-app-setup-policies.md) |
| You can develop and upload custom apps as app packages and make them available in your organization's app store. | Org-wide app settings in [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) | [Manage policy setting for custom apps](teams-custom-app-policies-and-settings.md) |
| You can customize the Teams app store with your organization's logo, custom background, or color. | [Customize store](https://admin.teams.microsoft.com/policies/customize-appstore) | [Customize your organization's app store](customize-your-app-store.md) |
| The Teams app usage report provides information about which apps in use, active users, and other app usage information. | [Usage reports](https://admin.teams.microsoft.com/analytics/reports) | [Teams app usage report](teams-analytics-and-reports/app-usage-report.md) |
| Your users can add apps when they host meetings or chats with guests. They can also use apps shared by guests when they join meetings or chats hosted externally. The data policies of the hosting user's organization, and the data sharing practices of any third-party apps shared by that user's organization, are applied. | [External access](https://admin.teams.microsoft.com/company-wide-settings/external-communications) | [App behavior depending on types of users](apps-external-users.md) |
| With guest access, you can provide access to applications and other Teams functionality to people outside your organization, while maintaining control over your corporate data. | [Guest access](https://admin.teams.microsoft.com/company-wide-settings/guest-configuration) | [Guest access in Teams](guest-access.md) |
| Teams update policies are used to manage Teams and Office preview users who can see prerelease or preview features in the Teams app. | [Teams update policies](https://admin.teams.microsoft.com/policies/updatemanagement) | [Teams public preview](public-preview-doc-updates.md) |

App management tasks that are supported on other portals are in the table below.

| App management use cases | Link to the interface | Documentation |
|:-------------------------|:----------------------|:--------------|
| Manage licenses and subscriptions of third-party apps in Microsoft 365 admin center | [Microsoft 365 admin center](https://admin.microsoft.com/#/licenses) | [Manage third-party app subscriptions](/microsoft-365/commerce/manage-saas-apps) |
| Audit Teams app events on Microsoft Purview compliance portal. | [Audit](https://compliance.microsoft.com/auditlogsearch?viewid=Async%20Search) | [Teams activities](audit-app-management-activities.md) |
| Applications can be granted permissions to your organization and its data by three methods: an admin consents to the application for all users, a user grants consent to the application, or an admin integrating an application and enabling self-service access or assigning users directly to the application. Verify the Microsoft Graph permissions for apps. Verify the permissions that users provided or that the admins delegated. | [Microsoft Entra admin center](https://aad.portal.azure.com/) | [Review permissions granted to applications](/azure/active-directory/manage-apps/manage-application-permissions) |

## Allow or block apps

As an admin, you control access to all [types of apps](apps-in-teams.md#types-of-teams-apps) that are used across your organization. Teams provides granular controls to configure access for each app and for each user.

To allow an app, you must do all of the following settings. To block an app, just use any one of these settings.

| Method                                                                                                           | Scope      | Use case                                                                                  |
|:-----------------------------------------------------------------------------------------------------------------|:-----------|:------------------------------------------------------------------------------------------|
| [Org-wide app settings](#manage-org-wide-app-settings)                                                           | Org-level  | Use this setting to allow use of relevant apps in your org.                               |
| Block or unblock apps                                                                                            | App-level  | Use this setting to allow a specific app in your org. You control which users use an app. |
| [App permission policy](teams-app-permission-policies.md) or [app centric management](app-centric-management.md) | User-level | Let all users or let specific users use an app.                                           |

You allow or block specific apps on either the Manage apps page or in the app details page. Manage apps page displays all the available app and the current org-level app status. To allow or block an app, follow these steps:

1. Sign in to the Teams admin center and access **Teams apps** > **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)**.

1. Select the app on the **Manage apps** page and select **Allow** or **Block** option.

   :::image type="content" source="media/allow-block-option-tac.png" alt-text="Screenshot showing the option to allow or block an app in the Manage apps page.":::

1. Alternately, click on the app name to open its app details page. Change the status between **Allowed** and **Blocked**.

   :::image type="content" source="media/allow-block-option-app-details.png" alt-text="Screenshot showing the option to allow or block an app in the app details page.":::

If you use [app centric management feature](app-centric-management.md), the block option is available in the **Actions** menu.

:::image type="content" source="media/acm-block-app.png" alt-text="Screenshot showing how to block access to an app from the Actions menu when you use manage access by app feature.":::

To allow an app for specific users, see [app permission policies](teams-app-permission-policies.md).

When a developer publishes an app to the Teams store, some apps may need an admin to configure the app. Before an admin allows such an app, it shows as `Blocked by publisher` in the admin center. Before you allow it for users, follow the publisher's guidance to configure the app.

To block all third-party apps, open the **Org-wide app settings** on the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page and disallow the use of third-party apps. If you use [manage access by apps feature](app-centric-management.md), you can also block the [apps created by Microsoft](apps-in-teams.md#apps-created-by-microsoft).

> [!NOTE]
> From within the Teams client, your users can request you to allow the apps that aren't available for them. You receive notifications and can allow the app. For details, see [view and manage user requests](user-requests-approve-apps.md).

## Allow access to an app for users and groups

As an admin, you use one of the following methods to define access to apps for your users:

* [App permission policies](teams-app-permission-policies.md) if you use policy-based method to define app access.
* App assignment if you use [app centric management](app-centric-management.md) to define app access.

## Manage org-wide app settings

Use org-wide app settings to control whether users with an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline) get the tailored frontline app experience, whether users can install third-party apps, and whether users can upload custom apps in your organization.

1. On **[Manage apps](https://admin.teams.microsoft.com/policies/manage-apps)** page, select **Org-wide app settings**. You can then configure the settings you want in the pane.

    :::image type="content" source="media/manage-apps-org-wide-app-settings.png" alt-text="Screenshot of the Org-wide app settings pane on the Manage apps page":::

1. Under **Tailored apps**, turn off or turn on **Show tailored apps**. When this setting is on, users with an [F license](https://www.microsoft.com/microsoft-365/enterprise/frontline#office-SKUChooser-0dbn8nt) get the tailored frontline app experience. This experience pins the most relevant apps in Teams for frontline workers. To learn more, see [Tailor Teams apps for your frontline workers](pin-teams-apps-based-on-license.md).

    This feature is available for F licenses. Other license types will be supported in the future.
1. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps in your organization:

    * **Allow third-party apps**: This setting controls whether users can use third-party apps. If you turn off this setting, your users can't add or use any third-party apps. App status of these apps shows as **Blocked org-wide**.

        > [!NOTE]
        > When **Allow third-party apps** is off, [outgoing webhooks](/microsoftteams/platform/webhooks-and-connectors/what-are-webhooks-and-connectors) are still enabled for all users, but you can control them at the user level by allowing or blocking the Outgoing Webhook app through [app permission policies](teams-app-permission-policies.md).

    * **Allow any new third-party apps published to the store by default**: This setting controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

1. Under **Custom apps**, turn off or turn on **Let users install and use available apps by default** option. This setting controls whether users can install and use the custom apps that you make available to them. To learn more about custom apps, see [how to manage custom apps](teams-custom-app-policies-and-settings.md).

1. Select **Save**. The settings take effect after a few hours.

Admin center settings may allow your users to collaborate with users from other organizations. To understand how apps work with external users in meetings, see [Teams apps for external attendees](apps-external-users.md).

## Install apps or let users install apps and uninstall apps

IT admins can install Teams apps for some or all users in their organization. Developers may create some Teams apps to work on Outlook and Microsoft 365 Apps (formerly office.com). You can easily preinstall the apps on all the supported hosts. Alternately, you can let users install apps on their own. A few supported apps can also be auto-installed if a user uses it outside teams. For details, see [how to preinstall apps](install-teams-apps.md).

## Manage org-wide app settings for Microsoft 365 Government

In a Microsoft 365 Government - GCC, GCCH and DoD deployment of Teams, all third-party apps are blocked by default. In GCC, you see the following note about managing third-party apps on the app permission policies page in the Microsoft Teams admin center.

:::image type="content" source="media/app-permission-policies-gcc.png" alt-text="Screenshot of app permission policy in GCCH and DoD." lightbox="media/app-permission-policies-gcc.png":::

Use org-wide app settings to control whether users can install third-party apps. Org-wide app settings govern the behavior for all users and override any other app permission policies assigned to users.

1. On the **Teams Apps** > **Manage apps** page, select **Org-wide app settings**. You can then configure the settings you want in the panel.

   :::image type="content" source="media/app-permission-policies-gcc-org-wide.png" alt-text="Screenshot that shows the Org-wide app settings in GCC.":::

1. Under **Third-party apps**, turn off or turn on these settings to control access to third-party apps:

    * **Allow third-party apps**: This option controls whether users can use third-party apps. If you turn off this setting, your users aren't able to add or use any third-party apps. In a Microsoft 365 Government - GCCH and DoD deployment of Teams, this setting is off by default.
    * **Allow any new third-party apps published to the store by default**: This option controls whether new third-party apps that are published to the Teams app store become automatically available in Teams. You can only set this option if you allow third-party apps.

1. Under **Blocked apps**, add the apps you want to block across your organization. For any third-party app you want to allow in your organization, remove the app from this blocked apps list. A blocked app isn't available to any user, regardless of app policies.

1. Select **Save** for org-wide app settings to take effect.

To allow third-party apps, either edit and use the Global (Org-wide default) policy or create and assign an admin-created policy.

## Manage apps in 21Vianet and air-gapped cloud environments

In Microsoft 365 operated by 21Vianet and air-gapped cloud environments, you get an overview of the apps on the Teams apps > Manage apps page.

To view more details of an app, click an app's name to access the app details page. You can allow or block the app for your users.

## Support information for apps

You may have queries about admin settings or configuration, user flows and app features, app troubleshooting, and more. You receive support information about apps from the following two different sources:

* We don't provide direct customer support for Teams apps but we provide the following safeguards, health checks, and certification methods for apps:

  * We proactively check Teams apps for issues and inform the developer to update their app. Scenarios covered are related to app health, functional issues reported by users to Microsoft, security issues, and so on. For details, see [Microsoft enforcement actions for published apps](/microsoftteams/platform/concepts/deploy-and-publish/appsource/post-publish/overview#possible-enforcement-actions).
  * For Publisher Attested and Microsoft 365 certified apps, Microsoft provides the [security and compliance information of apps](overview-of-app-certification.md).
  * Testing of all apps as part of its [app validation program](overview-of-app-validation.md) to ensure that all apps work as advertised. If apps don't work as suggested in the app listing, then we contact app developers to request either an update to the app. If app developers don't make the requested updates after a few reminders, we proactively remove the apps from Teams.
  * Certification to apps using [Microsoft 365 app compliance program](overview-of-app-certification.md) ensures that apps are compliant with the industry-standard frameworks.

### Developer provided app information, support, and documentation

* App developers provide customer support, updates to the apps, security and compliance information, bug fixes, and so on. The app security and compliance information are available in the admin center in app details page as mentioned above. App developers publish app updates, bug fixes, and vulnerability fixes as per their business requirements, issue severity, and service agreements. For direct support requests and inquiry about app updates, contact the app developer at their website address available at the following two places:

  * **App details** page of the app in [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center.

    :::image type="content" source="media/app-details-summary.png" alt-text="Screenshot that shows documentation links in the admin center for an app in its details page." lightbox="media/app-details-large.png":::

  * **Details + support** tab of the app's [AppSource](https://appsource.microsoft.com/) page.

    :::image type="content" source="media/appsource-help-link.png" alt-text="Screenshot that shows help and support link for a Teams app in AppSource.":::

* **Privacy and data access considerations**: In the terms of use and privacy policy of any app, the app developer discloses what data their app uses and how it handles the data. This information is available on app developer's website and you can access the URLs in the app details page in Teams admin center. Many app developers choose to undergo the Microsoft 365 app compliance program. The program checks and audits an app against controls that are derived from leading industry-standard frameworks. The detailed information about each such app is available at [Teams Apps Security and Compliance](/microsoft-365-app-certification/teams/teams-apps).

* App developers can provide their contact information that you can use to chat with them. It helps you quickly evaluate an app and get the needed information from the app developers before you adopt and roll out an app. Some examples of such information are compliance and certification details, data handling details, clarity on pricing plans for paid apps, and app configuration instructions. You can start a chat with app developers by selecting **Start a Teams chat** but only if the app developer provided their contact information. We recommend that you don't share personal and sensitive information in the chat.

   :::image type="content" source="media/chat-with-app-dev.png" alt-text="Screenshot showing the option in the app details page that lets you chat with app developer." lightbox="media/chat-with-app-dev-large.png":::

## Related articles

* [Manage user requests to allow apps](user-requests-approve-apps.md)
* [Auto install approved apps in Teams](auto-install-approved-apps.md)
* [Install and pin apps via setup policies](teams-app-setup-policies.md)
* [Overview of policies to govern apps](app-policies.md).
