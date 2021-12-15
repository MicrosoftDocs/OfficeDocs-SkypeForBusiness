---
title: "Identity best practices for Android devices"
author: amandafrechinjackson
ms.author: v-amandaf
manager: jsarrasin
ms.date: 12/16/2021
ms.topic: conceptual
audience: ITPro
ms.service: msteams
search.appverid: MET150 
ms.reviewer: 
description: A best practices guide for Teams Android devices.
ms.collection: 
  - M365-voice
  - M365-collaboration
  - skype-for-business-itpro
  - skype-for-business-online
f1.keywords:
- NOCSH
localization_priority: Normal
appliesto: 
  - Microsoft Teams
---

# Identity best practices for Teams Android devices

With the increase in adoption of Teams Android devices, customers need guidance on best practices for deploying authentication policies for their Microsoft Teams phones and calling devices, specifically those deployed in conference rooms or common areas. Although Teams devices are built on the Android operating system, a policy meant for Android mobile phones may not apply to Teams devices owned by the tenant.

This article provides general guidance and answers for some of the frequently encountered scenarios related to authentication and Conditional Access policies for Teams devices.

**Note:** Conditional Access requires an Azure Active Directory (Azure AD) Premium subscription.

## User-based devices vs common-area devices

Teams devices deployed in common areas (meeting-room devices or common-area phones) cannot be managed with the same set of requirements for enrollment and compliance that are typically applied to user-based devices. When authentication requirements for users are enabled for devices in common areas, the following problems could occur:

1.  **Devices are signed out due to password policies**

Devices are usually signed out for one key reason: accounts used on Teams devices have a password-expiration policy. Unlike users, the accounts used with Teams devices in common areas can be considered non-human accounts. When their passwords expire, there’s no user to update and restore them to a valid state. If your organization requires passwords to expire and reset periodically, these accounts will stop functioning on Teams devices and lead to disruption. To recover, it requires a Teams administrator to reset the password and sign back in to these devices.

2.  **Devices fail to sign in due to conditional access policies**

When accounts on Teams shared devices are grouped with regular users or user-based devices for Azure AD Conditional Access policies, these devices fail to sign in and end up in a bad state, as these non-human accounts cannot complete required actions to meet conditional access requirements. For instance, if multi-factor authentication (MFA) is required for accessing Teams, these accounts require user intervention to complete second-factor authentication. As a result, Teams device deployments will not function as expected. Similarly, if the account is configured to re-authenticate every X days, a common-area device cannot resolve the challenge without user intervention.

## Best practices for Teams shared device deployments 

Microsoft recommends deploying the following settings to avoid common issues you may face when deploying Teams devices in your organization.

### **Password policy** 

Teams shared devices should use an [Exchange resource account](https://docs.microsoft.com/en-us/exchange/recipients-in-exchange-online/manage-resource-mailboxes), which is essentially a user account in Azure Active Directory. These accounts can either be synced from Active Directory or created directly in Azure AD. Any password-expiry policies for users also apply to accounts used on Teams shared devices as well.

To avoid disruptions caused by password expiry, Microsoft recommends that passwords for Teams shared devices are set to not expire.

Starting with Teams devices CY21 [Update #1](https://support.microsoft.com/en-us/office/what-s-new-in-microsoft-teams-devices-eabf4d81-acdd-4b23-afa1-9ee47bb7c5e2#ID0EBD=Desk_phones) (Teams version 1449/1.0.94.2021022403 for Teams phones) and [CY2021 Update #2](https://support.microsoft.com/en-us/office/what-s-new-in-microsoft-teams-devices-eabf4d81-acdd-4b23-afa1-9ee47bb7c5e2#ID0EBD=Teams_Rooms_on_Android) (Teams version 1449/1.0.96.2021051904 for Microsoft Teams Rooms on Android), tenant administrators can sign into Teams devices remotely. So, instead of giving out the password for these accounts to technicians to set up devices, IT administrators can instead issue verification codes and then sign into these devices themselves from the Teams admin center.

See [Remote provisioning and sign in for Teams Android devices](https://docs.microsoft.com/en-us/MicrosoftTeams/devices/remote-provision-remote-login) for more details. 

### **Conditional Access policies** 

Azure AD Conditional Access brings together identity signals to make decisions and enforce organizational policies. Conditional Access is at the heart of the new identity-driven control plane.

For Teams devices, review the following guidance to determine if you have authored the appropriate policies.

### Multi-factor authentication 

Accounts used on common-area devices (for example, conference rooms) are linked to a room or physical space and not a human user. Any multi-factor authentication is not appropriate for accounts used in common areas. Microsoft recommends excluding common-area accounts from any multi-factor authentication policies.

**Recommendation:** Use either [named locations](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/location-condition) or [require compliant device](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) for these common-area accounts.

### Location-based access with named locations

If common-area devices are provisioned in a well-defined location that can be identified with a range of IP addresses, you can configure Conditional Access using [named locations](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/location-condition) for these devices. By doing so, you can ensure that these devices can access your corporate resources only when they are within your network and not outside it.

### Require compliant device

**Note:** Device compliance requires an Intune license.

If you are enrolling your common-area devices into Intune, you can configure device compliance as a control in Conditional Access so that only compliant devices can access your corporate resources. Teams devices can be configured for Conditional Access policies based on device compliance as described in [Conditional Access: Require compliant or hybrid Azure AD joined device](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device).

You can determine compliance settings for a device using Intune as described in [Use compliance policies to set rules for devices you manage with Intune](https://docs.microsoft.com/intune/protect/device-compliance-get-started).

However, enforcing this policy has a limitation for hot-desking scenarios. For hot-desking scenarios, the device will not be enrolled into the hot-desk user account. Requiring a compliant device only works for the room account used to set up the device and will not work with hot-desking users. If hot-desking is being used on a set of common-area devices, Microsoft recommends excluding these devices from device-compliance policies and using named locations instead.

To increase security, you can also [require multi-factor authentication](https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa) for hot-desking users in addition to the named-location policies.

### Sign-in frequency

In Conditional Access, you can [configure sign-in frequency](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime#user-sign-in-frequency) to require users to sign in again to access a resource after a specified time period. If sign-in frequency is enforced for room accounts, common-area devices will sign out until they are signed in again. This will disrupt the use of shared devices until an admin can intervene. Microsoft recommends excluding the shared accounts from any sign-in frequency policies to avoid disruption in usage.

### Filters for devices

[Filters for devices](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/concept-condition-filters-for-devices) is a new feature in Conditional Access that allows you to configure more granular policies for devices based on device properties available in Azure AD. You can also use your own custom values by setting extension attributes 1-15 on the device object and then using those.

You can use filters for devices to identify your common-area devices and enable policies in two key scenarios:

1.  Excluding common area devices from policies applied to end-user devices. For example: requiring device compliance is not enforced for common-area devices used for hot-desking but is enforced for all other devices based on model number.

2.  Enforcing special policies on common-area devices that should not be applied to end-user devices. For example: requiring named locations as policy only for common-area devices based on an extension attribute you set for these devices (for instance, “CommonAreaPhone”).

**Note:** Some of the attributes (such as **model**, **manufacturer**, and **operatingSystemVersion**) can only be set when devices are managed by Intune. If your devices are not managed by Intune, use extension attributes.