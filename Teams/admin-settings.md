---
title: Admin settings for apps in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: lolaj
ms.date: 01/29/2018 
ms.topic: article
ms.service: msteams
ms.reviewer: ritikag 
description: Learn to allow and enable apps in Microsoft Teams including side-loading of external apps.
ms.custom:
- NewAdminCenter_Update
MS.collection: Strat_MT_TeamsAdmin 
appliesto: 
- Microsoft Teams
- 
---

Admin settings for apps in Microsoft Teams
==========================================

Apps are tabs, connectors, bots, or any combination of these three, provided by a third-party service. There are Teams admin policies that can be configured in the Office 365 admin center to control which external third-party apps are allowed. These policies let you specify which apps are allowed and disallowed, new external App behavior, and whether side-loading apps is allowed.

> [!NOTE]
> To manage admin settings for apps in Teams, go to the Office 365 admin center and open **Settings** > **Services & add-ins**, then choose **Microsoft Teams**. If you're signed in as an Office 365 admin, this link should take you there:
> 
> https://portal.office.com/adminportal/home#/Settings/ServicesAndAddIns 

## Allow external apps in Teams

By default, **Allow external apps in Microsoft Teams** is turned on, with all apps selected.  If you turn off this switch, all external third-party apps are disabled. 

## Enable new external apps by default

#### :trophy: Best practice: Manage external apps individually 
 
To turn on some apps (and turn off others), turn off **Allow sideloading of external apps**. Then turn off any apps you don't want your users to use. Optional: Turn off **Enable new external apps by default** (if you want to control new apps). 

When this switch is turned on, users can activate new apps as soon as they're added to the Teams app catalog. To open the Teams app catalog, click **Store** at the bottom of Teams, then click **Apps**. If you want to control which apps are available, turn this switch off. Of course, if you turn it off, you have to remember to review new apps periodically so your organization doesn't miss out on cool new apps. 

Sideloading is how you add an app to Teams by uploading a zip file directly to a team. Sideloading lets you test an app as it's being developed. It also lets you build an app for internal use only and share it with your team without submitting it to the Teams app catalog in the Office Store. 

Only team owners, or members who are granted permissions, can sideload apps into Teams.  

![Screenshot of the Apps section of Microsoft Teams settings.](media/Admin_settings_for_apps_in_Microsoft_Teams_image1.png) 

## Creating and uploading app packages 

To learn more about apps, read [Develop apps for Teams](https://docs.microsoft.com/microsoftteams/platform/concepts/apps/apps-overview). 



