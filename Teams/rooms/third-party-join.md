---
title: "Enable Teams Rooms devices to join third-party meetings"
ms.author: dstrome
author: dstrome
manager: serdars
ms.reviewer: sohailta
audience: ITPro
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
localization_priority: Normal
description: "This article discusses how to use the recovery tool for Microsoft Teams Rooms, which you would use to bring an out of date system into a supported state."
---

# Enable Teams Rooms devices to join third-party meetings

Microsoft Teams Room enables one touch join for joining third party online meetings. To join third party meetings from conference room, the room should be configured to allow this. Currently, Microsoft Teams Room only support joining Cisco Webex and Zoom<sup>1</sup> meetings. In addition, you may need to make sure your environment doesn't have policies/ rules for third party meeting services that prohibits users to join these meetings from Teams Room devices.

## Allow calendar processing for external meetings

To make sure your organization is setup to receive third party meeting calendar invites and to enable one touch join experience from Team Room devices, make sure to set calendar processing rules for the resource account to allow external meetings and keep the message body for meeting join URL parsing. This can be set on the room account used with Teams Room systems using Exchange PowerShell command [Set-CalendarProcessing](https://docs.microsoft.com/powershell/module/exchange/set-calendarprocessing?view=exchange-ps.)

```powershell
Set-CalendarProcessing [-Identity] -ProcessExternalMeetingMessages $true -DeleteComments $false -DeleteSubject $false
```

Learn more about [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell?view=exchange-ps)

## Office 365 Threat Protection and link rewrite

To enable one touch join experience, meeting join link information from the third-party meeting should be present/ readable in the meeting invite. If your organization uses [ATP Safe Links](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links) feature available in [Office 365 Advanced Threat Protection service](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description?redirectedfrom=MSDN#safe-links), or if you use a third party solution that scans all incoming and outgoing URLs for threats, it may change the meeting join URLs and make the meeting unrecognizable by Teams Room. You should consider adding Third party service domain to the exception list, so meeting join URLs are not rewritten. In Office 365, you can do see using guidance provided at [Set up a custom do-not-rewrite URLs list using ATP Safe Links](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-a-custom-do-not-rewrite-urls-list-with-atp?view=o365-worldwide). For Cisco Webex meetings, the URL may contain `*.webex.com*`, while for Zoom, this may look like `*zoom.us*`, `*zoom.com*` or `*zoomgov.com`". Please check with your partner, customers that use the service on join URLs format and only add specific URLs, domains that you can trust.

## Enabling third party meetings on device

After ensuring that your environment is configured properly, you must configure each device to allow joining third party meeting. Since third party require username and email to join into meetings as guest and may store this data outside of Microsoft data centers, the setting needs to be enabled explicitly to allow you to enter a different username and email than using resource account. You can do this in the device settings or in the XML config file.

### Using device settings

1. On the Microsoft Team Rooms device, go to **More** (**\...**).
2. Select **Settings**, and then enter the device administrator username and password.
3. Go to the **Meetings** tab, turn on **Cisco Webex** and/or **Zoom<sup>1</sup>**
4. Optionally, enter username and email you'd like to use to join third party meetings and then select **Save and exit**.

### Using the XML config file

In your SkypeSettings.xml file, to enable Cisco Webex meetings set the WebExMeetingsEnabled XML element to **True**, as follows.

```xml
<WebExMeetingsEnabled>True</WebExMeetingsEnabled>
```

To enable Zoom<sup>1</sup> meetings set the ZoomMeetingsEnabled XML element to **True**, as follows.

```xml
<ZoomMeetingsEnabled>True</ZoomMeetingsEnabled>
```

You can optionally specify custom username and email info to join third party meetings using these XML elements:

```xml
<UseCustomInfoForThirdPartyMeetings>true</UseCustomInfoForThirdPartyMeetings>

<CustomDisplayNameForThirdPartyMeetings>guestname</CustomDisplayNameForThirdPartyMeetings>

<CustomDisplayEmailForThirdPartyMeetings>guest\@microsoft.com</CustomDisplayEmailForThirdPartyMeetings>
```

Note: If provided values are not valid, Teams Rooms default to use Room account username and email.

> [!NOTE]
> To join Cisco Webex meeting from Teams Room, Cisco meeting should be hosted using Cisco Webex web application version WBS 40.7 and above.

<sup>1</sup> Zoom meetings join is only available to select Microsoft Teams Room customer through Technology Access Program (TAP) and will be generally available with upcoming application version 4.6.
