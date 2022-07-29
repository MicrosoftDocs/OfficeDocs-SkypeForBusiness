---
title: "Deploy Teams phones, Teams displays, Teams panels, and Microsoft Teams Rooms on Android using Intune"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: weizxue
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
  - NOCSH
ms.collection: 
  - M365-voice
search.appverid: MET150
ms.localizationpriority: medium
description: "This article provides an overview of and features supported by Microsoft Teams Android devices."
---

# Deploy Teams phones, Teams displays, Teams panels, and Microsoft Teams Rooms on Android using Intune

This article gives you an overview of how to deploy Teams phones, Teams displays, Teams panels, and Microsoft Teams Rooms on Android using Intune.

## Conditional Access

Conditional Access is an Azure Active Directory (Azure AD) feature that helps you to ensure devices accessing your Office 365 resources are properly managed and are secure.  If you apply Conditional Access policies to the Teams service, Android devices (including Teams phones, Teams displays, Teams panels, and Microsoft Teams Rooms on Android) that access Teams need to be enrolled into Intune and their settings need to comply with your policies.  If the device isn't enrolled into Intune, or if it's enrolled but its settings don't comply with your policies, Conditional Access will prevent a user from signing in to or using the Teams app on the device.

Typically, compliance policies defined within Intune are assigned to groups of users.  This means that if you assign an Android compliance policy to user@contoso.com, that policy will apply equally to their Android smartphone and to any Android-based Teams device that user@contoso.com signs into.

If you use Conditional Access, which requires Intune enrollment to be enforced, in your organization, there are a couple things you need to set up to allow for a successful Intune enrollment:

- **Intune license** The user signing into the Teams device must be licensed for Intune.  As long as the Teams device is signed in to a user account that has a valid Intune license, the device will automatically be enrolled in Microsoft Intune as part of the sign-in process.
- **Configure Intune** You must have a properly configured Intune tenant set up for Android Device Administrator enrollment.

## Configure Intune to enroll Teams Android-based devices

Teams Android-based devices are managed by Intune via Android Device Administrator (DA) management. Before devices can be enrolled into Intune, there are a few basic steps to perform.  If you are already managing devices with Intune today, you probably have already done all these things.  If not, here's what to do:

> [!NOTE]
> - If tenant admins want common area phones to be enrolled into Intune, they need to add an Intune license to the account and follow the steps for Intune enrollment.
> - If the user account used to sign into a Teams device isn't licensed for Intune,
> Intune compliance policies and enrollment restrictions need to be disabled for the account.
> - If the user account used to sign into a Teams device is licensed for Intune, 
> the Teams device will be automatically enrolled in Intune.



1. Set Intune MDM (mobile device management) Authority.  

   If you've never used Intune before, you need to set the MDM authority before you can enroll devices. For more information, see [Set the mobile device management authority](/intune/fundamentals/mdm-authority-set).  This is a one-time step that has to be done upon creating a new Intune tenant.
1. Enable Android device administrator enrollment.
  
   Android-based Teams devices are managed as device administrator devices with Intune.  Device administrator enrollment is off by default for newly created tenants. See [Android device administrator enrollment](/intune/enrollment/android-enroll-device-administrator).
1. Assign licenses to users. 
 
   Users of Teams devices enrolling to Intune must be assigned a valid Intune license. For more information, see [Assign licenses to users so they can enroll devices in Intune](/intune/fundamentals/licenses-assign).
1. Assign Device Administrator compliance policies.  

   1. Create an Android Device Administrator compliance policy.

   1. Assign it to the Azure Active Directory group that contains the users that will be signing into the Teams devices. See [Use compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started).

## See also

[Phones for Teams](phones-for-teams.md)

[IP Phones certified for Microsoft Teams](teams-ip-phones.md)

[Teams displays](teams-displays.md)

[Manage your devices in Teams](device-management.md)

[Teams Marketplace](https://office.com/teamsdevices)
