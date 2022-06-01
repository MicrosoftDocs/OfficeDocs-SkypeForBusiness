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
ms.localizationpriority: medium
description: "This article discusses how to configure your organization and Teams Rooms devices to support third-party meeting joining to Cisco WebEx and Zoom."
---

# Enable Teams Rooms devices to join third-party meetings

> [!NOTE]
> This feature is currently only available on Teams Rooms on Windows.

Microsoft Teams Rooms devices support a one-touch experience for joining third-party online meetings, also referred to as Direct Guest Join. When enabled, you can use Teams Rooms to join meetings hosted on Cisco WebEx and Zoom just as easily as you can join meetings hosted in Microsoft Teams.

Before you can join third-party meetings from Teams Rooms, you need to do the following:

1. Configure the Teams Rooms' Exchange Online room mailbox to process invites for third-party meetings.
2. Make sure your organization doesn't have any policies that would prevent you from connecting to third-party meeting services.
3. Configure Teams Rooms to allow third-party meetings.

The following sections show you how to do each of these steps.

## Step 1: Allow calendar invite processing for third-party meetings

The first thing you need to do to enable a one-touch join experience from Team Rooms is set the calendar processing rules for the device's Exchange Online room mailbox. The room mailbox needs to allow external meetings and keep the message body and subject so it can see the URL needed to join the third-party meeting. To set these room mailbox options using the [Set-CalendarProcessing](/powershell/module/exchange/set-calendarprocessing?view=exchange-ps.) cmdlet, do the following:

1. Connect to Exchange Online PowerShell. For more information, see [Connect to Exchange Online PowerShell with Basic authentication](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps) or [Connect to Exchange Online PowerShell using multi-factor authentication](/powershell/exchange/mfa-connect-to-exchange-online-powershell?view=exchange-ps), depending on your authentication method.

2. Get the User Principal Name (UPN) of the room mailbox if you don't know it by running the following command:

    ```powershell
    Get-Mailbox | Where {$_.RoomMailboxAccountEnabled -eq $True} | Format-Table Name, UserPrincipalName
    ```
    
3. Find the name of the room mailbox associated with your Teams Rooms device and make note of its UPN.

4. After you find the room mailbox's UPN, run the following command. Replace `<UserPrincipalName>` with the room mailbox's UPN:

    ```powershell
    Set-CalendarProcessing <UserPrincipalName> -ProcessExternalMeetingMessages $True -DeleteComments $False -DeleteSubject $False
    ```

Learn more about [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell?view=exchange-ps).

## Step 2: Configure Office 365 Threat Protection and link rewrite

To enable the one-touch join experience, meeting join link information from the third-party meeting needs to be present and readable in the meeting invite. If your organization uses the [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/safe-links?view=o365-worldwide) safe links feature, or if you use a third-party solution that scans all incoming and outgoing URLs for threats, it may change the meeting join URLs and make the meeting unrecognizable by the Teams Rooms device. To make sure this doesn't happen, you need to add the third-party meeting service's URLs to the Defender for [Office 365 Safe Links **Do not rewrite** list](/microsoft-365/security/office-365-security/safe-links?view=o365-worldwide) or the third-party URL rewrite exception list.

 If you use a third-party solution, refer to the instructions for that solution to add URLs to its URL rewrite exception list.

Here are some example entries that you may need to add to your Defender for Office 365 Safe Links *Do not rewrite* list or third-party URL rewrite exception list:

- **Cisco WebEx** `*.webex.com/*`
- **Zoom** `*.zoom.us/*`, `*.zoom.com/*`, `*.zoomgov.com/*`

For a complete list of URLs to add to your Defender for Office 365 Safe Links *Do not rewrite* list or third-party URL rewrite exception list, contact the third-party meeting service provider you want to accept meeting invites from.

> [!CAUTION]
> Only add URLs that you trust to your Microsoft Defender for Office 365 Safe Links *Do not rewrite* list or third-party URL rewrite exception list.

## Step 3: Enable third-party meetings on Teams Rooms

The last step you need to do is allow Teams Rooms to join third-party meetings. Third-party meetings require a username and email address to join them. If the username and email address that you need to use is different than the device's room mailbox, you need to add them to your device. You can do this in the Teams Rooms settings or in the XML config file.

### Use device settings

To configure Teams Rooms using the touchscreen console, do the following:

1. On the Microsoft Teams Rooms console, select **More ...**.
2. Select **Settings**, and then enter the device administrator username and password.
3. Go to the **Meetings** tab and select **Cisco WebEx**, **Zoom**, or both.
4. If you want to join meetings with the username and email address associated with the room mailbox, select **Join with room info**.
5. If you want to join meetings with an alternate username and email address, select **Join with custom info** and enter username and email address you'd like to use.
6. Select **Save and exit**. Your device will restart.

### Use the SkypeSettings.xml configuration file

The following settings can be added to the `SkypeSettings.xml` file located in `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState`. For more information about the `SkypeSettings.xml` file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

To enable Cisco WebEx meetings, set the `WebExMeetingsEnabled` XML element to **True**, as follows.

```xml
<WebExMeetingsEnabled>True</WebExMeetingsEnabled>
```

To enable Zoom meetings, set the `ZoomMeetingsEnabled` XML element to **True**, as follows.

```xml
<ZoomMeetingsEnabled>True</ZoomMeetingsEnabled>
```

You can optionally specify a custom username and email address to join third-party meetings using the following XML elements. If the values you provide aren't valid, the Teams Rooms device will default to use room mailbox username and email address.

```xml
<UseCustomInfoForThirdPartyMeetings>true</UseCustomInfoForThirdPartyMeetings>

<CustomDisplayNameForThirdPartyMeetings>guestname</CustomDisplayNameForThirdPartyMeetings>

<CustomDisplayEmailForThirdPartyMeetings>guest@contoso.com</CustomDisplayEmailForThirdPartyMeetings>
```

> [!NOTE]
> To join a Cisco WebEx meeting from a Teams Rooms device, the Cisco meeting needs to be hosted in WebEx Meetings Pro using Cisco WebEx web application version WBS 40.7 or later. 
