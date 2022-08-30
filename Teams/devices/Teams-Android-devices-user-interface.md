---
title: Set Microsoft Teams Android devices user interface
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
appliesto: 
  - Microsoft Teams
ms.reviewer: 
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
description: Learn how to set the user interface on Teams Android devices.
---
# Set Microsoft Teams Android devices user interface

Microsoft Teams Android devices can display a specific user interface based on the type of license assigned to the signed-in account. You can override this behavior and control which interface is shown. This article details how the default user interface is chosen and how you can change the interface using a Powershell policy.

There are three types of user interfaces on Teams Android devices:

1. User
2. Common Area
3. Meeting

If you [assign a user license](/microsoftteams/user-access) to an account, like an E3 or an E5 license, the Teams device will display the default end-user interface which is fully featured for most user scenarios. However, if a device is performing a specific function, such as a common area phone or a meeting room, there are specific user interfaces for these usages.

The following three images show how the user interface changes based on the license assigned to the user account. 

## End-user interface 

The user account is assigned an E5 license. This is a user license, so the device shows the default end-user interface:

:::image type="content" source="../media/teams-android-devices-usermode1.jpg" alt-text="User mode interface.":::

## Common area interface

In this image, the user account has been assigned a [Common Area Phone license](/microsoftteams/set-up-common-area-phones). Common area phones are primarily used for making and receiving phone calls. As such, the dial pad is shown on the display:

:::image type="content" source="../media/teams-android-devices-cap1.jpg" alt-text="Common area phone interface.":::

## Meeting interface

This image shows a user account with a [Microsoft Teams Rooms license](/MicrosoftTeams/rooms/rooms-licensing) assigned. Teams Rooms licenses are meant to be used in meeting rooms or shared spaces, so the user interface changes to make it easy to join a meeting by showing the calendar view:

:::image type="content" source="../media/teams-android-devices-meeting.jpg" alt-text="Meeting interface.":::

> [!NOTE]
> Changing the user interface doesn't affect your ability to use other licensed features. For example, even though the Team Rooms license's default view is the calendar view, you can still make and receive Public Switch Telephone Network (PSTN) phone calls if the account is correctly licensed and configured.

> [!IMPORTANT]
> There are other elements of the interface that change. For example, to prevent end-users from signing out of a common area phone or meeting room device, the "Sign out" option on these devices is moved to a part of the settings menu that requires administrator permissions to access.

## Override automatic user interface detection

In some cases, you may choose to assign a license to an account that doesn't match its intended use. For example, you may assign a user license to an account meant to sign in to Teams Rooms on Android. By default, you would see the end-user interface instead of the meeting room interface. To override the default interface, create a new [Teams IP Phone Policy](/powershell/module/skype/new-csteamsipphonepolicy?view=skype-ps) and apply to it to that account.

> [!NOTE]
> The license assigned to the user account must have at least the same license entitlements as the desired user interface. The Common Area Phone license only allows the Common Area phone user interface. The meeting room license allows meeting room and common area phone user interfaces. An E3 or E5 license supports all sign-in modes.

The following is an example of how to override automatic license detection. In this example, assume that a meeting room resource account named conf-adams@contoso.com has been assigned an E3 license. When this account is signed-in, you want users to see the meeting room user interface.

### Create a new policy and assign to user

1. Start a remote Windows PowerShell session and connect to Microsoft Teams using the following cmdlet:

    ``` Powershell
    Connect-MicrosoftTeams
    ```

2. Create a new Teams IP Phone policy and set the sign-in mode to "MeetingSignIn":

   ``` Powershell
   New-CsTeamsIPPhonePolicy –Identity 'Meeting Sign in' –Description 'Meeting Sign In Phone Policy' -SignInMode 'MeetingSignIn'

   ```

3. You can now assign this new policy to the meeting room resource account:

   ``` Powershell
   Grant-CsTeamsIPPhonePolicy –Identity 'conf-adams@contoso.com' –PolicyName 'Meeting Sign In'
   ```

After granting the policy to the meeting room resource account, you'll need to wait for the policy assignment to replicate. You'll also need to sign out of the device and sign back in.

## Impact on Microsoft Teams admin center

Microsoft Teams admin center allows you to manage Microsoft Teams devices. For more information on managing devices using Teams admin center, see [Manage your devices in Microsoft Teams](device-management.md).


Teams admin center provides the ability to manage Teams phones. Phones are filtered into one of three tabs based on their function: user phones, common area phones, and conference phone. 

 :::image type="content" source="../media/teams-admin-center-phones-header.png" alt-text="Phones header in Teams admin center.":::

As with the user interface detection, Teams phones are categorized based on the license assigned to the account signing in to the phone. For example, if an account that is assigned a common area phone license signs in to a phone, then that phone will be shown in both the default **All phones** section as well as in the **Common area phones** section.

If you would like a phone to appear in a different section, you can either assign a different license to the phone, or create and assign a Teams IP Phone policy as [described above](#override-automatic-user-interface-detection).
