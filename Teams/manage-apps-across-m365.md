---
title: Manage apps that work across Outlook and Microsoft 365 App
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: conceptual
ms.service: msteams
ms.subservice: teams-apps
ms.custom: intro-get-started
audience: admin
ms.date: 07/08/2024
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
# Manage apps that work across Teams, Outlook, and Microsoft 365 App

> [!IMPORTANT]
> * This feature is **not** available in the admin centers yet. For more information, see [Microsoft 365 Roadmap 393931](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=393931).
> * The feature is available only if you use [app centric management](app-centric-management.md) in your organization. If your org uses permission policies, then the unification of admin settings doesn't apply in your org.

## What is unified app management

App developers can create apps that work  not only in Microsoft Teams but also in Microsoft Outlook and in Microsoft 365 App (previously known as Office.com). Such apps are available in app store and as custom apps. You can evaluate an app once and deploy it everywhere if it meets your org requirements. To simplify  app governance, we're introducing unified app management feature. Until now, you manage the same app separately in the following two places that can lead to potentially conflicting settings for the same app.

* Integrated apps page in Microsoft 365 Admin Center. The app management settings made here affect only apps in Outlook and the Microsoft 365 app. For more information, see [integrated apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

* Manage apps page in Teams Admin Center. It manages apps for Teams client. The changes you make in the Teams admin center, impact apps in only Teams.

Unified app management consolidates app catalog management into a single platform. You can manage apps on the Integrated apps page in the Microsoft 365 admin center or in the Teams admin center. Changes made in either admin center synchronize.

## Understand the impact on your organization

* App catalog: Apps start showing the hosts where the apps are available as Teams, Outlook, or Microsoft 365 app.

* Organization-wide settings: Default settings for app availability will apply to apps used in Teams, Outlook, and Microsoft 365 app.

* App installs: Apps deployed from the Integrated apps page in Microsoft 365 admin center will be preinstalled in all applicable hosts for the app. Unlike app installation in the Teams app setup policy, new app installs will provide access to the previously installed apps. The behavior is similar to deploying the app for Outlook and Microsoft 365 app. For more information, see [Microsoft 365 roadmap 394274](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=394274) and [Message Center post MC795355](https://admin.microsoft.com/?ref=MessageCenter/:/messages/MC795355).

* App availability: Managing app availability applies to all the applicable hosts.

* App block or unblock: Blocking or unblocking apps applies to all the applicable hosts.

* Consolidation of the existing app settings: All existing settings are unified between Integrated apps and Manage apps pages across both the admin centers. To know the merge rules that decide the impact, see [outcomes of settings across admin centers](#outcomes-of-admin-actions-across-admin-centers). In the admin centers, we'll provide an on-demand report for you to understand the impact of these changes in your org.

* Existing app settings: The unification of settings happens automatically. The changes can't be undone.

## Outcomes of admin actions across admin centers

Merge rules are the same for Microsoft, third-party apps, and custom apps.

Outcomes for Org-wide app settings.

| Teams admin center                                         | Microsoft 365 admin center                                  | Unification outcome                                        |
|------------------------------------------------------------|-------------------------------------------------------------|------------------------------------------------------------|
| Let users install and use available apps by default is On  | All users in the organization can install apps on their own | Users can install apps                                     |
| Let users install and use available apps by default is Off | Only admins can install apps for users in the organization  | Only admins can install apps for users in the organization |
| Let users install and use available apps by default: Off   | All users in the organization can install apps on their own | Users can install apps                                     |
| Let users install and use available apps by default: On    | Only admins can install apps for users in the organization  | Users can install apps                                     |

Outcomes for unblock or block setting applied to a particular app.

| Teams admin center | Microsoft 365 admin center | Unification outcome |
|--------------------|----------------------------|---------------------|
| Unblocked          | Unblocked                  | Unblocked           |
| Blocked            | Blocked                    | Blocked             |
| Unblocked          | Blocked                    | Blocked             |
| Blocked            | Unblocked                  | Blocked             |

Outcomes of app availability setting applied to a particular app.

| Teams admin center                                  | Microsoft 365 admin center                           | Unification outcome                                         |
|-----------------------------------------------------|------------------------------------------------------|-------------------------------------------------------------|
| No one                                              | No user in the organization can install              | No one                                                      |
| No one                                              | All users in the organization can install            | Everyone                                                    |
| No one                                              | Specific users/groups can install                    | Specific users & groups                                     |
| Specific users & groups                             | Specific users/groups can install                    | Specific users & groups                                     |
| Specific users & groups (example: Marketing, Legal) | Specific users/groups can install (example: Marketing, Design) | Specific users & groups (example: Legal, Design, Marketing) |
| Specific users & groups                             | No user in the organization can install              | Specific users & groups                                     |
| Everyone                                            | All users in the organization can install            | Everyone                                                    |
| Everyone                                            | No user in the organization can install              | Everyone                                                    |
| Everyone                                            | Specific users/groups can install                    | Everyone                                                    |

Outcomes of app deployment setting applied to a particular app.

| Teams admin center                                  | Microsoft 365 admin center                           | Unification outcome                                         |
|-----------------------------------------------------|------------------------------------------------------|-------------------------------------------------------------|
| No one                                              | -                                                    | No one                                                      |
| No one                                              | Specific users/groups                                | Specific users & groups                                     |
| No one                                              | Entire organization                                  | Everyone                                                    |
| Specific users & groups                             | -                                                    | Specific users & groups                                     |
| Specific users & groups (example: Marketing, Legal) | Specific users/groups (example: Marketing, Design)   | Specific users & groups (example: Legal, Design, Marketing) |
| Specific users & groups                             | Entire organization                                  | Everyone                                                    |
| Everyone                                            | -                                                    | Everyone                                                    |
| Everyone                                            | Specific users/groups                                | Everyone                                                    |
| Everyone                                            | Entire organization                                  | Everyone                                                    |
| Everyone                                            | No state (default is `None`)                         | Everyone                                                    |

## Related articles

* [How to enable app centric management functionality](app-centric-management.md)
* [Integrated apps](/microsoft-365/admin/manage/teams-apps-work-on-outlook-and-m365)
* [Get started with Integrated apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps)
