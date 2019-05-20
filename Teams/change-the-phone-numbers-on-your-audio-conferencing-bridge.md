---
title: "Change the phone numbers on your Audio Conferencing bridge"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.assetid: 6403f6d1-c05a-44ab-a6e0-558000e246f4
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-voice
audience: Admin
appliesto:
- Skype for Business
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "When you buy Audio Conferencing licenses, Microsoft is hosting your audio conferencing bridge for your organization. The audio conferencing bridge gives out dial-in phone numbers from different locations so meeting organizers and participants can use them to join Skype for Business or Microsoft Teams meetings using a phone."
---

# Change the phone numbers on your Audio Conferencing bridge

When you buy **Audio Conferencing** licenses, Microsoft is hosting your audio conferencing bridge for your organization. The audio conferencing bridge gives out dial-in phone numbers from different locations so that meeting organizers and participants can use them to join Skype for Business or Microsoft Teams meetings using a phone.
  
In addition to the phone numbers already assigned to your conferencing bridge, you can [get additional service numbers](/SkypeForBusiness/what-is-phone-system-in-office-365/getting-service-phone-numbers) (toll and toll-free numbers used for audio conferencing) from other locations, and then assign them to the conferencing bridge so you can expand coverage for your users.
  
> [!NOTE]
> To be able to assign/unassign a phone number for a conferencing bridge, the phone number must be a '*service*' number. You can see the type of number it is by navigating to **Voice** > **Phone numbers** in the legacy portal and looking in the **Number Type** column. Office 365 Communications Credits must be set up first in order for users to dial into the bridge on a toll free number.

## Steps when you are assigning a new service phone number to your conference bridge

### Step 1 - Assign the new phone number to your audio conferencing bridge

1. Sign in to Office 365 with your work account.

2. Go to **Microsoft 365 admin center** > **Admin centers** > **Teams & Skype** > **Legacy portal** > **Voice** > **Phone numbers**.

3. Select the phone number from the list, and in the Action pane, click **Assign**.

4. On the **Assign** page, click **Save**.

### Step 2 - Change the default phone number of your conference bridge (optional)

The default phone number of your conference bridge defines the caller ID that will be used when an outbound call is placed by a participant or the organizer from within a meeting.

Only a service toll number can be set as the default number for your conferencing bridge; **service toll-free numbers can't be set as the default number of your conferencing bridge**. If you are assigning a service toll number and you would like to set it as the new default number for your audio conferencing bridge, perform these steps:

1. Sign in to Office 365 with your work account.

2. Go to **Microsoft 365 admin center** > **Admin centers** > **Teams & Skype** > **Meetings** > **Conference Bridges**.

3. Highlight the service toll number that you want to configure as the default.

4. Select **Set as default**.
 
### Step 3 - Change the default phone numbers that are included in the meeting invites of users (optional)

The default phone numbers of a user are the ones that are included on their meeting invites when they schedule a meeting. For more information, including how the defaul phone numbers are assigned for new users, see [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md) or [Set the phone numbers included on invites in Skype for Business Online](/SkypeForBusiness/audio-conferencing-in-office-365/set-the-phone-numbers-included-on-invites).
  
1. Sign in to Office 365 with your work or school account.

2. Go to the **Microsoft 365 admin center** > **Admin centers** > **Teams & Skype** > **Legacy portal** > **Audio conferencing** > **Users**, and select the users on the list.

3. Click **Edit** in the action pane.

4. Under **Default toll number** or **Default toll-free number**, select the number in the list and click **Save**.

After the changes have been saved, the new default phone numbers will be included on the meeting invites of organizers the next time they schedule a new meeting.

### Step 4 - Update existing meeting invites of users using the Meeting Migration Service (optional)

For the next two steps, you will need to start Windows PowerShell.
  
If you updated the default phone numbers that are inlcuded in the meeting invites for some or all of your users, you can optionally update meeting invites that were already sent to users in your organization before their default phone numbers were changed using the Meeting Migration Service. For additional information, see [Setting up the Meeting Migration Service (MMS)](/SkypeForBusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).
  
- Run the Meeting Migration Service (MMS) for the users who had their default phone numbers changed in Step 2. To do this, run the following command:

```
	Start-CsExMeetingMigration user@contoso.com
```

- You can also view the meeting migration status. All meetings would be rescheduled once there are no operations in  *Pending*  or *In-Progress*  state.

```
	Get-CsMeetingMigrationStatus -SummaryOnly
```

## Steps when you are unassigning a service phone number for a conferencing bridge


When you unassign a phone number from a conferencing bridge, users won't be able to join any meetings using that phone number anymore. Because the phone number is changing, it's important to update all users who could have a phone number as their default number (if any) and to update their existing meeting invites before the phone number is unassigned from the audio conferencing bridge.

If the phone number is removed without updating the users and their meetings, their existing meeting invites could contain a phone number that won't work for joining their meetings.

For the first three steps, you will need to start Windows PowerShell. To see how to do this, click [Want to know how to manage with Windows PowerShell?](change-the-phone-numbers-on-your-audio-conferencing-bridge.md#bkPowerShell)

### Step 1 - Update users who have the phone number to be unassigned as one of their default numbers

Replace the default toll or toll-free number for all users who have the number to be unassigned as a default number and start the process of rescheduling their meetings. To do this, run the following command:

```
Set-CsOnlineDialInConferencingUserDefaultNumber -FromNumber <Number to be removed> -ToNumber <Number to be set as new default> -NumberType <"Toll" or "Toll-Free"> -RescheduleMeetings
```
 > [!IMPORTANT] 
 >You can also change the default toll or toll-free number of users in the Skype for Business admin center. However, this won't automatically reschedule their meetings. 
 
 For additional information, see [Set the phone numbers included on invites in Microsoft Teams](set-the-phone-numbers-included-on-invites-in-teams.md) or [Set the phone numbers included on invites in Skype for Business Online](/SkypeForBusiness/audio-conferencing-in-office-365/set-the-phone-numbers-included-on-invites).

  > [!NOTE]
  > Depending on the size of your organization, this could take some time to complete.

### Step 2 - View meeting migration status using Windows PowerShell

All meetings will be rescheduled once there are no operations in *Pending* or *In-Progress* state.

```
Get-CsMeetingMigrationStatus -SummaryOnly
```

For more information about the Meeting Migration Service, see [Setting up the Meeting Migration Service (MMS)](/SkypeForBusiness/audio-conferencing-in-office-365/setting-up-the-meeting-migration-service-mms).
  
### Step 3 - Unassign the old phone number from the audio conferencing bridge

1. Sign in to Office 365 with your work or school account.

2. Go to the **Microsoft 365 admin center** > **Admin centers** > **Teams & Skype** > **Legacy portal** > **Voice** > **Phone numbers**.

3. If the phone number is a toll-free number, select the phone number from the list, and in the Action pane, click **Unassign**. If the phone number is a toll-number, please contact [Microsoft support](https://go.microsoft.com/fwlink/?linkid=2091806) to have the phone number unassigned.

4. If the phone number is a toll-fre number, click **Yes** in the confirmation window.

   > [!IMPORTANT]
   > After a phone number is unassigned from an audio conferencing bridge, the phone number will no longer be available for users to join new or existing meetings.

## Want to know how to manage with Windows PowerShell?
<a name="bkPowerShell"> </a>

### To verify that Windows PowerShell is ready to go

 These steps check that you are running Windows PowerShell version 3.0 or higher.

1. Type **Start Menu** > **Windows PowerShell**.

2. Type _Get-Host_ in the **Windows PowerShell** window to check the version.

3. If you don't have version 3.0 or higher, you need to download and install updates to Windows PowerShell. See [Windows Management Framework 4.0 ](https://go.microsoft.com/fwlink/?LinkId=716845) to download and update Windows PowerShell to version 4.0.
Restart your computer when you are prompted.

4. You also need to install the Windows PowerShell module for Skype for Business Online that enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module is supported only on 64-bit computers and can be downloaded from the Microsoft Download Center at [Windows PowerShell Module for Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=294688).
Restart your computer if you are prompted.

If you need to know more, see [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/library/dn568015.aspx).

### To start Windows PowerShell

 **Start a Windows PowerShell session**

1. From the **Start Menu** > **Windows PowerShell**.

2. In the **Windows PowerShell** window, connect to your Office 365 organization by running:

>
  ```
    Import-Module "C:\\Program Files\\Common Files\\Skype for Business Online\\Modules\\SkypeOnlineConnector\\SkypeOnlineConnector.psd1"
    $credential = Get-Credential
    $session = New-CsOnlineSession -Credential $credential
    Import-PSSession $session
  ```

> [!NOTE]
> You only have to run the **Import-Module** command the first time you use the Skype for Business Online Windows PowerShell module.
If you want more information about starting Windows PowerShell, see [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/library/dn568015.aspx) or [Connecting to Skype for Business Online by using Windows PowerShell](https://technet.microsoft.com/library/dn362795%28v=ocs.15%29.aspx).

### Save time and automate

To save time by automating this process, you can use the [Set-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617688) or the **Set-CsOnlineDialInConferencingUserDefaultNumber** cmdlets.

- Use the [Set-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617688) cmdlet to change the default toll or toll-free number for specific users.

  - To change the default toll-free number for a user, run:

  ```
  Set-CsOnlineDialinConferencingUser -Identity amos.marble@Contoso.com -TollFreeServiceNumber   80045551234
  ```

- Use the **Set-CsOnlineDialInConferencingUserDefaultNumber** cmdlet to change the default toll or toll-free number of users based on their original default number or their location.

    > [!NOTE]
    > To find the BridgeID, use the **Get-CsOnlineDialInConferencingBridge**.

  - To set the default toll-free number for all users without one to 8005551234, run:

  ```
  Set-CsOnlineDialInConferencingUserDefaultNumber -FromNumber $null -ToNumber 8005551234 -NumberType TollFree -BridgeId <Bridge Id>
  ```

  - To change the default toll-free number of all users that have 8005551234 as their default toll-free number to 8005551239 and automatically reschedule their meetings, run:

  ```
  Set-CsOnlineDialInConferencingUserDefaultNumber -FromNumber 8005551234 -ToNumber 8005551239 NumberType TollFree -BridgeId <Bridge Id> -RescheduleMeetings
  ```

  - To set the default toll-free number of all users located in the U.S. to 8005551234 and automatically reschedule their meetings, run:

  ```
  Set-CsOnlineDialInConferencingUserDefaultNumber -Country US -ToNumber 8005551234 -NumberType TollFree -BridgeId <Bridge Id> -RescheduleMeetings
  ```

    > [!NOTE]
    > The location that is used above needs to match the contact information of user(s) that is set in the Microsoft 365 admin center.

## Troubleshooting

**Unassign button is greyed-out**

You want to Unassign a number but the button is greyed-out and if while hoovering over it, you are redirected to contact Support with the following message _"Default or shared numbers can´t be unassigned from the bridge. To unassign dedicated toll numbers, please contact support._".

To obtain more information about the bridge(s), run the following Powershell :
```
Get-CsOnlineDialInConferencingBridge -Name "Conference Bridge"
```

The result, aside other information like Identity, Name and Region, should also contain the DefaultServiceNumber.

**Example**, to unassign, the DefaultServiceNumber "8005551234"
```
Unregister-CsOnlineDialInConferencingServiceNumber -BridgeName “Conference Bridge” -RemoveDefaultServiceNumber 8005551234 
```

## About Windows PowerShell

With Windows PowerShell you can manage users and what they are or are not allowed to do. Windows PowerShell  can help you manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, especially when you've got multiple tasks to do. To get started with Windows PowerShell, see these topics:

  - [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)

  - [Why you need to use Office 365 PowerShell](https://go.microsoft.com/fwlink/?LinkId=525041)

Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:

  - [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)

  - [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)

  - [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)

## Related topics
[Change the settings for an Audio Conferencing bridge](change-the-settings-for-an-audio-conferencing-bridge.md)
