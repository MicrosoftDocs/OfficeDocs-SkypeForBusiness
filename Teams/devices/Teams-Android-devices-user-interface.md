---
title: "Setting Microsoft Teams Android devices user interface"
ms.author: mitressl
author: flinchbot
manager: leopaiv
audience: ITPro
appliesto: 
  - Microsoft Teams
ms.reviewer: 
ms.topic: article
ms.service: msteams
localization_priority: Normal
ms.collection:
  - M365-collaboration
description: Learn how to set the user interface on Teams Android devices.
---
# Setting Microsoft Teams Android devices user interface

Microsoft Teams Android devices have the ability to display a specific user interface, based upon the type of license assigned to the signed in account. You can override this behavior and control which interface is shown. This article details how the default user interface is chosen and how you can change the interface using a Powershell policy.

There are three types of user interfaces on Teams Android devices:

1. User
2. Common Area
3. Meeting

If you [assign a user license](/microsoftteams/user-access) to an account, such as an E3 or an E5 license, the Teams device will display the default end-user interface which is fully featured for most user scenarios. However, if a device is performing a specific function such as a common area phone or a meeting room, there are specific user interfaces for these usages.

Below are three images showing how the user interface changes based on the license assigned to the user account. In the first image, the user account is assigned an E5 license. As this is a user license, the device shows the default end user interface intended.

:::image type="content" source="../media/TeamsAndroidDevices-UserMode1.jpg" alt-text="User mode interface":::

In the following image, the user account has been assigned a [common area phone license](/microsoftteams/set-up-common-area-phones). Common area phones are primarily used for making and receiving phone calls. As such, the dial pad is shown on the display.

:::image type="content" source="../media/TeamsAndroidDevices-CAP1.jpg" alt-text="Common area phone interface":::

Finally, the following image shows a user account with a [Microsoft Teams Rooms Standard license](/MicrosoftTeams/rooms/rooms-licensing) assigned. Teams Rooms licenses are meant to be used in meeting rooms or shared spaces. As such, the user interface changes to make it easy to join a meeting by showing the calendar view.

:::image type="content" source="../media/TeamsAndroidDevices-Meeting.jpg" alt-text="Meeting interface":::

> [!NOTE]
> Just because the user interface changes does not mean that you cannot use other licensed features. For example, even though the meeting view defaults to showing the calendar, you can still make and receive Public Switch Telephone Network (PSTN) phone calls if the account is correctly licensed and configured.

> [!IMPORTANT]
> There are other elements of the interface that change. For example, it is not desirable to have end users sign out of a common area phone or a meeting room device. As such, the "Sign out" option on common area phones and meeting room devices is moved to a part of the settings menu that requires administrator permissions to access.

## Override automatic user interface detection

In some cases, you may choose to assign a license to an account that does not match its intended use. For example, you may assign a user license to an account meant to sign in to Teams Rooms on Android. By default, you would receive the end-user interface instead of the meeting room interface. You can override the default interface by creating a new [Teams IP Phone Policy](/powershell/module/skype/new-csteamsipphonepolicy?view=skype-ps) and applying to it to that account.

> [!NOTE]
> The license assigned to the user account must have at least the same license entitlements as the desired user interface. The Common Area Phone license only allows the Common Area phone user interface. The meeting  room license allows meeting room and common area phone user interfaces. An E3 or E5 license supports all sign-in modes.

The following is an example of how to override automatic license detection. In this example, assume that a meeting room resource account named conf-adams@contoso.com has been assigned an E3 license. You want to make sure that the meeting room user interface is seen after this account signs in.

### Create a new policy and assign to user

1. Start a remote Windows PowerShell session and connect to Microsoft Teams as follows:

    ``` Powershell
    Connect-MicrosoftTeams
    ```

2. After establishing a session, you'll need to create a new Teams IP Phone policy and set the sign in mode to "MeetingSignIn":

   ``` Powershell
   New-CsTeamsIPPhonePolicy –Identity 'Meeting Sign in' –Description 'Meeting Sign In Phone Policy' -SignInMode 'MeetingSignIn'

   ```

3. You can now assign this new policy to the meeting room resource account:

   ``` Powershell
   Grant-CsTeamsIPPhonePolicy –Identity 'conf-adams@contoso.com' –PolicyName 'Meeting Sign In'
   ```

After granting the policy to the meeting room resource account, you will need to wait for the policy assignment to replicate. You will also need to sign out of the device and sign back in.
