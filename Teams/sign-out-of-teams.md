---
title: Sign out of Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: sbhatta
description: Learn how to sign out of Microsoft Teams.
ms.custom: seo-marvel-apr2020
ms.localizationpriority: high
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# Sign out of Microsoft Teams

We recommend for users to remain signed in to the Microsoft Teams app to continue receiving chats, incoming calls, and other activities. We understand that, at times, users might want to sign out of the Teams application for several reasons:

- Because they're done using Teams for the day
- They want to use a different account
- Because they're on a device that they share with another person

For these reasons and others, Teams allows you to sign out of the app and end your session.

## Account sharing between apps

Modern operating systems allow sharing of accounts between different apps on a device. This single sign-on (SSO) design allows users to use multiple apps on their device without requiring them to sign in to every single app. Teams doesn't control this behavior, but it does take advantage of the convenience this design provides for the end-user experience.

SSO has an important impact on sign out. When users sign out of Teams, the data associated with their account is removed from the Teams app, but other apps on the device could continue to have access to their account. It also means that users might not be prompted to reenter their credentials if they choose to sign back in to Teams with the same account.

## Sign out of Teams on desktop

To sign out of the Teams desktop client or from the browser, select your profile picture at the top of the app, and then select **Sign out**.

For the desktop app, you can also right-click the app icon in the taskbar, and then select **Sign out**.

If you have multiple accounts added, you'll need to sign out of each individual account. Once you've signed out of the accounts in Teams, you might need to enter your credentials again on the next launch of the app to access your account.

## Sign out of Teams on mobile devices

On mobile, you can sign out of Teams by going to the menu, selecting the **More** menu, and then selecting **Sign out**. Once signed out, you'll need to reenter their credentials the next time you launch the app.

### Global sign-in and sign-out for Frontline workers

The Teams Android app now supports Global sign-in and sign-out, to provide a hassle free sign-in and sign-out experience for Frontline Workers. Employees can pick a device from the shared device pool and do a single sign-in to "make it theirs" for the duration of their shift. At the end of their shift, they should be able to perform sign out to globally sign out on the device. This will remove all of their personal and company information from the device so they can return the device to the device pool. To get this capability, the device must be in shared mode.  Make sure to end any active meeting or call on the device before signing out. To learn how to set up a shared device, see [How to use a shared device mode in Android](/azure/active-directory/develop/tutorial-v2-shared-device-mode#set-up-an-android-device-in-shared-mode).

## Manual Cleanup

While rare, it's possible that Teams might not be able to clean up after itself fully on sign-out. Based on user reports, the common causes include files being locked by a service running on the system but there could be other reasons dependent on an individual's device configurations or policies and user permissions applied to the device.

One common manifestation of this problem is that Teams will try to automatically select an existing account to sign the user in. In situations like this, the user might want to manually clean up Teams' local cache. Learn more at [Sign in or remove an account from Teams](https://support.microsoft.com/office/sign-out-or-remove-an-account-from-teams-a6d76e69-e1dd-4bc4-8e5f-04ba48384487?ui=en-US&rs=en-US&ad=US).

## Related topics

[Sign in or remove an account from Teams](https://support.microsoft.com/office/sign-out-or-remove-an-account-from-teams-a6d76e69-e1dd-4bc4-8e5f-04ba48384487?ui=en-US&rs=en-US&ad=US)
