---
title: Sign out of Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
audience: Admin
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: 
ms.date: 07/20/2021
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

We recommend that users remain signed in to Microsoft Teams to continue receiving chats, incoming calls, and other notifications.  

The new Teams desktop app supports multiple accounts side-by-side, removing the need to sign out and sign back in. [Learn more about New Teams.](/microsoftteams/new-teams-desktop-admin)
We understand that, in some cases, users might need to sign out of Teams, for example when they’re using a device that is shared with another person.  
Except for [Shared Device Mode for mobile devices](#shared-device), signing out of Teams should always be initiated by end-users, from inside the Teams app. Microsoft recommends against using custom scripts that attempt to programmatically sign out users.

## Sign out of Teams on the web

To sign out of Teams in a browser, select your profile picture at the top of the app, then select  **Sign Out**. You'll be signed out from all Microsoft 365 applications in that browser profile. The next time you sign in to Teams or other Microsoft 365 applications, your username will be shown on the sign-in page. In most cases, you have to reenter your credentials, and you can remove your account from the list by clicking “Forget”.  

If this is a shared computer and you don’t want your username to be visible to other users, we recommend using InPrivate/Incognito mode in your browser.

## Sign out of Teams on desktop (Windows or MacOS)

To sign out of the Teams desktop app, select your profile picture at the top of the app, and then select  **Sign Out**. If you have multiple accounts added, you'll need to sign out of each account individually.

### Account sharing between apps

Modern operating systems allow sharing of accounts between different apps on a device. This is referred to as single sign-on (SSO), and it’s designed to help you seamlessly navigate between different apps with the same account.  
SSO has an important impact on sign out: when you sign out of the Teams desktop app, the data associated with your account is removed from the Teams app but your account isn’t removed from the device. You have to reenter the credentials if you choose to sign back in to Teams with the same account, but other apps on the device may continue to have access to your account. This means that signing in to Teams does not prevent other users from accessing the data associated with your account.

### “This app only” mode on Windows

On Windows, users may see an option to sign in to “this app only”. When this option is selected, and you later sign out of Teams, your account is removed from the PC. However, your user name may continue to be shown on sign-in pages.

![Screenshot: User interface of sign in to all apps with a link to only sign into this app only.](media/sign-in-to-all-apps.png)

**Note:** when you select “this app only” when signing in to Teams, other apps on your PCs won’t be able to use this account. Practically, this means that links to files or websites you click in Teams may not properly open in Microsoft 365 or in Edge, or you may be prompted to sign in again. In other words, “this app only” prevents SSO from working correctly between Windows, Teams and other applications on your PC, and as such it’s not recommended when signing in to Teams.

### Best practices for multiple users on a shared desktop device

If you’re sharing the desktop computer with other people, we recommend setting up separate accounts on Windows or MacOS. This allows you to enjoy SSO between apps in a given operating system session, and conveniently lock the device when you walk away. 

In cases where a single desktop computer is shared between multiple frontline workers, we recommend using Cloud PCs, as described here: [Frontline worker for Windows devices in Microsoft Intune](/mem/solutions/frontline-worker/frontline-worker-overview-windows)

## Sign out of Teams on mobile devices

On mobile, you can sign out of Teams by tapping your profile icon, selecting **Settings**, and then **Sign out**. Once signed out, you'll need to reenter their credentials the next time you launch the app.

## <a id="shared-device" />Shared Device Mode: Global sign-in and sign-out for Frontline workers

Microsoft’s Shared Device Mode (SDM) allows mobile devices to be optimized for fast check-in/check-out by frontline workers. When a device is enabled for SDM, sign-out work differently on Teams.

With SDM, you can pick any device from the shared device pool and sign in as usual to "make the device yours" for the duration of your shift. At the end of your shift, you should tap on Sign out, and sign-out will behave differently. A global sign-out will be initiated on the device, which should remove your work account and data from the device so it can be returned to the device pool.

**Android**: To learn how to set up android devices in shared mode, see [How to use a shared device mode in Android](/azure/active-directory/develop/tutorial-v2-shared-device-mode#set-up-an-android-device-in-shared-mode).

**iOS**: Shared device mode support on iOS is in public preview. To set a device in shared mode on iOS, see [How to use shared device mode on iOS](/azure/active-directory/develop/msal-ios-shared-devices).

> [!NOTE]
> This feature is in public preview.

![Sign-out-section](media/signout.png)
