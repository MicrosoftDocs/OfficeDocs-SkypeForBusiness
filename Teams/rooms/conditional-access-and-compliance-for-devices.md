---
title: Conditional Access and compliance best practices for Microsoft Teams Rooms
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: dimehta
ms.date: 08/22/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
description: Learn about recommended Conditional Access and Intune device compliance policies and best practices for Microsoft Teams Rooms.
---

# Conditional Access and Intune compliance for Microsoft Teams Rooms and panels

This article provides requirements and best practices for Conditional Access and Intune device compliance policies for Microsoft Teams Rooms on Windows, Teams Rooms on Android, and Teams panel devices that are used in shared spaces.

[!INCLUDE [teams-pro-license-requirement](../includes/teams-pro-license-requirement.md)]

## Requirements

- Teams Rooms resource accounts created, for more information, see [Create resource accounts for rooms and shared Teams devices](create-resource-account.md).
- A Microsoft Entra ID P1 Service Plan is required to use Conditional Access. Its included in the Microsoft Teams Rooms license or Shared Device license.

## Teams Rooms Conditional Access best practices

Conditional Access policies can secure the sign in process on devices that are in shared spaces. For an overview of Conditional Access in Microsoft Entra ID, see [What is Conditional Access in Microsoft Entra ID?](/azure/active-directory/conditional-access/overview).

When using Conditional Access to secure Teams Rooms, consider the following best practices:

- To simplify deployment and management, include all Microsoft 365 room resources accounts associated with Teams Rooms in one Entra ID user group.
- Have a naming standard for all Teams Rooms resource accounts. For example, the account names 'mtr-room1@contoso.com' and 'mtr-room2@contoso.com' both start with the prefix 'mtr-'. When account names are standardized, you can use dynamic groups in Microsoft Entra ID to automatically apply Conditional Access policies to all of these accounts at once. For more information on dynamic groups, see [Rules for dynamically populated groups membership](/azure/active-directory/enterprise-users/groups-dynamic-membership).
- Exclude your Teams Rooms resource accounts from all existing Conditional Access policies and create a new policy specific to the resource accounts.
- User interactive multifactor authentication (MFA) is not supported for Teams Rooms resource accounts since the resource accounts do not have a second device to approve the MFA request.

For a list of supported Conditional Access assignments for Teams Rooms, see [Supported Conditional Access policies](supported-ca-and-compliance-policies.md#supported-conditional-access-policies).

### Example Conditional Access policy

In this example, the Conditional Access policy works as follows:

1. The account signing in must be a member of a specific user group, in this example, the "Shared devices" group.
2. The account signing in must only be trying to access Office 365, Office 365 Exchange Online, Microsoft Teams Services, and Office 365 SharePoint Online. Attempts to sign into any other client app are rejected.
3. The authentication method must be modern authentication, legacy authentication mechanisms should be blocked.
4. The resource account must be signing in on the Windows or Android device platform.
5. The resource account must also sign in from a known, trusted location.
6. The resource account must be signing in from a compliant device.

If these conditions are met successfully, and the device has the correct username and password, then the resource account signs into Teams.

## Intune compliance for Teams Rooms

Compliance requirements are defined rules that devices must meet to be marked as compliant, such as minimum operating system version. Device compliance can be used as a condition in conditional access before the resource account can sign in.

For a list of supported Intune compliance policies for Teams Rooms, see [Supported device compliance policies](supported-ca-and-compliance-policies.md#supported-device-compliance-policies).

### Example Intune compliance policy for Teams Rooms on Windows

In this example for Teams Rooms on Windows

1. Require that a firewall is running on Teams Rooms on Windows.
2. Require a minimum operating system version.
3. Require that Microsoft Defender is running on Teams Rooms.
4. If Teams Rooms doesn't meet either of these requirements, it won't be marked as compliant, and the devices won't sign in.

This compliance policy should be assigned to the Teams Rooms devices and the Teams Rooms resource accounts.

### Example Intune compliance policy for Teams Rooms on Android and Teams panels

In this example for Teams Rooms on Android and Teams panels

1. Miniumum operating system version is greater than Android 10.
2. Block rooted devices.
3. Require encryption of data storage on device

This compliance policy should be assigned to the Teams Rooms devices and the Teams Rooms resource accounts.
