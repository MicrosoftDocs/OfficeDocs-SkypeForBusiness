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
ms.date: 05/21/2024
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
- ACM migration wizard docs
- TAC deploy docs
--->

## What is unified app management

App developers can create apps that work in not just Microsoft Teams but also in Microsoft Outlook and in Microsoft 365 App. Such apps are available in app store and as custom apps. You can evaluate an app once and deploy it everywhere if it meets your org requirements. To make app governance easier, we are introducing unified app management feature.

Till now, you manage the same app separately in the following two place that can lead to potentially conflicting settings for the same app and some admin confusion.

* In the Integrated apps page in Microsoft 365 Admin Center. It has governance controls for Outlook and the Microsoft 365 App surfaces. For more information, see [integrated apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps). The changes made here affect only Teams apps in Outlook and the Microsoft 365 app.
* In the Manage apps page in Teams Admin Center. It has governance control for apps for Teams client. The changes you make in the Teams admin center, impact apps in only Teams.

We shall introduce a functionality that allows you to easily manage your app availability across supported clients in a consistent way. Your intent and desired outcomes synchronize across the admin centers to ensure. You don't have to use two different admin center UIs to manage the same app.

> [!IMPORTANT]
> The feature is available only if you've [migrated to app centric management](app-centric-management.md#migrate). If your org is using permission policies to manage access to apps, then the unification of admin settings doesn't happen in your org.

## Understand the impact on your organization

* App catalog: The app catalog now displays the hosts as Teams, Outlook, or the Microsoft 365. Without this feature, you can't quick find out the supported hosts.
* Organization-wide settings: App availability default settings apply to apps used in Teams, Outlook, and Microsoft 365 app.
* App deployment: Apps deployed from the Integrated apps page in Microsoft 365 admin center are preinstalled in all applicable hosts for the app. Unlike app installation in the Teams app setup policy, app deployment provides access to the previously installed apps, similar to deploying the app for Outlook and the Microsoft 365.
* App availability: You can manage the availability of individual apps for its applicable app hosts. Blocking or allowing apps apply to all applicable app hosts.
* Existing app settings: The unification of settings happen automatically. The changes can't be undone. See [how to prepare](#how-to-prepare-for-the-upcoming-migration).

## Identify apps that work on multiple hosts

Some apps are Teams only and other apps work across multiple. To identify the hubs in which your app works, do one of the following:

* In Teams admin center, on the Manage apps page, see the icons in the **Supported on** column. Each icon represents the applicable host for each app.

   :::image type="content" source="media/tac-supported-column.png" alt-text="Screenshot showing the column that displays icons of supported Microsoft 365 products for each app." lightbox="media/tac-supported-column-large.png":::

* In Microsoft 365 admin center, open the [**Integrated apps**](https://admin.microsoft.com/Adminportal/Home#/Settings/IntegratedApps) > **Available apps**. Locate the product icons.

   :::image type="content" source="media/integrated-apps-filter.png" alt-text="Screenshot showing the option to filter the list of apps based on host product." lightbox="media/integrated-apps-filter-large.png":::

## Outcomes of admin actions across admin centers

Unification rules are the same for Microsoft, third-party apps, and custom apps.

Outcomes for Org-wide app settings.

| Teams admin center                                         | Microsoft 365 admin center                                 | Unification outcome           |
|------------------------------------------------------------|------------------------------------------------------------|-------------------------------|
| Let users install and use available apps by default is On  | All users can install apps on their own                    | Users can install apps        |
| Let users install and use available apps by default is Off | Only admins can install apps for users                     | Admins install apps for users |
| Let users install and use available apps by default: Off   | All users can install apps on their own                    | Users can install apps        |
| Let users install and use available apps by default: On    | Only admins can install apps for users in the organization | Users can install apps        |

Outcomes for allow or block setting applied to a particular app.

| Teams admin center | Microsoft 365 admin center | Unification outcome |
|--------------------|----------------------------|---------------------|
| Allowed            | Allowed                    | Allowed             |
| Blocked            | Blocked                    | Blocked             |
| Allowed            | Blocked                    | Blocked             |
| Blocked            | Allowed                    | Blocked             |

Outcomes of app availability setting applied to a particular app.

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

Outcomes of app deployment setting applied to a particular app.

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

The upcoming availability of this feature is meant for organizations that are using default settings in either Microsoft 365 admin center or Teams admin center. for organization-wide defaults, app deployment, app availability, or block/unblock. After this release, any app management setting configured in either admin centers will apply to all the relevant clients.

We recommend that you do the following preparation in advance:

* Review the individual settings for desired apps and org-wide app settings for your org in the admin centers. If different departments manage it in your organization, we recommend conducting these reviews collaboratively.

* Review the unification rules and consider the potential impact on app availability in your organization. Make the necessary adjustments to the app-level or org-level settings in advance.

* Update the relevant internal documentation as appropriate.

No action is required by you to make the feature available - it will be automatically made available to your organization.

## Related articles

* [Integrated apps](/microsoft-365/admin/manage/teams-apps-work-on-outlook-and-m365)
* [Get started with Integrated apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps)
