---
title: "Phones for Microsoft Teams"
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: kponnus
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-voice
search.appverid: MET150
localization_priority: Normal
description: "This article covers the list of phones that are certified for Microsoft Teams and the features supported in the phones certified for Microsoft Teams."
---

# Phones for Microsoft Teams

Microsoft Teams supports a portfolio of desk phones for users who require a traditional phone experience. This article provides a complete overview of Teams phones and can help in planning, delivering, and managing Microsoft Teams phones as part of your Microsoft Phone System solution. 

To deliver a high-quality and reliable Microsoft Teams experience on phones, we are partnering and actively working with Yealink, Crestron, Lenovo, Polycom, and Audiocodes to develop and certify a wide portfolio of desk phones and conference room audio devices. To get the latest and up-to-date information on Teams devices, go to [Teams Marketplace](https://office.com/teamsdevices).

To manage phones, you need to be a Global admin, Teams Service admin, or Teams Device admin. For more information about admin roles, see [Use Microsoft Teams administrator roles to manage Teams](../using-admin-roles.md).

## Features supported by Teams Phones
Teams-certified phones have a broad array of features to help your users do their jobs, and help you manage their use. Here's a summary of the features available in Teams-certified phones:

- **Authentication** Phones use Modern Authentication to simplify signing in and to improve security. Users can sign in by entering their username and password on the phone or by signing in from another device like PC/smartphone.
- **Speed dial and call history** Users have quick access to their contacts, call history, and voicemail. They can easily manage their contacts and speed dial entries directly from their phone.
- **Meetings and calls** Users can view their schedules and easily join meetings using Teams' one-touch join.
- **Call groups** Phone agents who participate in call groups can easily manage their availability and accept or decline incoming calls from the call queue.
- **User delegation** Executive assistants and admins can manage their executives' phones - intercept incoming calls; make calls on behalf of the executive; take over calls that the executive has placed on hold; and monitor whether the executive is on a call, on hold, and so on.
- **Hot desking** Users can get their contacts, meetings, and other preferences, just by signing into a phone. When they're done, they can sign out and leave the phone ready for the next user.
- **Video** Phones with video support let users join calls and video conferences just like they were at their computers. Users can keep their privacy by using a phone's camera shutter and microphone mute switch when available.
- **Better together** Phones can lock and unlock in an integrated fashion when connected to their Windows PC running a 64-bit Teams desktop client.
- **Accessibility** Phones have several accessibility features, such as high contrast text, to make it easier for anyone to use them.
- **Dynamic and enhanced E911 support** Signed-in users who call 911 will see their location on the phone. 
    > [!IMPORTANT]
    > If a phone isn't signed in, or if it doesn't have an Internet connection, 911 calls can't be placed. If this happens, a notification is displayed on the phone.

In addition to the above features, you can control what capabilities are available depending on the type of license and phone policy that are assigned to the user signing into the phone. For example, users who sign into a phone with their personal accounts can access the full range of features - calling, meetings, voicemail, and so on. Accounts assigned a Common Area Phone license that sign into a phone, however, may only get access to a limited range of features; call history and meeting schedules may not be retained, for example, to protect users' privacy.

## Required Licenses

Microsoft Teams licenses can be purchased as part of their [Microsoft 365 and Office 365 subscriptions](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description). To learn more about the required licenses for using Microsoft Teams on phones, see available [phone system licenses](https://products.office.com/microsoft-teams/voice-calling).

For more information about getting Teams, check out [How do I get access to Microsoft Teams?](https://support.office.com/article/fc7f1634-abd3-4f26-a597-9df16e4ca65b)

## Deploy your phones via Intune

### Conditional Access

Conditional Access is an Azure Active Directory feature that helps you to ensure devices accessing your Office 365 resources are properly managed and are secure.  If you apply Conditional Access policies to the Teams service, then Android devices (including a Teams phone) that access Teams need to be enrolled into Intune and their settings need to comply with your policies.  If the device isn't enrolled into Intune, or if it's enrolled but its settings don't comply with your policies, Conditional Access will prevent a user from signing into or using the Teams app on the device.

Typically, compliance policies defined within Intune are assigned to groups of users.  This means that if you assign an Android compliance policy to user@contoso.com, that policy will apply equally to their Android smartphone and to any Android-based Teams device that user@contoso.com signs into.

If you use Conditional Access, which requires Intune enrollment to be enforced, in your organization, there are a couple things you need to set up to allow for a successful Intune enrollment:

- **Intune license** The user signing into the Microsoft Teams phone must be licensed for Intune.  As long as the Microsoft Teams phones are signed into a user account that has a valid Intune license, the phone will automatically be enrolled in Microsoft Intune as part of the sign-in process.
- **Configure Intune** You must have a properly configured Intune tenant set up for Android Device Administrator enrollment.

### Configure Intune to enroll Teams Android-based devices

Teams Android-based devices are managed by in Intune via Android Device Administrator (DA) management. Before devices can be enrolled into Intune, there are a few basic steps to perform.  If you are already managing devices with Intune today, you probably have already done all these things.  If not, here’s what to do:

1. Set Intune MDM (mobile device management) Authority.  If you’re never used Intune before, you need to set the MDM authority before you can enroll devices. For more information, see [Set the mobile device management authority](https://docs.microsoft.com/intune/fundamentals/mdm-authority-set).  This is a one-time step that has to be done upon creating a new Intune tenant.
2. Enable Android device administrator enrollment. Android-based Teams device are managed as device administrator devices with Intune.  Device administrator enrollment is off by default for newly created tenants.  For more information, see [Android device administrator enrollment](https://docs.microsoft.com/intune/enrollment/android-enroll-device-administrator).
3. Assign licenses to users. Users of Teams devices enrolling to Intune must be assigned a valid Intune license. For more information, see [Assign licenses to users so they can enroll devices in Intune](https://docs.microsoft.com/intune/fundamentals/licenses-assign).
4. Assign Device Administrator compliance policies.  Create an Android Device Administrator compliance policy and assign it to the Azure Active Directory group that contains the users that will be signing into the Teams devices. For more information, see [Use compliance policies to set rules for devices you manage with Intune](https://docs.microsoft.com/mem/intune/protect/device-compliance-get-started).

## Manage your phones

A tenant admin can manage and keep all their Teams devices up-to-date via the Teams Admin Center. For more information, see [Manage your devices in Microsoft Teams](https://docs.microsoft.com/microsoftteams/devices/device-management). 

## See also

[Teams Marketplace](https://office.com/teamsdevices)

[IP Phones certified for Microsoft Teams](teams-ip-phones.md)
