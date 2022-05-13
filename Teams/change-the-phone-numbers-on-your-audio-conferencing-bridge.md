---
title: "Change phone numbers on Audio Conferencing bridge"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 6403f6d1-c05a-44ab-a6e0-558000e246f4
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: Learn the steps required to assign a new service phone number to your conference bridge to expand coverage for your users.
---

# Change the phone numbers on your Audio Conferencing bridge

When you buy **Audio Conferencing** licenses, Microsoft is hosting your audio conferencing bridge for your organization. The audio conferencing bridge gives out dial-in phone numbers from different locations so that meeting organizers and participants can use them to join Skype for Business or Microsoft Teams meetings using a phone.
  
In addition to the phone numbers already assigned to your conferencing bridge, you can [get additional service numbers](./getting-service-phone-numbers.md) (toll and toll-free numbers used for audio conferencing) from other locations, and then assign them to the conferencing bridge so you can expand coverage for your users.
  
> [!NOTE]
> To be able to assign/unassign a phone number for a conferencing bridge, the phone number must be a '*service*' number. You can see the type of number it is by navigating to **Voice** > **Phone numbers** in the Microsoft Teams admin center and looking in the **Number Type** column. Microsoft 365 or Office 365 Communications Credits must be set up first in order for users to dial into the bridge on a toll-free number.

## Steps when you are assigning a new service phone number to your conference bridge

> [!NOTE]
> Except where it's called out otherwise, all these steps must be performed in the Microsoft Teams admin center.

### Step 1 - Assign the new phone number to your audio conferencing bridge

1. On the left navigation pane, go to **Voice** > **Phone numbers**.

2. Select the phone number from the list, and click **Edit**.

3. On the **Edit** page, under **Assigned to**, expand the dropdown and then select **Conference bridge** > **Apply**.

### Step 2 - Change the default phone number of your conference bridge (optional)

The default phone number of your conference bridge defines the caller ID that will be used when an outbound call is placed by a participant or the organizer from within a meeting.

Only a service toll number can be set as the default number for your conferencing bridge; **service toll-free numbers can't be set as the default number of your conferencing bridge**. If you are assigning a service toll number and you would like to set it as the new default number for your audio conferencing bridge, perform these steps:

1. On the left navigation pane, go to **Meetings** > **Conference bridges**.

2. Highlight the service toll number that you want to configure as the default.

3. Select **Set as default**.

### Step 3 - Change the default phone numbers that are included in the meeting invites of users (optional)

Refer to [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md).

> [!NOTE]
> You can also set phone numbers by adding them to the *TeamsAudioconferencingpolicy* and assigning the policy to your users. Toll and toll-free phone numbers added to the policy take precedence over the phone numbers set individually for users via the audio conferencing settings pane. If no phone numbers are added to the *Teamsaudioconferencingpolicy*, then the phone number set individually for users via the audio conferencing settings pane will be displayed in Microsoft Teams meeting requests. [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md) has more information.

### Step 4 - Update existing meeting invites of users using the Meeting Migration Service (optional)

For the next two steps, you will need to start Windows PowerShell.
  
If you updated the default phone numbers that are included in the meeting invites for some or all of your users, you can optionally update meeting invites that were already sent to users in your organization before their default phone numbers were changed using the Meeting Migration Service. For additional information, see [Setting up the Meeting Migration Service (MMS)](/SkypeForBusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).
  
- Run the Meeting Migration Service (MMS) for the users who had their default phone numbers changed in Step 2. To do this, run the following command:

```PowerShell
    Start-CsExMeetingMigration user@contoso.com
```

- You can also view the meeting migration status. All meetings would be rescheduled once there are no operations in  *Pending*  or *In-Progress*  state.

```PowerShell
    Get-CsMeetingMigrationStatus -SummaryOnly
```

## Steps when you are unassigning a service phone number for a conferencing bridge

When you unassign a phone number from a conferencing bridge, users won't be able to join any meetings using that phone number anymore. Because the phone number is changing, it's important to update all users who could have a phone number as their default number (if any) and to update their existing meeting invites before the phone number is unassigned from the audio conferencing bridge.

If the phone number is removed without updating the users and their meetings, their existing meeting invites could contain a phone number that won't work for joining their meetings.

For the first three steps, you will need to start Windows PowerShell. To see how to do this, click [Want to know how to manage with Windows PowerShell?](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#about-windows-powershell)

### Step 1 - Update users who have the phone number to be unassigned as one of their default numbers

Replace the default toll or toll-free number for all users who have the number to be unassigned as a default number and start the process of rescheduling their meetings. To do this, run the following command:

```PowerShell
Set-CsOnlineDialInConferencingUserDefaultNumber -FromNumber <Number to be removed> -ToNumber <Number to be set as new default> -NumberType <"Toll" or "Toll-Free"> -RescheduleMeetings
```

 > [!IMPORTANT]
 >You can also change the default toll or toll-free number of users in the Microsoft Teams admin center. However, this won't automatically reschedule their meetings.

 For additional information, see [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md) or [Set the phone numbers included on invites in Skype for Business Online](/SkypeForBusiness/audio-conferencing-in-office-365/set-the-phone-numbers-included-on-invites).

  > [!NOTE]
  > Depending on the size of your organization, this could take some time to complete.

### Step 2 - View meeting migration status using Windows PowerShell

All meetings will be rescheduled once there are no operations in *Pending* or *In-Progress* state.

```PowerShell
Get-CsMeetingMigrationStatus -SummaryOnly
```

For more information about the Meeting Migration Service, see [Setting up the Meeting Migration Service (MMS)](/SkypeForBusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).
  
### Step 3 - Unassign the old phone number from the audio conferencing bridge

Use the Unregister-CsOnlineDialInConferencingServiceNumber cmdlet to unregister a Toll or Toll free number from a conference bridge

```PowerShell
Unregister-CsOnlineDialInConferencingServiceNumber -identity "toll number to be removed" -bridgeId "Conference Bridge ID"
Unregister-CsOnlineDialInConferencingServiceNumber -identity "toll free number to be removed" -bridgeId "Conference Bridge ID"
```

Note:
To find the Conference Bridge ID, run the following PowerShell: Get-CsOnlineDialInConferencingBridge.

   > [!IMPORTANT]
   > After a phone number is unassigned from an audio conferencing bridge, the phone number will no longer be available for users to join new or existing meetings.

### Save time and automate

To save time by automating this process, you can use the [Set-CsOnlineDialInConferencingUser](/powershell/module/skype/Set-CsOnlineDialInConferencingUser) or the **Set-CsOnlineDialInConferencingUserDefaultNumber** cmdlets.

- Use the [Set-CsOnlineDialInConferencingUser](/powershell/module/skype/Set-CsOnlineDialInConferencingUser) cmdlet to change the default toll or toll-free number for specific users.

  - To change the default toll-free number for a user, run:

  ```PowerShell
  Set-CsOnlineDialinConferencingUser -Identity amos.marble@Contoso.com -TollFreeServiceNumber   80045551234
  ```

- Use the **Set-CsOnlineDialInConferencingUserDefaultNumber** cmdlet to change the default toll or toll-free number of users based on their original default number or their location.

    > [!NOTE]
    > To find the BridgeID, use the **Get-CsOnlineDialInConferencingBridge**.

  - To set the default toll-free number for all users without one to 8005551234, run:

  ```PowerShell
  Set-CsOnlineDialInConferencingUserDefaultNumber -FromNumber $null -ToNumber 8005551234 -NumberType TollFree -BridgeId <Bridge Id>
  ```

  - To change the default toll-free number of all users that have 8005551234 as their default toll-free number to 8005551239 and automatically reschedule their meetings, run:

  ```PowerShell
  Set-CsOnlineDialInConferencingUserDefaultNumber -FromNumber 8005551234 -ToNumber 8005551239 NumberType TollFree -BridgeId <Bridge Id> -RescheduleMeetings
  ```

  - To set the default toll-free number of all users located in the U.S. to 8005551234 and automatically reschedule their meetings, run:

  ```PowerShell
  Set-CsOnlineDialInConferencingUserDefaultNumber -Country US -ToNumber 8005551234 -NumberType TollFree -BridgeId <Bridge Id> -RescheduleMeetings
  ```

    > [!NOTE]
    > The location that is used above needs to match the contact information of user(s) that is set in the Microsoft 365 admin center.

## Troubleshooting

### The Unassign button isn't available

You want to Unassign a number but the button isn't available, and if while hovering over it, you are redirected to contact Support with the following message: "Default or shared numbers can´t be unassigned from the bridge. To unassign dedicated toll numbers, please contact support.".

To obtain more information about the bridge(s), run the following Powershell:

```PowerShell
Get-CsOnlineDialInConferencingBridge -Name "Conference Bridge"
```

The result, aside other information like Identity, Name and Region, should also contain the DefaultServiceNumber.

**Example**, to unassign, the DefaultServiceNumber "8005551234"

```PowerShell
Unregister-CsOnlineDialInConferencingServiceNumber -BridgeName "Conference Bridge" -RemoveDefaultServiceNumber 8005551234 
```

## About Windows PowerShell

With Windows PowerShell you can manage users and what they are or are not allowed to do. Windows PowerShell  can help you manage Microsoft 365 or Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, especially when you've got multiple tasks to do. To get started with Windows PowerShell, see these topics:

- [An introduction to Windows PowerShell and Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

- [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:

- [Best ways to manage Microsoft 365 or Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

- [Using Windows PowerShell to manage Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

- [Using Windows PowerShell to do common Skype for Business Online management tasks](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

## Related topics

[Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md)
