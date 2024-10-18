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

# Authentication best practices for Teams shared device management on Android devices

The goals of devices used with Teams make different device management strategies necessary. For example, a personal business tablet used by a single sales person has a different set of needs from an on-call phone shared by many customer service people.

Security administrators and operations teams must plan for the devices that can be used in the organization. They must  implement *security* measures best suited to each purpose. This article's recommendations make some of those decisions easier.

>[!NOTE]
>Conditional Access requires a Microsoft Entra ID P1 or P2 subscription.

>[!NOTE]
>Policies for Android mobile devices may not apply to Teams Android devices.

## Authentication recommendations are different for personal versus shared android devices

Shared Teams devices can't use the same requirements for enrollment and compliance that are used on personal devices. Applying personal device authentication requirements to shared devices cause sign in issues.

1.  **Devices are signed out due to password policies.**

    Accounts used on Teams devices have a password-expiration policy. The accounts used with shared devices don't have a specific user to update and restore them to a working state when their passwords expire. If your organization requires passwords to expire and reset occasionally, these accounts stop working on Teams devices until a Teams administrator resets the password and signs back in.

    **Challenge**: When it comes to accessing. Teams from a device, a person's account has a password-expiration policy. When the password is going to expire, they change it. But accounts used on *shared devices*(Resource accounts) may not be connected to a single person who can change a password as required. This means a password can expire and leave workers on the spot, not knowing how to resume their work.

    When your organization requires a password reset or enforces password expiration, be sure a Teams administrator is prepared to reset the password so these shared accounts can sign back in.

2.  **Devices fail to sign in due to conditional access policies.**

    **Challenge**: Shared devices can't comply with Microsoft Entra Conditional Access policies for user accounts or personal devices. If shared devices are grouped with user accounts or personal devices for a Conditional Access policy, the sign-in will *fail*.

    For example, if multifactor authentication is required for accessing Teams, user entry of a code is needed to complete that authentication. Shared devices don't generally have a single user that can configure and complete multifactor authentication. Also, if the account must reauthenticate every X days, a shared device can't resolve the challenge without a user's intervention.

## Best practices for the deployment of shared android devices with Teams

Microsoft recommends the following settings when deploying Teams devices in your organization.

### **Use a Resource account and curtail its password expiration**

Teams shared devices should use an [Exchange resource mailbox](/exchange/recipients-in-exchange-online/manage-resource-mailboxes). Creating these mailboxes generates an account automatically. You can either sync these accounts to Microsoft Entra ID from Active Directory or create them directly in Microsoft Entra ID. Any password expiration policies for users will also apply to accounts used on Teams shared devices, therefore, to avoid disruptions caused by password expiration policies, set the password expiration policy for shared devices to never expire.

Starting with Teams devices CY21 [Update #1](https://support.microsoft.com/office/what-s-new-in-microsoft-teams-devices-eabf4d81-acdd-4b23-afa1-9ee47bb7c5e2#ID0EBD=Desk_phones) (Teams version 1449/1.0.94.2021022403 for Teams phones) and [CY2021 Update #2](https://support.microsoft.com/office/what-s-new-in-microsoft-teams-devices-eabf4d81-acdd-4b23-afa1-9ee47bb7c5e2#ID0EBD=Teams_Rooms_on_Android) (Teams version 1449/1.0.96.2021051904 for Microsoft Teams Rooms on Android), tenant administrators can sign into Teams devices remotely. Instead of sharing passwords with technicians to set up devices, Tenant administrators should use remote sign-in to issue verification codes. You can sign into these devices from the Teams admin center.

For more information, see [Remote provisioning and sign in for Teams Android devices](/MicrosoftTeams/devices/remote-provision-remote-login). 

### **Review these Conditional Access policies**

Microsoft Entra Conditional Access sets other requirements that devices must meet in order to sign in. For Teams devices, review the guidance that follows to determine if you have authored the policies that allow shared device users to do their work.

> [!TIP]
> For an overview of Conditional Access, see [What is Conditional Access](/azure/active-directory/conditional-access/overview)?


>[!TIP]
>Use either [named location](/azure/active-directory/conditional-access/location-condition) or [require compliant device](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) to secure shared devices.

### You can use location-based access with named locations

If shared devices are provisioned in a well-defined location that can be identified with a range of IP addresses, you can configure Conditional Access using [named locations](/azure/active-directory/conditional-access/location-condition) for these devices. This conditional will allow these devices to access your corporate resources only when they are within your network.

### When and when not to require compliant shared devices

>[!NOTE]
>Device compliance requires an Intune license.

If you're enrolling shared devices into Intune, you can configure device compliance as a control in Conditional Access so that only compliant devices can access your corporate resources. Teams devices can be configured for Conditional Access policies based on device compliance. For more information, see [Conditional Access: Require compliant or Microsoft Entra hybrid joined device](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device).

To set compliance setting for your devices using Intune, see [Use compliance policies to set rules for devices you manage with Intune](/mem/intune/protect/device-compliance-get-started).

>[!NOTE]
> Shared devices being used for *hot-desking* should be excluded from compliance policies. Compliance polices prevent the devices from enrolling into the hot desk user account. **Instead, use named locations to secure these devices**.
> To increase security, you can also [require multi-factor authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa) for *hot-desking users / user accounts* in addition to the named location policies.

### Exclude shared devices from sign-in frequency conditions

In Conditional Access, you can [configure sign-in frequency](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime#user-sign-in-frequency) to require users to sign in again to access a resource after a specified time period. If sign-in frequency is enforced for room accounts, shared devices sign out until they're signed in again by an admin. Microsoft recommends excluding shared devices from any sign-in frequency policies.

### Using Filters for devices

[Filters for devices](/azure/active-directory/conditional-access/concept-condition-filters-for-devices) is a feature in Conditional Access that allows you to configure more granular policies for devices based on device properties available in Microsoft Entra ID. You can also use your own custom values by setting extension attributes 1-15 on the device object and then using those.

Use filters for devices to identify your common-area devices and enable policies in two key scenarios:

1.  Excluding shared devices from policies applied for personal devices. For example, requiring device compliance *isn't enforced* for shared devices used for hot-desking, but *is enforced* for all other devices, based on model number.

2.  Enforcing special policies on shared devices that *shouldn't* be applied to personal devices. For example, requiring named locations as policy only for common-area devices based on an extension attribute you set for these devices (for example: “CommonAreaPhone”).

>[!NOTE] 
> Some attributes such as **model**, **manufacturer**, and **operatingSystemVersion** can only be set when devices are managed by Intune. If your devices are not managed by Intune, use extension attributes.

### Microsoft Teams Rooms usage report
New capabilities like the camera video minutes and call minutes data have been added to the Teams Rooms Pro management portal in the report section. This data allows users to track engagement during each meeting and have a better understanding of those data. 
