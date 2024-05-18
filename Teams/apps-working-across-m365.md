---
title: Manage apps that work across Outlook and Microsoft 365
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-apps
ms.custom: intro-get-started
audience: admin
ms.date: 05/17/2024
ms.collection: 
  - M365-collaboration
  - tier2
  - highpri
ms.reviewer: mhayrapetyan
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Learn how to manage Teams apps that work across Outlook and Microsoft 365.
appliesto: 
- Microsoft Teams
ms.localizationpriority: medium
---
# Manage apps that work across Teams, Outlook, and Microsoft 365

> [!IMPORTANT]
> This feature is **not** available in the admin centers yet. For information on availability, see Message Center post [MC688930](https://lynx.office.net/messagecenter/MC688930) and [Microsoft 365 Roadmap 393931](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=393931). This feature works only if you use [app centric management](app-centric-management.md) feature in your organization.

<!---
- Expand on what are hosts. Where to find applicable hosts? - the `Supported on` column on Manage apps page lists the icons of the supported surfaces.
- Explain that admins can't manage apps specific to a host
- ACM migration wizard docs
- TAC deploy docs
- consider adding icons or visuals in the tables for yes or no.
--->

Introduction about hubs and existing governance controls:

* App developers can create apps that work in not just Teams but also in Outlook and in Microsoft 365 App.
* Development becomes easier as developers build once and use everywhere. App governance becomes easier as you can evaluate once and deploy everywhere.
* Such apps are available in store and as custom apps. However, until now, you manage the same app separately,

* In the Integrated apps page in Microsoft 365 Admin Center, it has governance controls for Outlook and the Microsoft 365 App surfaces.
* In the Manage apps page in Teams Admin Center, it has governance control for apps for Teams client.

## What is unified app management

We'll soon introduce unified app management feature that allows you to manage your apps from just one of the admin centers. Your intent and desired impact synchronizes across the admin centers to ensure that you don't have to use two different UIs to manage the same app for two different surfaces.

We'll consolidate the management of these apps and ensure that the apps are consistently available across all the supported clients.

Describe integrated apps section in MAC portal?

As an admin, you can discover, purchase, acquire, manage, and deploy apps that work across Teams, Outlook, and Microsoft 365 app.

Till now the changes made in the [Integrated apps](/microsoft-365/admin/manage/teams-apps-work-on-outlook-and-m365) section of the Microsoft 365 admin center affect only Teams apps in Outlook and the Microsoft 365 app. Also, the changes you make in the Teams admin center, impact apps in only Teams.

Link to [Message Center post 393931](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=393931).

## Understand the impact on your organization

<!--- 
- Shall we provide a before-after comparison in a table?
--->

* App catalog enhancements: Catalog displays the hosts (Teams, Outlook, or the Microsoft 365), where the apps are available.
* Organization-wide settings: App availability default settings apply to apps used in Teams, Outlook, and Microsoft 365 app.
* App deployment: Apps deployed from the Integrated apps page in Microsoft 365 admin center are preinstalled in all applicable hosts for the app. Unlike app installation in the Teams App setup policy, app deployment provides access to the previously installed apps, similar to deploying the app for Outlook and the Microsoft 365. (See more [TODO: reference to MC post on app deployment in Teams])
* App availability: Managing individual app availability applies to all applicable app hosts.
* App block/unblock: Blocking or unblocking apps apply to all applicable app hosts.
* Unification of existing app settings: The unification of settings happen automatically in three major phases. Unification changes can't be rolled back.

Without this feature, controls to manage Teams apps that work in Outlook and the Microsoft 365 app are available between the [Integrated apps](https://admin.microsoft.com/Adminportal/Home#/Settings/IntegratedApps) page in the Microsoft 365 admin center and the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page in Teams admin center. This sometimes resulted in different settings for the same app and admin confusion. With unified app management, admins can manage the apps in the applicable admin center and the update synchronizes across all surfaces.






## Identify apps that work on multiple hosts

Some apps are Teams only and other apps work across multiple. To identify the hubs in which your app works, do one of the following:

* In Teams admin center, on the Manage apps page, see the icons in the **Supported on** column. Each icon represents the applicable host for each app.

   :::image type="content" source="media/tac-supported-column.png" alt-text="Screenshot showing the column that displays icons of supported Microsoft 365 products for each app." lightbox="media/tac-supported-column-large.png":::

* In Microsoft 365 admin center, open the [**Integrated apps**](tbd) > **Available apps**. Locate the product icons.

   :::image type="content" source="media/tac-supported-column.png" alt-text="Screenshot showing the column that displays icons of supported Microsoft 365 products for each app." lightbox="media/tac-supported-column-large.png":::

## Outcomes of admin actions across admin centers

Unification rules are the same for Microsoft, third-party apps, and custom apps.

Organization-wide app settings:

| Teams admin center                                         | Microsoft 365 admin center                                 | Unification outcome                     |
|------------------------------------------------------------|------------------------------------------------------------|-----------------------------------------|
| Let users install and use available apps by default is On  | All users can install apps on their own                    | All users can install apps on their own |
| Let users install and use available apps by default is Off | Only admins can install apps for users                     | Only admins can install apps for users  |
| Let users install and use available apps by default: Off   | All users can install apps on their own                    | All users can install apps on their own |
| Let users install and use available apps by default: On    | Only admins can install apps for users in the organization | All uses can install apps on their own  |

Allow or block setting applied to the individual app.

| Teams admin center | Microsoft 365 admin center | Unification outcome |
|--------------------|----------------------------|---------------------|
| Unblocked          | Unblocked                  | Unblocked           |
| Blocked            | Blocked                    | Blocked             |
| Unblocked          | Blocked                    | Blocked             |
| Blocked            | Unblocked                  | Blocked             |

Available To setting applied to the individual app.

| Teams admin center                                  | Microsoft 365 admin center                           | Unification outcome                                         |
|-----------------------------------------------------|------------------------------------------------------|-------------------------------------------------------------|
| No one                                              | No one                                               | No one                                                      |
| No one                                              | Everyone                                             | Everyone                                                    |
| No one                                              | Specific users & groups                              | Specific users & groups                                     |
| Specific users & groups                             | Specific users & groups                              | Specific users & groups                                     |
| Specific users & groups (example: Marketing, Legal) | Specific users & groups (example: Marketing, Design) | Specific users & groups (example: Legal, Design, Marketing) |
| Specific users & groups                             | No one                                               | Specific users & groups                                     |
| Everyone                                            | Everyone                                             | Everyone                                                    |
| Everyone                                            | No one                                               | Everyone                                                    |
| Everyone                                            | Specific users & groups                              | Everyone                                                    |

Deployed to setting applied to the individual app:

| Teams admin center                                  | Microsoft 365 admin center                           | Unification outcome                                         |
|-----------------------------------------------------|------------------------------------------------------|-------------------------------------------------------------|
| No one                                              | No one                                               | No one                                                      |
| No one                                              | Specific users & groups                              | Specific users & groups                                     |
| No one                                              | Everyone                                             | Everyone                                                    |
| Specific users & groups                             | No one                                               | Specific users & groups                                     |
| Specific users & groups (example: Marketing, Legal) | Specific users & groups (example: Marketing, Design) | Specific users & groups (example: Legal, Design, Marketing) |
| Specific users & groups                             | Everyone                                             | Everyone                                                    |
| Everyone                                            | No one                                               | Everyone                                                    |
| Everyone                                            | Specific users & groups                              | Everyone                                                    |
| Everyone                                            | Everyone                                             | Everyone                                                    |
| Everyone                                            | No state (default is `None`)                         | Everyone                                                    |

## How to prepare for the upcoming migration

We recommend that you review app and org settings in the Microsoft 365 admin center and the Teams admin center. If different departments manage it in your organization, we recommend conducting these reviews collaboratively.
We also recommend that you review the unification rules and consider their potential impact on apps in your organization. Make any necessary adjustments to unify them in advance, if the unification rules in this message don't align with your expectations.
This rollout happens automatically by the specified date with no admin action required before the rollout. You may want to update any relevant documentation as appropriate.

## Next steps

* In a few weeks, we'll unify the controls across the portals to make it easy for you to manage apps across all surfaces. The apps will then be consistently available across all supported clients. For more information, see [Message Center post MC688930](https://admin.microsoft.com/Adminportal/Home#/MessageCenter/:/messages/MC688930).

* However, this new feature is available only if you've [migrated to ACM](app-centric-management.md#migrate).

* The upcoming availability of UAM is meant for organizations that are using default settings in either Microsoft 365 admin center or Teams admin center. for organization-wide defaults, app deployment, app availability, or block/unblock.

* After this release, any app management setting configured in either admin centers will apply to all the relevant clients.

## Related articles

* [Integrated apps](/microsoft-365/admin/manage/teams-apps-work-on-outlook-and-m365)
* [Get started with Integrated apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps)
