---
title: Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms
ms.author: tonysmit
author: tonysmit
ms.reviewer: kspiess
ms.date: 02/28/2022
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Rooms
  - Tier1
description: Learn about supported and recommended Conditional Access and Intune device compliance policies for Microsoft Teams Rooms.
---

# Supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms and Teams Android Devices

This article provides supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms. For best practices and example policies, see [Conditional Access and Intune compliance best practices for Microsoft Teams Rooms](conditional-access-and-compliance-for-devices.md).

[!INCLUDE [teams-pro-license-requirement](../includes/teams-pro-license-requirement.md)]

> [!NOTE]
> Teams Rooms must already be deployed on the devices you want to assign
Conditional Access policies to. If you haven't deployed Teams Rooms yet,
see [Create resource accounts for rooms and shared Teams devices](create-resource-account.md)
and [Deploy Microsoft Teams Rooms on Android](../devices/collab-bar-deploy.md)
for more information.

## Supported Conditional Access policies  

The following list includes the supported Conditional Access policies for Teams Rooms on Windows and Android, and for policies on Teams panels, phones, and displays.

| Assignment                               | Teams Rooms on Windows                                                                                                                                                                              | Teams Rooms on Android and panels                                                                                                                                                                              | Teams phones and displays                                                                                                                                                    |
|------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| User or workload identities              | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Cloud apps or actions                    | Supported <br><br> Teams Rooms needs to access the following three Cloud apps when in Teams only mode: Office 365 Exchange Online, Office 365 SharePoint Online, and Microsoft Teams | Supported <br><br> Teams Rooms needs to access the following three Cloud apps when in Teams only mode: Office 365 Exchange Online, Office 365 SharePoint Online, and Microsoft Teams | Supported<br><br>Teams Android devices need to access the following three Cloud apps: Office 365 Exchange Online, Office 365 SharePoint Online, and Microsoft Teams  |
| **Conditions**                           | ---                                                                                                                                                                                  | ---                                                                                                                                                                                  | ---                                                                                                                                                                  |
| User risk                                | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Sign-in risk                             | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Device platforms                         | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Locations                                | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Client apps                              | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                        |
| Filter for devices                       | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| **Grant**                                | ---                                                                                                                                                                                  | ---                                                                                                                                                                                  | ---                                                                                                                                                                  |
| Block access                             | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Grant access                             | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                                    |
| Require multi-factor authentication      | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                                        | Supported                                                                                                                                                            |
| Require device to be marked as compliant | Supported                                                                                                                                                                            | Supported                                                                                                                                                                            | Supported                                                                                                                                                            |
| Require Hybrid Azure AD joined device    | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                        |
| Require approved client app              | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                        |
| Require app protection policy            | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                        |
| Require password change                  | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                                        | Not supported                                                                                                                                                        |

> [!NOTE]
> Skype for Business Online is retired and not supported. Skype for
Business Online cloud app is not supported for device compliance based
Conditional Access policies.

> [!NOTE]
> Microsoft Teams Rooms on Windows must meet the following
requirements to support device compliance grant controls:
>
> - Microsoft Teams Rooms application 4.8.19.0 or above
> - Windows 10 version 20H2 and above (10.0.19042)

## Supported device compliance policies 

Microsoft Teams Rooms on Windows and Teams Rooms on Android support
different device compliance policies.

#### [Teams Rooms on Windows](#tab/mtr-w)

Below is a table of device compliance settings and recommendations for
their use with Teams Rooms.  

| Policy                                                                                                                      | Availability   | Notes                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------|----------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| [**Device health**](/mem/intune/protect/compliance-policy-create-windows#device-health)                                     | --             | --                                                                                                                                          |
| Require BitLocker                                                                                                           | Supported      | Only use if you have first enabled BitLocker on Teams Rooms.                                                                                |
| Require Secure Boot to be enabled on the device                                                                             | Supported      | Secure Boot is  a requirement for Teams Rooms.                                                                                              |
| Require code integrity                                                                                                      | Supported      | Code integrity is already a requirement for Teams Rooms.                                                                                    |
| [**Device Properties**](/mem/intune/protect/compliance-policy-create-windows#device-properties)                             | --             | --                                                                                                                                          |
| Operating System Version (minimum, maximum)                                                                                 | Not supported  | Teams Rooms automatically updates to newer versions of Windows and setting values here could prevent successful sign-in after an OS update. |
| OS version for mobile devices (minimum, maximum)                                                                            | Not supported. |                                                                                                                                             |
| Valid operating system builds                                                                                               | Not supported  |                                                                                                                                             |
| [**Configuration Manager Compliance**](/mem/intune/protect/compliance-policy-create-windows#device-properties)              | --             | --                                                                                                                                          |
| Require device compliance from Configuration Manager                                                                        | Supported      |                                                                                                                                             |
| [**System security**](/mem/intune/protect/compliance-policy-create-windows#system-security)                                 | --             | --                                                                                                                                          |
| All password policies                                                                                                       | Not supported  | Password policies can prevent the local Skype account from automatically signing in.                                                        |
| Require encryption of data storage on device.                                                                               | Supported      | Only use if you have first enabled encryption of data storage on Teams Rooms.                                                               |
| Firewall                                                                                                                    | Supported      | Firewall is already a requirement for Teams Rooms                                                                                           |
| Trusted Platform Module (TPM)                                                                                               | Supported      | Trusted Platform Module (TPM) is already a requirement for Teams Rooms.                                                                     |
| Antivirus                                                                                                                   | Supported      | Antivirus (Windows Defender) is already a requirement for Teams Rooms.                                                                      |
| Antispyware                                                                                                                 | Supported      | Antispyware (Windows Defender) is already a requirement for Teams Rooms.                                                                    |
| Microsoft Defender Antimalware                                                                                              | Supported      | Microsoft Defender Antimalware is already a requirement for Teams Rooms.                                                                    |
| Microsoft Defender Antimalware minimum version                                                                              | Not supported. | Teams Rooms automatically updates this component so there's no need to set compliance policies.                                             |
| Microsoft Defender Antimalware security intelligence up-to-date                                                             | Supported      | Validate that Microsoft Defender Antimalware is already a requirement for Teams Rooms.                                                      |
| Real-time protection                                                                                                        | Supported      | Real-time protections are already a requirement for Teams Rooms.                                                                            |
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-windows#microsoft-defender-for-endpoint) | --             | --                                                                                                                                          |
| Require the device to be at or under the machine risk score.                                                                | Supported      |                                                                                                                                             |

#### [Teams Rooms on Android](#tab/mtr-a)

Below is a table of device compliance settings and recommendations for
their use with Teams Rooms.  

| Policy                                                                                                                                  | Availability  | Notes                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------|---------------|-------------------------------------------------------------------------------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint)             | --            | --                                                                            |
| Require the device to be at or under the machine risk score                                                                             | Not supported |                                                                               |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android#device-health)                                                 | --            | --                                                                            |
| Device managed with device administrator                                                                                                | Required      | Teams Android devices management requires device administrator to be enabled. |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| Require the device to be at or under the device threat level                                                                            | Not supported |                                                                               |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health)                                           | --            | --                                                                            |
| Google Play Services is configured                                                                                                      | Not supported | Google play isn't installed on Teams Android devices.                         |
| Up-to-date security provider                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| Threat scan on apps                                                                                                                     | Not supported | Google play isn't installed on Teams Android devices.                         |
| SafetyNet device attestation                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties)                                         | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android#system-security)                                             | --            | --                                                                            |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |
| [**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security)                                             | --            | --                                                                            |
| Block apps from unknown sources                                                                                                         | Not supported | Only Teams admins install apps or OEM tools                                   |
| Company Portal app runtime integrity                                                                                                    | Supported     |                                                                               |
| Restricted apps                                                                                                                         | Not supported |                                                                               |
| Block USB debugging on device                                                                                                           | Supported     |                                                                               |
| [**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices)                                      | --            | --                                                                            |
| Maximum minutes of inactivity before password are required                                                                              | Not supported |                                                                               |
| Require a password to unlock mobile devices                                                                                             | Not supported |                                                                               |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later)                                   | --            | --                                                                            |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | --            | --                                                                            |
| Required password type                                                                                                                  | Not supported |                                                                               |

#### [Teams phones and displays](#tab/phones)

Below is a table of device compliance settings and recommendations for their use with Teams phones and displays.  

| Policy                                                                                                                                  | Availability  | Notes                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------|---------------|-------------------------------------------------------------------------------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint)             | --            | --                                                                            |
| Require the device to be at or under the machine risk score                                                                             | Not supported |                                                                               |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android#device-health)                                                 | --            | --                                                                            |
| Device managed with device administrator                                                                                                | Required      | Teams Android devices management requires device administrator to be enabled. |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| Require the device to be at or under the device threat level                                                                            | Not supported |                                                                               |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health)                                           | --            | --                                                                            |
| Google Play Services is configured                                                                                                      | Not supported | Google play isn't installed on Teams Android devices.                         |
| Up-to-date security provider                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| Threat scan on apps                                                                                                                     | Not supported | Google play isn't installed on Teams Android devices.                         |
| SafetyNet device attestation                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties)                                         | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android#system-security)                                             | --            | --                                                                            |
| Require encryption of data storage on device.                                                                                           | Supported     | Manufacturers might configure encryption attributes on their devices in a way that Intune doesn't recognize. If this happens, Intune marks the device as noncompliant.<br><br>How manufacturers configure these encryption attributes can vary depending on the model of the device. For more information a specific model, contact the device manufacturer. |
| [**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security)                                             | --            | --                                                                            |
| Block apps from unknown sources                                                                                                         | Not supported | Only Teams admins install apps or OEM tools                                   |
| Company Portal app runtime integrity                                                                                                    | Supported     |                                                                               |
| Restricted apps                                                                                                                         | Not supported |                                                                               |
| Block USB debugging on device                                                                                                           | Supported     |                                                                               |
| [**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices)                                      | --            | --                                                                            |
| Maximum minutes of inactivity before password are required                                                                              | Not supported |                                                                               |
| Require a password to unlock mobile devices                                                                                             | Not supported |                                                                               |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later)                                   | --            | --                                                                            |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | --            | --                                                                            |
| Required password type                                                                                                                  | Not supported |                                                                               |



#### [Teams panels](#tab/panels)

Below is a table of device compliance settings and recommendations for their use with Teams panels.  

| Policy                                                                                                                                  | Availability  | Notes                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------|---------------|-------------------------------------------------------------------------------|
| [**Microsoft Defender for Endpoint**](/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint)             | --            | --                                                                            |
| Require the device to be at or under the machine risk score                                                                             | Not supported |                                                                               |
| [**Device Health**](/mem/intune/protect/compliance-policy-create-android#device-health)                                                 | --            | --                                                                            |
| Device managed with device administrator                                                                                                | Required      | Teams Android devices management requires device administrator to be enabled. |
| Rooted devices                                                                                                                          | Supported     |                                                                               |
| Require the device to be at or under the device threat level                                                                            | Not supported |                                                                               |
| [**Google Play Protect**](/mem/intune/protect/compliance-policy-create-android#device-health)                                           | --            | --                                                                            |
| Google Play Services is configured                                                                                                      | Not supported | Google play isn't installed on Teams Android devices.                         |
| Up-to-date security provider                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| Threat scan on apps                                                                                                                     | Not supported | Google play isn't installed on Teams Android devices.                         |
| SafetyNet device attestation                                                                                                            | Not supported | Google play isn't installed on Teams Android devices.                         |
| [**Device properties**](/mem/intune/protect/compliance-policy-create-android#device-properties)                                         | --            | --                                                                            |
| Operating System Version (minimum, maximum)                                                                                             | Supported     |                                                                               |
| [**System security**](/mem/intune/protect/compliance-policy-create-android#system-security)                                             | --            | --                                                                            |
| Require encryption of data storage on device.                                                                                           | Supported     |                                                                               |
| [**Device security**](/mem/intune/protect/compliance-policy-create-android#device-security)                                             | --            | --                                                                            |
| Block apps from unknown sources                                                                                                         | Not supported | Only Teams admins install apps or OEM tools                                   |
| Company Portal app runtime integrity                                                                                                    | Supported     |                                                                               |
| Restricted apps                                                                                                                         | Not supported |                                                                               |
| Block USB debugging on device                                                                                                           | Supported     |                                                                               |
| [**All Android devices*](/mem/intune/protect/compliance-policy-create-android#all-android-devices)                                      | --            | --                                                                            |
| Maximum minutes of inactivity before password are required                                                                              | Not supported |                                                                               |
| Require a password to unlock mobile devices                                                                                             | Not supported |                                                                               |
| [**Android 10 and later**](/mem/intune/protect/compliance-policy-create-android#android-10-and-later)                                   | --            | --                                                                            |
| [**Android 9 and earlier or Samsung Knox**](/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox) | --            | --                                                                            |
| Required password type                                                                                                                  | Not supported |                                                                               |

---
