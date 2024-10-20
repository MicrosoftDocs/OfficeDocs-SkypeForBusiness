---
title: Deploy Teams phones using Conditional Access and Intune
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.date: 04/25/2024
ms.reviewer: prashibadkur
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords: 
  - NOCSH
ms.collection: 
  - teams-rooms-devices
  - M365-voice
  - Teams_ITAdmin_Devices
  - Tier1
search.appverid: MET150
ms.localizationpriority: medium
description: This article provides an overview of and features supported by Microsoft Teams phones.
---

# Intune and Conditional Access for Teams phones

This article gives you an overview of how to deploy configure Intune and Conditional Access to support Teams phones.

## Configure Intune to allow enrollment Teams phones

Customers must enroll their Teams phone devices using Android Device Administrator. Before devices can be enrolled into Intune successfully, there are a few basic steps to perform. If you're already managing devices with Intune today, you probably have already done all these things. If not, here's what to do:

1. Ensure Intune is set as the MDM (mobile device management) authority.  

  If you've never used Intune before, you need to set the MDM authority before you can enroll devices. For more information, see [Set the mobile device management authority](/mem/intune/fundamentals/mdm-authority-set). This is a one-time step that has to be done upon creating a new Intune tenant.
1. Enable Android device administrator.
  
   Teams phones are Android-based and without Google Mobile Services (GMS) and therefore are managed in Intune with Android Device Administrator (ADA). Device Administrator enrollment is off by default for newly created tenants. See [Android device administrator enrollment](/mem/intune/enrollment/android-enroll-device-administrator) for steps on how to enable Android Device Administrator in your environment.
  > [!NOTE]
  > Intune enrollment for Teams phones will switch to Android Open Source Project (AOSP) Device Management in 2025.

1. Assign Device Administrator compliance policies.  

  Android Device Administrator offers Intune compliance policies which can be used to ensure Teams phones are compliant with various organization security policies. Create an Android Device Administrator compliance policy and assign it to your Teams phone resource accounts, see [use compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started).

> [!NOTE]
> - If the user account used to sign into a Teams device isn't licensed for Intune, Intune compliance policies and enrollment restrictions need to be disabled for the account.
> - If the user account used to sign into a Teams device is licensed for Intune, the Teams device will automatically enroll in Intune.

## Conditional Access

Conditional Access is a Microsoft Entra ID feature that helps to ensure devices accessing your Microsoft 365 resources are properly managed and secure. For Teams phones, we recommend using Conditional Access to secure Teams phone resource accounts since resource accounts do not support user interactive multi-factor authentication (MFA). Conditional Access can be used to enforce a different secondary factor, such as known network location or compliant device to match organization security policies. If you apply a Conditional Access policy requiring Teams phones to be Intune compliance, the Teams phone must be enrolled into Intune with a compliance policy configured. If the device isn't enrolled into Intune, or if its enrolled, but its settings don't comply with your policies, Conditional Access prevents that Teams phone from signing in successfully.

Typically, compliance policies defined within Intune are assigned to groups of users. This means that if you assign an Android compliance policy to user@contoso.com, that policy applies equally to their Android smartphone and to any Android-based Teams device that user@contoso.com signs into. For more information, review [Teams phone authentication best practices](authentication-best-practices-phones.md).

If you use Conditional Access, which requires Intune enrollment to be enforced, in your organization, there are a couple things you need to set up to allow for a successful Intune enrollment:

- **Intune license** The user signing into the Teams phone must be licensed for Intune. As long as the Teams device is signed in to a user account that has a valid Intune license, the device is automatically enrolled in Microsoft Intune as part of the sign in process.
- **Configure Intune** You must have a properly configured Intune tenant set up for Android Device Administrator enrollment.

## See also

[Phones for Teams](phones-for-teams.md)

[Certified Teams phones](../devices/teams-phones-certified-hardware.md)

[Teams Marketplace](https://office.com/teamsdevices)
