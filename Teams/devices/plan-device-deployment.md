---
title: "Plan your deployment for Teams phone devices and Displays"
ms.author: czawideh
author: cazawideh
manager: serdars
ms.reviewer: tony.woodruff
ms.topic: reference
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
f1.keywords:
  - NOCSH
search.appverid: MET150
description: "This article provides and overview the tasks and steps to deploy Teams phones and displays in your organization."
---

# Plan your deployment for Teams phone devices and Displays

A successful deployment of Teams phone devices and Teams Displays starts with planning. This article will take you through the tasks and steps to deploy these devices in your organization. It also provides guidance on devices usage, licensing, integrating with your environment, touchpoints, and management.

> [!TIP]
> [The Microsoft 365 Adoption Hub](https://adoption.microsoft.com/) is a great place to get started on your adoption journey with Microsoft Teams.

## Task 1: What are your deployment objectives?

Planning the rollout of Teams phones and Displays in your organization starts with your deployment goals. Teams devices support hybrid work in meeting rooms, offices, and other functional spaces. You'll need to determine where these devices will be used and by whom.

### Objective: Identify your device personas

Teams phones and Displays will fit one of two personas: 

- Personal devices
- Shared space devices

Personal and shared devices have different roles and usages. 

**Personal devices:** 

- Typically assigned to one user, signed in with that user's account, and enabled with a Teams feature license to access the service.
- Think of personal devices as having a one-to-one relationship, with one device per one user.
- Can be paired with the Teams desktop client and use features like Better Together
- May connect to a headset, wired or wireless
- Additional features on personal devices include hot-desking and Home Screen. 

**Shared space devices:**

- Perform a specific function, like a common area phone or meeting room device and require a dedicated account and feature license to access the service.
- Think of shared devices as having a one-to-many relationship: one device shared by many users.
- Deployed in shared spaces like meeting rooms, reception areas, or manufacturing floors. 
- Their user interfaces (UI) are specific to their function, such as Common Area Phone UI, or meeting room UI depend upon the function and placement of the shared device.
- Require configuration and optional hardening to ensure settings aren't changed, or to prevent the account from signing out. 
- Additional features on shared space devices include search on common area phones and hot-desking with idle timeout

### Objective: How many personal and shared space devices do you need?

Now that you've identified your device personas, you need to determine which certified devices you want to use and how many of them you need. To help you make this decision, consider the following questions: 

- How many personal devices are required and who will have one?
- How many rooms or spaces require shared devices? Will every space have the same type of device? 
- Will your devices need to meet specific requirements?
    - Examples include screen size, form factor, and manufacturer or model? For a list of certified phones and displays, see [Microsoft Teams certified devices](teams-ip-phones.md).
-  Do you need Teams phones or Teams displays? For a list of features supported by Teams phones, see [Phones for Microsoft Teams](phones-for-teams.md#features-supported-by-teams-phones) and for a list of features supported by Teams displays, see [Microsoft Teams displays](teams-displays.md#features-supported-by-teams-displays).
- Do you have enough devices for new users, or a process for new orders and delivery?
- Will you have spare devices available for maintenance or in case of hardware issues? Being able to swap a device quickly prevents disruptions in user experience.

## Task 2: What are your licensing requirements? 

Now you know how many devices you need, the next step is to determine how many licenses are needed. Teams phones and displays require licenses to access Microsoft Teams and Microsoft 365.

Shared and personal devices will need different licensing. For personal devices, licenses assigned to user accounts can be used. Shared devices need licenses specific to their function. For phones and displays, the applicable licenses are [the Common Area Phone license for Microsoft Teams](../set-up-common-area-phones.md#step-1---buy-the-licenses) and [the Microsoft Teams Rooms Standard license](../rooms/rooms-licensing.md#licensing-solutions-for-shared-communication-devices).

For more information and to compare your licensing options, see [Microsoft 365 licensing plans](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). 

## Task 3: What are your dependencies? 

### Objective: Plan your device identities

Identities enable devices to access Microsoft 365 services, and they should make devices easier to discover, manage, and connect to within your organization. To accomplish this, consider the following when planning device identities:

- User principal names and their format and domain
- Display names
- Address book discoverability
- Personal versus shared space device types
- Group versus user assigned licensing

### Objective: Review Conditional Access policies

Azure Active Directory Conditional Access policies are additional requirements that must be met before a device can be signed in.

As you plan your deployment

- Review existing Conditional Access policies that could affect your Teams phones and displays. You can do this in the Azure AD Admin Center using the [What If tool](/azure/active-directory/conditional-access/what-if-tool) and [Sign-in logs](/azure/active-directory/reports-monitoring/concept-sign-ins)

- Plan for new rules if needed

- Use Conditional Access features like device filters to apply rules to Teams phones and displays.

>[!NOTE]
>There are some Conditional Access policies that Android devices don't support. For guidance and best practices, see Android devices, see [Authentication best practices for Teams Android devices](authentication-best-practices-for-android-devices.md).

## Task 4: Prepare your environment

### Objective: Plan network basics

Teams Phone devices and displays require access to the internet to connect to Teams and function as intended. To get your network ready for deployment, consider the following:

- Does your network infrastructure have enough capacity? Consider switch ports, wireless access points, and other coverage.
- If you use VLANs and DHCP, are your scopes sized accordingly?
- Evaluate and test network paths from where devices are deployed to Microsoft 365. 
- Open the required firewall ports and URLs for Microsoft 365 as per guidance.
- Review and test E911 requirements and configuration for location accuracy and compliance. 
- Avoid using a proxy server and optimize media paths for reliability and quality.

### Objective: Physical considerations

Consider the physical spaces that your Teams phones and displays will be used in.

Key aspects include

- **Power:** Do you have enough electrical outlets? If the device needs an external power source, how close can you position it to an outlet?
- **Device placement:** Where will your device physically be? Review desk stands, wall mounts, and other accessories from the original equipment manufacturer (OEM).
- **Security:** Does your device need to be locked in certain spaces?
- **Accessibility:** Does the device meet the accessibility requirements of its primary user? Consider where it's placed, wire length, and handset or headset usability.

### Task 5: How will you manage deployed devices?

Teams phones and displays are managed from two to three Microsoft 365 portals and their respective PowerShell modules: 

#### Azure Active Directory Admin Center

Use the Azure AD Admin Center to manage

- All identity-related tasks for Teams phones and displays
- Conditional Access policies 
- Password resets

#### Teams Admin Center

Use the Teams Admin Center to manage

- [Device settings for Teams](../business-voice/manage-devices.md)
- [Configuration profiles](device-management.md#use-configuration-profiles-in-teams)
- [Device tagging](manage-device-tags.md)
- [Remote sign-in and sign-out](remote-sign-in-and-sign-out.md)
- Call analytics  
- Firmware
- Troubleshooting and downloading logs

#### Endpoint Manager Admin Center (if you use Intune for device management)

Use the Endpoint Manager Admin Center to manage: 

- Device compliance policies
- Enrollment restrictions
- Corporate device identifiers
- Device filters
