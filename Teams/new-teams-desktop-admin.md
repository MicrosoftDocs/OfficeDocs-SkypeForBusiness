---
title:  The new Microsoft Teams desktop client
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
ms.topic: article
ms.date: 09/01/2023
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
- m365initiative-deployteams
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the new Microsoft Teams desktop client for Windows. Try out new features and provide feedback.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---

# The new Microsoft Teams desktop client 

> [!TIP]
>Ready to deploy the new Teams? Step by step instructions are here: [**Deploy the new Teams using policies**.](/microsoftteams/new-teams-deploy-using-policies?tabs=teams-admin-center#set-the-policies-to-deploy-the-new-teams-client)
>
>Looking for tips on using the new Teams? See [**Try the new Microsoft Teams**](/office/try-the-new-microsoft-teams-2d4a0c96-fa52-43f8-a006-4bfbc62cf6c5).
>
>Visit our **[new Teams microsite](https://aka.ms/newTeams)** to learn more and see a more detailed list of upcoming features.

## What is the new Teams?

The new Teams desktop client for Windows has been reimagined from the ground up with performance in mind, providing a faster, simpler, and more flexible experience. The new Teams client installs and loads faster, letting you launch the app and join meetings more quickly, giving you more time to focus on the business tasks. 

The new Teams ensures more efficient use of device resources. You can lower memory and disk usage with a Teams app optimized for your device. Whether you have users on multiple accounts or tenants, the new Teams can help eliminate the silos and bring them together in one place, giving them more extensibility and scale.

>[!Note]
>Ready to deploy?  Follow these step by step instructions: [**Deploy the new Teams using policies**](/microsoftteams/new-teams-deploy-using-policies?tabs=teams-admin-center#set-the-policies-to-deploy-the-new-teams-client)

## Is the new Teams available for my organization?

The new Teams client **is not** yet available for the following customers but is planned for release later in this calendar year:

**Platforms:**  Mac, VDI, Web</br>
**Customer segments:**  </br>- Government clouds: GCC, GCC High, DoD</br>- Special cloud: Air-gapped, Microsoft 365 operated by 21Vianet in China </br>- Consumer</br>- Desktop running a Windows 10 version earlier than 10.0.19041


## New Teams rollout schedule for Windows clients

>[!Note]
>*This rollout schedule is only for **Windows clients**. We will be updating this schedule as other platform support, such as Mac, is available.
 
>[!Important]
>These schedules only apply if your organization has set the Teams Update policy "**Use new Teams Client**" to either:
>- **Microsoft controlled** (the value in the Teams Admin Center)  **or**
>- **Microsoft choice** (if you are using PowerShell) 
>
>[Learn more about Teams Admin policies](/microsoftteams/manage-teams-with-policies).

### When will all users see the "Try the new Teams" toggle?

##### Licenses

|License|Rollout begins|
|:-----|:-----|
|Business Licenses and Teams Essentials|Early August 2023|
|Enterprise and other Licenses|See the schedule listed in this article.|

##### Update channels

>[!Tip]
>Learn more about update channels, including how to make changes here:
> - [**Update channels for Microsoft 365 apps**](/deployoffice/updates/overview-update-channels)

If the update channel isn't listed, then the Monthly Enterprise Channel schedule is followed.

|Update channel|Date|
|:-----|:-----|
Public preview program|Available|
|Targeted release program|Available|
|Current Channel|August 2023|
|Monthly Enterprise Channel|Mid September 2023|
|Semi-Annual Enterprise Channel (Preview)|August 2023|
|Semi-Annual Enterprise Channel, Semi-annual Extended, LTSC and remaining channels|Early November 2023|

>[!Note]
>- Teams for Government includes GCC, GCCH, DoD and other special clouds follow the schedule for the Semi-Annual channels
>- New Teams is not currently available on VDI and Mac OS but is planned for release later in this calendar year

### When will the new Teams become the default client?

Existing Teams users are updated to the new Teams based on two factors:</br>
- Which Microsoft 365/Teams license is assigned to the user; and 
- The [**Microsoft 365 app update channel**](/deployoffice/updates/overview-update-channels) you're using. 

Users are switched once to the new Teams. Afterward, users can switch back to classic Teams if they wish.

##### Licenses

|License|Date|
|:-----|:-----|
|Business Licenses and Teams Essentials|Mid September 2023
|Enterprise and other Licenses|See the schedule listed in this article.|

##### Update channels

If the update channel isn't listed, then the Monthly Enterprise Channel schedule is followed.

>[!Tip]
>Learn more about update channels, including how to make changes here: [**Update channels for Microsoft 365 apps**](/deployoffice/updates/overview-update-channels).

|Update channel|Date|
|:-----|:-----|
|Teams Public Preview|Mid August 2023|
|Targeted Release Channel|Mid August 2023|
|Current Channel|Early October 2023|
|Monthly Enterprise Channel|Early November 2023|
|Semi-Annual Enterprise Channel (Preview)|Early October 2023|
|Semi-Annual Enterprise Channel, Semi-annual Extended, LTSC, and remaining channels|Mid January 2024|

>[!Note]
>- Teams for Government includes GCC, GCCH, DoD and other special clouds will follow the schedule for the Semi-Annual channels.
>- New Teams is not currently available on VDI and Mac OS but is planned for release later in this calendar year.

## What features are still missing?

Most of the features you're familiar with in classic Teams are already in new Teams, however a few are still being worked on. </br>

[**Follow Microsoft Adoption for the latest information on upcoming features for the new Teams.**](https://aka.ms/newTeams).

## What features are changing?

As we improve the client, the experience has been improved to align with similar features. Here are some of the changes you see.

|Classic Teams|New Teams|
|:-----|:-----|
|Purple toast notifications|You'll no longer see the purple "toast" notifications, and the taskbar icon will behave a little different. Notifications are via Windows native notifications to provide a consistent experience.|
|Adding a Wiki to a channel tab|You'll no longer see a Wiki app. Instead, select the Notes app.|
|Adding third party cloud storage service from Files app and Files tab in channels|You'll no longer see the "Add cloud storage" in the Files app on Teams' left navigation bar and within the Files tab in Teams channels. Now you can add the third party storage app directly from the Teams App Store.|
|Look up an organizational chart while in a 1:1 chat |Select a user’s avatar or profile photo anywhere in Teams and navigate to the organizational chart within the profile card.|
|Look up LinkedIn while in a 1:1 chat | Select a user’s avatar or profile photo anywhere in Teams and navigate to the LinkedIn tab within the profile card.|
|Adding a document library (DocLib) app to a tab in channels|Use the Sharepoint app instead. Then add the document library from there as a tab to the channel. Existing document libraries will automatically convert to a SharePoint document library on first use.|
|Activity tab in chat| No longer available.|
|Ability to save messages and files in Teams|No longer available. Will be replaced later this year by a similar feature.|
|Allow users to follow another user's presence, then notify them of availability|Select a user’s avatar or profile photo anywhere in new Teams to quickly get an overview of their online status, next available calendar slot in Outlook, work hours, local time, and work location (remote or office).|
|Ability to sign out from the notification area at the far right of the taskbar (system tray). |No longer available.|
|Settings dialog|Settings is now an app accessed from the More options menu **(...)** in the title bar. |
|About links in the More options menu (...) |About links are now in the Settings app under the **About Teams** category.|
|Help in the app bar|The Help entrypoint, including Help links and Give Feedback is now located under the More options menu **(...)** in the title bar.|
|Ability to build Teams personal apps usings Adaptive cards|No longer available.|
|General appearance changes|Colors, tooltip styles, and general appearance have been updated.|
|Ability to use tags in the "Add member" dialog.|There's now an advanced flow for tags.|
|Organization chart is a tab in chat|The organization chart is now located in the live persona card (LPC).|
