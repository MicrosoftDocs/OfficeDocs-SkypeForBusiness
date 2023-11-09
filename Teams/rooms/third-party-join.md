---
title: Enable Teams Rooms devices to join third-party meetings
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: naforer
ms.date: 08/22/2023
audience: ITPro
ms.topic: article
ms.service: msteams
ms.subservice: itpro-rooms
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: This article discusses how to configure your organization and Teams Rooms devices to support third-party meeting joining to Cisco Webex and Zoom.
---

# Enable Teams Rooms devices to join third-party meetings

Microsoft Teams Rooms devices support a one-touch experience for joining third-party online meetings, also referred to as Direct Guest Join. When enabled, you can use Teams Rooms to join meetings hosted on Cisco Webex and Zoom just as easily as you can join meetings hosted in Microsoft Teams. Keep in mind that in this case, the experience in Teams Rooms of the third-party online meeting is driven by the third-party online meeting provider.

Supported devices and services:

- Teams Rooms on Windows, all certified models – Zoom, Cisco Webex, BlueJeans by Verizon

- Teams Rooms on Android, all certified models – Zoom, Cisco Webex

    > [!NOTE]
    > Microsoft releases new features for Teams Rooms on Android on a regular basis. However, there can be a delay between when features are released and when they become available on a device. If a feature isn't available on your device, check with your device's manufacturer for information on when it might become available.

> [!NOTE]
> To join a Cisco Webex meeting from a Teams Rooms device, the Cisco meeting needs to be hosted in Webex Meetings Pro using Cisco Webex web application version WBS 40.7 or later.

Before you can join third-party meetings from Teams Rooms, you need to do the following:

1. Configure the Teams Rooms' Exchange Online room mailbox to process invites for third-party meetings.
2. Make sure your organization doesn't have any policies that would prevent you from connecting to third-party meeting services.
3. Configure Teams Rooms to allow third-party meetings.

The following sections show you how to complete each of these steps.

## Step 1: Allow calendar invite processing for third-party meetings

The first thing you need to do to enable a one-touch join experience from Team Rooms is set the calendar processing rules for the device's Exchange Online room mailbox. The room mailbox needs to allow external meetings and keep the message body and subject so it can see the URL needed to join the third-party meeting. To set these room mailbox options using the [Set-CalendarProcessing](/powershell/module/exchange/set-calendarprocessing.) cmdlet, do the following:

1. Connect to Exchange Online PowerShell. For more information, see [Connect to Exchange Online PowerShell with Basic authentication](/powershell/exchange/connect-to-exchange-online-powershell) or [Connect to Exchange Online PowerShell using multi-factor authentication](/powershell/exchange/mfa-connect-to-exchange-online-powershell), depending on your authentication method.

2. Get the User Principal Name (UPN) of the room mailbox if you don't know it by running the following command:

    ```powershell
    Get-Mailbox | Where {$_.RoomMailboxAccountEnabled -eq $True} | Format-Table Name, UserPrincipalName
    ```

3. Find the name of the room mailbox associated with your Teams Rooms device and make note of its UPN.

4. After you find the room mailbox's UPN, run the following command. Replace `<UserPrincipalName>` with the room mailbox's UPN:

    ```powershell
    Set-CalendarProcessing <UserPrincipalName> -ProcessExternalMeetingMessages $True -DeleteComments $False -DeleteSubject $False
    ```

Learn more about [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell).

## Step 2: Configure Office 365 Threat Protection and link rewrite

To enable the one-touch join experience, meeting join link information from the third-party meeting needs to be present and readable in the meeting invite. If your organization uses the [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/safe-links) safe links feature, or if you use a third-party solution that scans all incoming and outgoing URLs for threats, it may change the meeting join URLs and make the meeting unrecognizable by the Teams Rooms device. To make sure this doesn't happen, you need to add the third-party meeting service's URLs to the Defender for [Office 365 Safe Links **Do not rewrite** list](/microsoft-365/security/office-365-security/safe-links) or the third-party URL rewrite exception list.

 If you use a third-party solution, refer to the instructions for that solution to add URLs to its URL rewrite exception list.

Here are some example entries that you may need to add to your Defender for Office 365 Safe Links *Do not rewrite* list or third-party URL rewrite exception list:

- **Cisco Webex** `*.webex.com/*`
- **Zoom** `*.zoom.us/*`, `*.zoom.com/*`, `*.zoomgov.com/*`
- **BlueJeans** `*.bluejeans.com/*`

For a complete list of URLs to add to your Defender for Office 365 Safe Links *Do not rewrite* list or third-party URL rewrite exception list, contact the third-party meeting service provider you want to accept meeting invites from.

> [!CAUTION]
> Only add URLs that you trust to your Microsoft Defender for Office 365 Safe Links *Do not rewrite* list or third-party URL rewrite exception list.

## Step 3a: Enable third-party meetings on Teams Rooms on Windows

The last step you need to do is allow Teams Rooms to join third-party meetings. Third-party meetings require a username and email address to join them. If the username and email address that you need to use is different than the device's room mailbox, you need to add them to your device. You can do this in the Teams Rooms settings or in the XML config file. You can do this in the Teams Rooms settings on any capable Teams Rooms or in the XML config file for Teams Rooms on Windows.

### Use device settings

To configure Teams Rooms on Windows using the touchscreen console, do the following:

1. On the Microsoft Teams Rooms console, select **More**.
2. Select **Settings**, and then enter the device administrator username and password.
3. Go to the **Meetings** tab and select a third-party meeting provider you wish to enable (e.g., **Webex**, **Zoom**, etc.).

:::image type="content" source="../media/use-device-settings.png" alt-text="Turning on and off third party providers.":::

1. If you want to join meetings with the username and email address associated with the room mailbox, select **Join with room info**.
1. If you want to join meetings with an alternate username and email address, select **Join with custom info** and enter username and email address you'd like to use.
1. Select **Save and exit**. Your device will restart.

     ![Meetings](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/assets/63427703/6503b72c-4482-4ec4-9492-610503d02c36)

### Use the SkypeSettings.xml configuration file

The following settings can be added to the `SkypeSettings.xml` file located in `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState`. For more information about the `SkypeSettings.xml` file, see [Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md).

To enable Zoom meetings, set the `ZoomMeetingsEnabled` XML element to **True**, as follows.

```xml
<ZoomMeetingsEnabled>True</ZoomMeetingsEnabled>
```

To enable Cisco Webex meetings, set the `WebexMeetingsEnabled` XML element to **True**, as follows.

```xml
<WebexMeetingsEnabled>True</WebexMeetingsEnabled>
```

To enable BlueJeans meetings, set the `BlueJeansMeetingsEnabled` XML element to **True**, as follows.

```xml
<BlueJeansMeetingsEnabled>True</BlueJeansMeetingsEnabled>
```

You can optionally specify a custom username and email address to join third-party meetings using the following XML elements. If the values you provide aren't valid, the Teams Rooms device will default to use room mailbox username and email address.

```xml
<UseCustomInfoForThirdPartyMeetings>true</UseCustomInfoForThirdPartyMeetings>

<CustomDisplayNameForThirdPartyMeetings>guestname</CustomDisplayNameForThirdPartyMeetings>

<CustomDisplayEmailForThirdPartyMeetings>guest@contoso.com</CustomDisplayEmailForThirdPartyMeetings>
```

## Step 3b: Enable third-party meetings on Teams Rooms on Android

To configure Teams Rooms on Android using the touchscreen console or front-of-room display, do the following:

1. On the Microsoft Teams Rooms console or front-of-room display, select **More**.
2. Select **Settings**, and:
   - If using a personal account (for example, an account with an E5 license), choose **Meetings** option.
   - If using a shared account (for example, a resource account with a Teams Rooms license), choose **Device settings**, locate **Teams Admin settings**, enter an admin password, and choose a **Meetings** option.

      > [!NOTE]
      > Some device manufacturers require an admin password before **Device settings** can be accessed.

    ![Meetings settings for MTR on Android](..\media\step-3b-enable-third-party-meetings-on-teams-rooms-on-android.png)

3. Select the third-party meeting provider you want to enable.
4. If you want to join meetings with a custom username and email address, select **Join with custom name and email**. To update custom personal info, press **Edit custom info** and input your preferred name and email address.