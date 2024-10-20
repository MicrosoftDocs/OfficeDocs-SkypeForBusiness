---
title: Authentication best practices for Microsoft Teams shared device management of Android devices.
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: dimehta
ms.date: 09/30/2024
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
search.appverid: MET150
f1.keywords: 
  - NOCSH
ms.localizationpriority: Medium
description: Best practices on shared android device management in Teams. This features Conditional Access, password policy, multifactor authentication advice and more.
---

# Authentication best practices for Teams Rooms on Android and Teams panels

The goals of devices used with Teams make different device management and security strategies necessary. For example, a personal business tablet used by a single sales person has a different set of needs from an on-call phone shared by many customer service people. Security administrators and operations teams must plan for the devices that are used in the organization. They must implement security measures best suited to each purpose. This article's recommendations make some of those decisions easier. Commonly, Teams Rooms on Android and Teams panel devices are deployed with resource accounts which should be configured specifically for their function. If, there are users in your organization using Teams Rooms on Android in a *personal mode*, specific security configurations must be made to ensure they can sign in to the device successfully.

>[!NOTE]
>Conditional Access requires a Microsoft Entra ID P1 or P2 subscription.

>[!NOTE]
>Policies for Android mobile devices may not apply to Teams Android devices.

## Challenges with using the same controls for personal accounts and Teams resource accounts

Shared Teams devices can't use the same requirements for enrollment and compliance that are used on personal accounts and devices. Applying personal device authentication requirements to shared devices cause sign in issues. Some challenges with personal account security on resource accounts are:

1.  **Devices are signed out due to passwords expiry.**

    If the accounts used on Teams devices have a password-expiration policy, when the password expires the Teams Room or panel device will sign out automatically. The accounts used with shared space devices don't have a specific user to update and restore them to a working state when their passwords expire. If your organization requires passwords to expire and reset occasionally, these accounts stop working on Teams devices until a Teams device administrator resets the password and manually signs the device back in. Teams resource accounts should be excluded from password expiration.

    If the account is a users personal account, when their password expires, they can easily sign the device back in again.

2.  **Devices fail to sign in due to conditional access policies requiring user interactive multi-factor authentication.**

    If the account used on a Teams device is subject to Conditional Access policies and the multifactor authentication (MFA) policy is enabled, a Teams resource account won't sign in successfully as it doesn't have a secondary device to approve the MFA request. Teams resource accounts should be secured using alternative second factor authentication such as known network or compliant device. Or if a conditional access policy is enabled to require reauthentication ever X days, the Teams Room on Android or Teams panel device will sign out and require an IT administrator to sign back in every X days.

    If the account is a users personal account, user interactive MFA can be required for Teams Rooms on Android or Teams panels as the user will have a second device they can approve the authentication request on.


## Best practices for the deployment of shared android devices with Teams

Microsoft recommends the following settings when deploying Teams devices in your organization.

### Use a Teams Rooms resource account and disable password expiration

Teams shared devices should use a [Teams Rooms resource account](/rooms/create-resource-account.md). You can either sync these accounts to Microsoft Entra ID from Active Directory or create them directly in Microsoft Entra ID. Any password expiration policies for users will also apply to accounts used on Teams shared devices, therefore, to avoid disruptions caused by password expiration policies, set the password expiration policy for shared devices to never expire.

### Use remote sign in

Tenant administrators can sign into Teams Rooms on Android and Teams panels remotely. Instead of sharing passwords with technicians to set up devices, Tenant administrators should use remote sign-in to issue verification codes. You can sign into these devices from the Teams admin center. For more information, see [Remote provisioning and sign in for Teams Android devices](/MicrosoftTeams/devices/remote-provision-remote-login). 

### Create a unique Conditional Access policy for resource accounts

Microsoft Entra [Conditional Access](/azure/active-directory/conditional-access/overview) sets requirements that devices or accounts must meet in order to sign in. For Teams Rooms resource accounts, we recommend creating a new Conditional Access policy specific to your Teams Rooms resource accounts and then excluding the accounts from all other organization Conditional Access policies. To achieve multifactor authentication (MFA) with shared device accounts, we recommend a combination of known network location and compliant device.

#### Use location-based access with named locations

If shared devices are installed in a defined location that can be identified with a range of IP addresses, you can configure Conditional Access using [named locations](/azure/active-directory/conditional-access/location-condition) for these devices. This condition allows these devices to access your corporate resources only when they are within your network.

#### Use compliant devices

>[!NOTE]
>Device compliance requires Intune enrollment.

You can configure device compliance as a control in Conditional Access so that only compliant devices can access your corporate resources. Teams devices can be configured for Conditional Access policies based on device compliance. For more information, see [Conditional Access: Require compliant device](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device).

To set compliance policies for your devices using Intune, see [Use compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started).

#### Exclude resource accounts from sign-in frequency conditions

In Conditional Access, you can [configure sign-in frequency](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime#user-sign-in-frequency) to require users to sign in again to access a resource after a specified time period. If sign-in frequency is enforced for resource accounts, devices sign out until they're signed in again by an admin.

#### Using filters for devices

For more granular control for what can sign in to Teams using a resource account or for controlling policies for users signing into a Teams Room on Android device with their personal account, device filters can be used. [Filters for devices](/azure/active-directory/conditional-access/concept-condition-filters-for-devices) is a feature in Conditional Access that allows you to configure more granular policies for devices based on device properties available in Microsoft Entra ID. You can also use your own custom values by setting extension attributes 1-15 on the device object and then using those.

Use filters for devices to identify your shared devices and enable policies in two key scenarios:

1.  Excluding shared devices from policies applied for personal devices. For example, requiring device compliance *isn't enforced* for shared devices used for hot-desking, but *is enforced* for all other devices, based on model number.

2.  Enforcing special policies on shared devices that *shouldn't* be applied to personal devices. For example, requiring named locations as policy only for common-area devices based on an extension attribute you set for these devices (for example: CommonAreaPhone).

>[!NOTE] 
> Some attributes such as **model**, **manufacturer**, and **operatingSystemVersion** can only be set when devices are managed by Intune. If your devices are not managed by Intune, use extension attributes.
