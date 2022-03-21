---
title: "Conditional Access and compliance best practices for Microsoft Teams Rooms"
ms.author: czawideh
author: cazawideh
ms.reviewer: sohailta
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
description: Learn about recommended Conditional Access and Intune device compliance policies and best practices for Microsoft Teams Rooms.
---

# Conditional Access and Intune compliance for Microsoft Teams Rooms

This article provides requirements and best practices for Conditional Access and Intune device compliance policies for Microsoft Teams Rooms that are used in shared spaces.

## Requirements

Teams Rooms must already be deployed on the devices you want to assign
Conditional Access policies to. If you haven’t deployed Teams Rooms yet,
see [Create resource accounts for rooms and shared Teams devices](with-office-365.md)
and [Deploy Microsoft Teams Rooms on Android](../devices/collab-bar-deploy.md)
for more information.

An Azure Active Directory P1 Service Plan is required to use Conditional
Access. It’s included in the Microsoft Teams Rooms license.

## Teams Rooms Conditional Access best practices

Conditional Access policies can secure the sign-in process on devices that are in shared spaces and used by multiple people. For an overview of Conditional Access in Azure Active Directory (Azure AD), see [What is Conditional Access in Azure Active Directory?](/azure/active-directory/conditional-access/overview).

When using Conditional Access to secure Teams Rooms, consider the
following best practices:

-   To simplify deployment and management, include all Microsoft 365
    room resources accounts associated with Teams Rooms in one user
    group.

-   Have a naming standard for all Teams Rooms resource accounts. For
    example, the account names ‘mtr-room1@contoso.com’ and
    ‘mtr-room2@contoso.com’ both start with the prefix ‘mtr-‘.
    When account names are standardized, you can use dynamic groups in Azure AD
    to automatically apply Conditional Access policies to all of these
    accounts at once. See [Rules for dynamically populated groups membership](/azure/active-directory/enterprise-users/groups-dynamic-membership) for more information on dynamic groups.

For a list of supported Conditional Access assignments for Teams Rooms, see [Supported Conditional Access policies](supported-ca-and-compliance-policies.md#supported-conditional-access-policies).

## Example Conditional Access policy

In the example below, the Conditional Access policy works as follows:

1.  The account signing in must be a member of a specific user group, in
    this example, the “Shared devices” group.

2.  The account signing in must only be trying to access Exchange
    Online, Microsoft Teams, or SharePoint Online. Attempts to sign into
    any other client app will be rejected.

3.  The resource account must be signing in on the Windows device
    platform.

4.  The resource account must also sign in from a known, trusted
    location.

If these conditions are met successfully, and the user enters the
correct username and password, then the resource account will sign into
Teams.

## Conditional Access with Microsoft Intune compliance for Teams Rooms

Compliance requirements are defined rules that devices must meet to be
marked as compliant, such as minimum operating system version. Devices
must be considered compliant before they can be used to sign into a
resource account.

For a list of supported Intune compliance policies for Teams Rooms, see [Supported device compliance policies](supported-ca-and-compliance-policies.md#supported-device-compliance-policies).

For more information on setting up Intune with Teams Android devices, see [Configure Intune to enroll Teams Android-based devices](../devices/phones-displays-deploy.md#configure-intune-to-enroll-teams-android-based-devices).

## Example (Windows only): Conditional Access with Intune device compliance

In this example for Teams Rooms on Windows

1. Require that a firewall is running on Teams Rooms on Windows.

2. Require that Microsoft Defender is running on Teams Rooms.

3. If a Teams Room doesn't meet either of these requirements, it won't be marked as compliant, and the devices won't sign in.

This compliance policy applies to all users, not just Teams resource accounts.
