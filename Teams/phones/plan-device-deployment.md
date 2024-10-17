---
title: Plan your deployment for Teams Phones
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 08/02/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
description: This article provides an overview of the tasks and steps to deploy Teams phones in your organization.
---

# Plan your deployment for Teams Phones

Teams phones are a great way to stay connected and productive with your colleagues and customers. These devices are designed to provide a seamless calling and meeting experience. With just three easy steps, you can deploy a [Teams Phone device certified by Microsoft](https://www.microsoft.com/en-us/microsoft-teams/across-devices/devices/category/desk-phones-teams-displays/34?page=1&filterIds=), in your spaces and enjoy advanced calling features.

## Step 1: Consider the space Teams Phone device will be used in

- **Personal Space**: Used on an employee’s desk to make and receive calls.
- **Shared Space**: Used in a shared space, such as a lobby, a building floor, or anywhere your employees and visitors need quick access to make call.

The space you choose will determine the type of license you'll need.

## Step 2: Pick the licenses and workloads you'll need for the space 

|License  |Calls |People  |Voicemail  |	Walkie Talkie|Calendar|
|---------|---------|---------|---------|-------|------|
|Teams Phone license     | Yes        |Yes         |Yes         |Yes|Yes|
|Teams Shared Device license    | 	Yes   |  	Yes    | 	Yes    |Yes|No|
|Teams Rooms Pro license     |Yes         |  Yes       |  No       |No|Yes|

### Licenses

- **Teams Phone license**: If the phone device is used at a user’s desk, you can use the same Teams Phone License used on Teams desktop or Teams mobile app allowing you to make and receive calls and join meetings on the phone device. Teams subscriptions with Teams Phone license enable calling between Teams on mobile, desktop, and phone device. With Microsoft Calling plans add-on license, you can make and receive calls to and from a phone number over PSTN network.

- **Teams Shared Device license**: If you're using the phone device in a shared space, such as a lobby or a building floor, you'll need a Shared Device license that allows users to use the device for calling purposes. Shared Device license comes included with a Teams Phone license enabling use of advanced calling features such as call queue, auto attendant, etc.

- **Teams Rooms Pro license**: If you're using the audio-conferencing device in a small meeting room, you'll need a Teams Rooms Pro license that allows you to join audio meetings with one touch.

### Workloads:

- **Calls**: Manage calls, search the directory, and use speed dial for quick calling. Users can also use advanced calling features, such as call queue and auto attendant.
- **People**: Add and manage contacts and contact groups.
- **Voicemail**: View voicemail history and associated actions.
- **Walkie Talkie**: Users part of a Teams channel can broadcast messages to other users' part of the same channel.
- **Calendar**: Schedule and join meetings.

  :::image type="content" source="media/teams-apps-1" alt-text="Screenshot of teams app." lightbox="media/teams-apps-1.png":::

## Step 3: Setup desired phone device experience for your users

First, configure IP Phone Policy [SignInMode](/powershell/module/teams/new-csteamsipphonepolicy#-signinmode) parameter via PowerShell to enable associated apps on phone device.

- With **UserSignIn** mode, get Calls, People, Voicemail, Walkie Talkie, and Calendar apps when Personal License is assigned to the account.

- With **CommonAreaPhoneSignIn** mode, get Calls app when Shared Device License is assigned to the account. Additionally, you can enable '[Advanced Calling](../set-up-common-area-phones.md#step-6---set-up-advanced-calling-on-common-area-phones-optional)' setting on phone device or Teams Admin Center to get People, Walkie Talkie, and Voicemail apps.

- With **MeetingSignIn** mode, get Calendar app with meeting join experience when Teams Rooms Pro license is assigned to the account.

  :::image type="content" source="media/sign-in-teams.png" alt-text="Screenshot to sign into teams." lightbox="media/sign-in-teams.png":::

Then, choose from the following home screen experiences you want to enable for your users. On touch and non-touch phones, you can choose to enable one of the following experiences:

- **Basic Calling Experience**: On an account signed in with CommonAreaPhoneSignIn mode, you can offer a basic Dialpad and Speed Dial view by disabling the '[Advanced Calling](../set-up-common-area-phones.md#step-6---set-up-advanced-calling-on-common-area-phones-optional)' setting.

- **Advanced Calling Experience**: On an account signed in with CommonAreaPhoneSignIn mode, you can offer a home screen experience with Calls, People, and Voicemail apps by enabling '[Advanced Calling](../set-up-common-area-phones.md#step-6---set-up-advanced-calling-on-common-area-phones-optional)' setting.

- **Hotline Experience**: On an account signed in with CommonAreaPhoneSignIn mode and assigned with Shared Device license, you can enable '[Hotline](../set-up-common-area-phones.md#step-7---set-up-hotlineplar-on-common-area-phones-optional)' setting to offer a PLAR (Private line auto ringdown) experience.

In addition to the above, you can choose from the following experiences on touch phones.

- **Calls App Experience**: On an account signed in with UserSignIn mode or CommonAreaSignIn mode (with Advanced Calling enabled), you can set the Calls app to be your default home screen by disabling [Homescreen](/powershell/module/teams/new-csteamsipphonepolicy#-allowhomescreen).

- **Meeting Experience**: An account signed in with MeetingSignIn mode will get meeting join experience.

## Best Practices:

- **Manage firmware and Teams app updates**: Enable [auto updates](../devices/remote-update.md#automatic-updates) of firmware via Teams admin center and assign devices to different rings (Validation, General, Final) to roll out updates in phases. You can assign the Validation ring to a small set of test phones and assign other phones to General and Final rings. 

  > [!NOTE]
  > Auto updates on Teams application is coming soon. Currently, you can [schedule](../devices/remote-update.md#manually-update-remote-devices) Teams application update via Teams admin center.

- **Manage Authentication**: For password management, review [Authentication best practices](../devices/authentication-best-practices-for-android-devices.md).

- **Configure calling policies**: Configure different [calling policies](../teams-calling-policy.md) based on your needs.

- **Optimize phone memory usage**: To optimize phone performance, enable daily or automatic restart of Teams application on the phone device via [configuration profile](../devices/device-management.md#use-configuration-profiles-in-teams).

- **Secure common area phones**: To provide secured access to settings on phone devices in shared spaces, set an Admin PIN on common area phones via [configuration profile](../devices/device-management.md#use-configuration-profiles-in-teams).

- **Secure personal phones**: Ask your users who use phones in personal spaces to set a phone device lock PIN for secured access instead of setting a default phone device lock PIN via configuration profile.
