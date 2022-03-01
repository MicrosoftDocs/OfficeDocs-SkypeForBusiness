---
title: "Supported Conditional Access and Intune compliance policies for Microsoft Teams Rooms"
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
description: Learn about supported and recommended Conditional Access and Intune device compliance policies for Microsoft Teams Rooms.
---

# Supported Conditional Access and Intune compliance policies for Microsoft Teams Rooms

This article provides supported Conditional Access and Intune device compliance policies for Microsoft Teams Rooms on Windows and on Android.

## Supported Conditional Access policies  

Not every Conditional Access policy is supported on Teams Rooms on
Windows and Teams Rooms on Android devices. Below is a list of the
supported Conditional Access policies for each OS: 

<table>
<colgroup>
<col style="width: 28%" />
<col style="width: 35%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Assignment</strong> </th>
<th><strong>Windows</strong> </th>
<th><strong>Android</strong> </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>User or workload identities </td>
<td><p>Supported</p>
<p> </p>
<p>Add relevant Teams Rooms resource accounts. </p></td>
<td><p>Supported </p>
<p> </p>
<p>Add relevant Teams Rooms resource accounts. </p></td>
</tr>
<tr class="even">
<td>Cloud apps or actions </td>
<td><p>Supported   </p>
<p> </p>
<p>Teams Rooms needs to access the following three Cloud apps when in
Teams only mode: Office 365 Exchange Online, Office 365 SharePoint
Online, and Microsoft Teams </p></td>
<td><p>Supported  </p>
<p> </p>
<p>Teams Android devices needs to access the following three Cloud apps:
Office 365 Exchange Online, Office 365 SharePoint Online, and Microsoft
Teams </p></td>
</tr>
<tr class="odd">
<td><strong>Conditions</strong> </td>
<td> </td>
<td> </td>
</tr>
<tr class="even">
<td>User risk </td>
<td>Supported </td>
<td>Supported </td>
</tr>
<tr class="odd">
<td>Sign-in risk </td>
<td>Supported </td>
<td>Supported </td>
</tr>
<tr class="even">
<td>Device platforms </td>
<td><p>Supported  </p>
<p> </p>
<p>Select Windows for Teams Rooms on Windows. </p></td>
<td><p>Supported  </p>
<p> </p>
<p>Select Android for Teams Rooms on Android. </p></td>
</tr>
<tr class="odd">
<td>Locations </td>
<td>Supported </td>
<td>Supported </td>
</tr>
<tr class="even">
<td>Client apps </td>
<td>Supported </td>
<td>Not supported </td>
</tr>
<tr class="odd">
<td>Filter for devices </td>
<td>Supported </td>
<td>Supported </td>
</tr>
<tr class="even">
<td><strong>Grant</strong> </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td>Block access </td>
<td>Supported </td>
<td>Supported </td>
</tr>
<tr class="even">
<td>Grant Access </td>
<td> </td>
<td> </td>
</tr>
<tr class="odd">
<td>
<p>Require multi-factor authentication </p>
</td>
<td>Not supported </td>
<td>Not supported </td>
</tr>
<tr class="even">
<td>
<p>Require device to be marked as compliant </p>
</td>
<td>Supported </td>
<td>Supported </td>
</tr>
<tr class="odd">
<td>
<p>Require Hybrid Azure AD joined device </p>
</td>
<td>Not supported </td>
<td>Not supported </td>
</tr>
<tr class="even">
<td>
<p>Require approved client app </p>
</td>
<td>Not supported </td>
<td>Not supported </td>
</tr>
<tr class="odd">
<td>
<p>Require app protection policy </p>
</td>
<td>Not supported </td>
<td>Not supported </td>
</tr>
<tr class="even">
<td>
<p>Require password change </p>
</td>
<td>Not supported </td>
<td>Not supported </td>
</tr>
</tbody>
</table>

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

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Policy</strong> </th>
<th><strong>Notes</strong> </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22device-health"><strong><u>Device
Health</u></strong></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Require BitLocker </td>
<td><p>Supported  </p>
<p> </p>
<p>Only use if you have first enabled BitLocker on Teams
Rooms. </p></td>
</tr>
<tr class="odd">
<td>Require Secure Boot to be enabled on the device </td>
<td><p>Supported  </p>
<p> </p>
<p>Secure Boot is already a requirement for Teams Rooms. </p></td>
</tr>
<tr class="even">
<td>Require code integrity </td>
<td><p>Supported  </p>
<p> </p>
<p>Code integrity is already a requirement for Teams Rooms. </p></td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22device-properties"><strong><u>Device
Properties</u></strong></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Operating System Version (minimum, maximum) </td>
<td><p>Not supported.  </p>
<p> </p>
<p>Teams Rooms automatically updates to newer versions of
Windows<u>,</u> and setting values here could prevent successful sign in
after an OS update. </p></td>
</tr>
<tr class="odd">
<td>OS version for mobile devices (minimum, maximum) </td>
<td>Not supported. </td>
</tr>
<tr class="even">
<td>Valid operating system builds </td>
<td>Not supported </td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22device-properties"><strong><u>Configuration
Manager Compliance</u></strong></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Require device compliance from Configuration Manager </td>
<td>Supported </td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22system-security"><strong><u>System
Security</u></strong></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>All password policies </td>
<td><p>Not supported.  </p>
<p> </p>
<p>Setting these can prevent the local Skype account from automatically
signing in. </p></td>
</tr>
<tr class="odd">
<td><p>Require encryption of data storage on device. </p>
<p> </p></td>
<td><p>Supported  </p>
<p> </p>
<p>Only use if you have first enabled encryption of data storage on
Teams Rooms. </p></td>
</tr>
<tr class="even">
<td>Firewall </td>
<td><p>Supported  </p>
<p> </p>
<p>Firewall is already a requirement for Teams Rooms </p></td>
</tr>
<tr class="odd">
<td>Trusted Platform Module (TPM) </td>
<td><p>Supported  </p>
<p> </p>
<p>Trusted Platform Module (TPM) is already a requirement for Teams
Rooms. </p></td>
</tr>
<tr class="even">
<td>Antivirus </td>
<td><p>Supported  </p>
<p> </p>
<p>Antivirus (Windows Defender) is already a requirement for Teams
Rooms. </p></td>
</tr>
<tr class="odd">
<td>Antispyware </td>
<td><p>Supported  </p>
<p> </p>
<p>Antispyware (Windows Defender) is already a requirement for Teams
Rooms. </p></td>
</tr>
<tr class="even">
<td>Microsoft Defender Antimalware </td>
<td><p>Supported  </p>
<p> </p>
<p>Microsoft Defender Antimalware is already a requirement for Teams
Rooms. </p></td>
</tr>
<tr class="odd">
<td>Microsoft Defender Antimalware minimum version </td>
<td><p>Not supported.  </p>
<p> </p>
<p>Teams Rooms automatically updates this component so there’s no need
to set compliance policies. </p></td>
</tr>
<tr class="even">
<td>Microsoft Defender Antimalware security intelligence
up-to-date </td>
<td><p>Supported  </p>
<p> </p>
<p>Validate that Microsoft Defender Antimalware is already a requirement
for Teams Rooms. </p></td>
</tr>
<tr class="odd">
<td>Real-time protection </td>
<td><p>Supported </p>
<p> </p>
<p> Real-time protections is already a requirement of Teams
Rooms. </p></td>
</tr>
<tr class="even">
<td><a
href="https://docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-windohttps:/docs.microsoft.com/en-us/mem/intune/protect/compliance-policy-create-windows%22%20/l%20%22microsoft-defender-for-endpointws"><strong><u>Microsoft
Defender for Endpoint</u></strong></a> </td>
<td> </td>
</tr>
<tr class="odd">
<td>Require the device to be at or under the machine risk score. </td>
<td>Supported </td>
</tr>
</tbody>
</table>

#### [Teams Rooms on Android](#tab/mtr-a)

Below is a table of device compliance settings and recommendations for
their use with Teams Rooms.  

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Policy </th>
<th>Notes </th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#microsoft-defender-for-endpoint"><u>Microsoft
Defender for Endpoint</u></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Require the device to be at or under the machine risk score. </td>
<td>Not supported </td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android%22%20/l%20%22device-health"><u>Device
Health</u></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Device managed with device administrator </td>
<td><p>Not supported. </p>
<p> </p>
<p>Teams Android devices are managed with device
administrator. </p></td>
</tr>
<tr class="odd">
<td>Rooted devices </td>
<td>Supported </td>
</tr>
<tr class="even">
<td>Require the device to be at or under the device threat level </td>
<td>Not supported</td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#device-health"><u>Google
Play Protect</u></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Google Play Services is configured </td>
<td><p>Not supported </p>
<p> </p>
<p> Google play is not installed on Teams Android
devices. </p></td>
</tr>
<tr class="odd">
<td>Up-to-date security provider </td>
<td><p>Not supported  </p>
<p> </p>
<p>Google play is not installed on Teams Android devices. </p></td>
</tr>
<tr class="even">
<td>Threat scan on apps </td>
<td><p>Not supported  </p>
<p> </p>
<p>Google play is not installed on Teams Android devices. </p></td>
</tr>
<tr class="odd">
<td>SafetyNet device attestation </td>
<td><p>Not supported  </p>
<p> </p>
<p>Google play is not installed on Teams Android devices. </p></td>
</tr>
<tr class="even">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#device-properties"><u>Device
Properties</u></a> </td>
<td> </td>
</tr>
<tr class="odd">
<td>Operating System Version (minimum, maximum) </td>
<td>Supported </td>
</tr>
<tr class="even">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#system-security"><u>System
Security</u></a> </td>
<td> </td>
</tr>
<tr class="odd">
<td>Encryption </td>
<td> </td>
</tr>
<tr class="even">
<td><p>Require encryption of data storage on device. </p>
<p> </p></td>
<td>Supported </td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#device-security"><u>Device
Security</u></a> </td>
<td> </td>
</tr>
<tr class="even">
<td>Block apps from unknown sources </td>
<td><p>Not supported.  </p>
<p> </p>
<p>Teams Android devices can only have apps installed via Teams admin
center or OEM tools. </p></td>
</tr>
<tr class="odd">
<td>Company Portal app runtime integrity </td>
<td>Supported</td>
</tr>
<tr class="even">
<td>Restricted apps </td>
<td>Not supported.  </td>
</tr>
<tr class="odd">
<td>Block USB debugging on device </td>
<td>Supported</td>
</tr>
<tr class="even">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#all-android-devices"><u>All
Android devices</u></a> </td>
<td> </td>
</tr>
<tr class="odd">
<td>Maximum minutes of inactivity before password is required </td>
<td>Not supported </td>
</tr>
<tr class="even">
<td>Require a password to unlock mobile devices </td>
<td>Not supported </td>
</tr>
<tr class="odd">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#android-10-and-later"><u>Android
10 and later</u></a> </td>
<td> </td>
</tr>
<tr class="even">
<td><a
href="https://docs.microsoft.com/mem/intune/protect/compliance-policy-create-android#android-9-and-earlier-or-samsung-knox"><u>Android
9 and earlier or Samsung Knox</u></a> </td>
<td> </td>
</tr>
<tr class="odd">
<td>Required password type </td>
<td>Not supported </td>
</tr>
</tbody>
</table>

---