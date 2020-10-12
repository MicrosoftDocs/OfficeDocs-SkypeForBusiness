---
title: "Set up an auto attendant for Microsoft Teams"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.assetid: 6fc2687c-0abf-43b8-aa54-7c3b2a84b67c
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Learn how to set up and test auto attendants for Microsoft Teams."
--- 

# Set up an auto attendant

Auto attendants let people call your organization and navigate a menu system to speak to the right department, call queue, person, or an operator. You can create auto attendants for your organization with the Microsoft Teams admin center, or with PowerShell. 

Be sure you have read [Plan for Teams auto attendants and call queues](plan-auto-attendant-call-queue.md) and followed the [getting started steps](plan-auto-attendant-call-queue.md#getting-started) before you follow the procedures in this article.

Auto attendants can direct calls, based on callers' input, to one of the following destinations:

- **Person in the organization** - a person in your organization who is able to receive voice calls. This can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app** - another auto attendant or a call queue. (Choose the resource account associated with the auto attendant or call queue when choosing this destination.)
- **External phone number** - any phone number. (See [external transfer technical details](create-a-phone-system-auto-attendant.md#external-phone-number-transfers---technical-details)).
- **Voicemail** - the voice mailbox associated with a Microsoft 365 group that you specify.
- **Operator** - the operator defined for the auto attendant. Defining an operator is optional. The operator can be defined as any of the other destinations in this list.

You'll be prompted to choose one of these options at various stages as you set up an auto attendant.

To set up an auto attendant, in the Teams admin center, expand **Voice**, click **Auto attendants**, and then click **Add**.

## General info

![](media/auto-attendant-general-info-page-new.png)

1. Type a name for the auto attendant in the box at the top.

2. If you want to designate an operator, specify the destination for calls to the operator. This is optional (but recommended). You can set the **Operator** option to allow callers to break out of the menus and speak to a designated person.

3. Specify the time zone for this auto attendant. The time zone is used for calculating business hours if you [create a separate call flow for after hours](#call-flow-for-after-hours).

4. Specify a language for this auto attendant. This the language that will be used for system-generated voice prompts.

5. Choose if you want to enable voice inputs. When enabled, the name of every menu option becomes a speech-recognition keyword. For example, callers can say "One" to select the menu option mapped to key 1, or they can say "Sales" to select the menu option named "Sales."

6. Click **Next**.

## Call flow

![](media/auto-attendant-call-flow-greeting-message.png)

Choose if you want to play a greeting when the auto attendant answers a call.

If you select **Play an audio file** you can use the **Upload file** button to upload a recorded greeting message saved as audio in .WAV, .MP3, or .WMA format. The recording can be no larger than 5 MB.

If you select **Type a greeting message** the system will read the text you the text that you type (up to 1000 characters) when the auto attendant answers a call.

![](media/auto-attendant-call-flow-route-call-message.png)

Choose how you want to route the call.

If you select **Disconnect**, the auto attendant will hang up the call.

If you select **Redirect call**, you can choose one of the call routing destinations.

If you select **Play menu options**, you can choose to **Play an audio file** or **Type in a greeting message** and then choose between menu options and directory search.

### Menu options

![](media/auto-attendant-call-flow-menu-options-complete.png)

For dialing options, you can assign the 0-9 keys on the telephone keypad to one of the call routing destinations. (The keys \* (Repeat) and \# (Back) are reserved by the system and can't be reassigned.)

Key mappings don't have to be continuous. It is possible, for example, to create a menu with keys 0, 1, and 3 mapped to options, while the 2 key isn't used.

We recommend mapping the 0 key to the operator if you have configured one. If the operator isn't set to any key, the voice command "Operator" is also disabled. 

For each menu option, specify the following:

- **Dial key** - the key on the telephone keypad to access this option. If voice inputs are available, callers can also say this number to access the option.

- **Voice command** - defines the voice command that a caller can give to access this option, if voice inputs are enabled. It can contain multiple words like "Customer Service" or "Operations and Grounds." For example, the caller can press 2, say "two," or say "Sales" to select the option mapped to the 2 key. This text is also rendered by text to speech for the service confirmation prompt, which might be something like "Transferring your call to sales."

- **Redirect to** - the call routing destination used when callers choose this option. If you are redirecting to an auto attendant or call queue, choose the resource account associated with it.

### Directory search

If you assign dial keys to destinations, we recommend that you choose **None** for **Directory search**. If a caller attempts to dial a name or extension using keys that are assigned to specific destinations, they may be unexpectedly routed to a destination before they finish entering the name or extension. We recommend that you create a separate auto attendant for directory search and have your main auto attendant link to it via a dial key.

If you didn't assign dial keys, then choose an option for **Directory search**.

**Dial by name** - If you enable this option, callers can say the user's name or type it on the telephone keypad. Any online user with a Phone System license, or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with Dial by name. (You can set who is and is not included in the directory on the [Dial scope](#dial-scope) page.)

**Dial by extension** - If you enable this option, callers can connect with users in your organization by dialing their phone extension. Any online user with a Phone System license, or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with **Dial by extension**. (You can set who is and is not included in the directory on the [Dial scope](#dial-scope) page.)

Users you wish to make available for Dial By Extension need to have an extension specified as part of one of the following phone attributes defined in Active Directory or Azure Active Directory (See [Add users individually or in bulk](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) for more information.)

- OfficePhone
- HomePhone
- Mobile/MobilePhone
- TelephoneNumber/PhoneNumber
- OtherTelephone

The required format to enter the extension in the user phone number field is either *+<phone number>ext=<extension>* or *+<phone number>x<extension>*.

You can set the extension in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Azure Active Directory admin center](https://aad.portal.azure.com). It can take up to 12 hours before changes are available to auto attendants and call queues.

> [!NOTE]
> If you want to use both the **Dial by name** and **Dial by extension** features, you can assign a dial key on your main auto attendant to reach an auto attendant enabled for **Dial by name**. Within that auto attendant, you can assign the 1 key (which has no letters associated with it) to reach the **Dial by extension** auto attendant.

Once you have selected a **Directory search** option, click **Next**.

## Call flow for after hours

![](media/auto-attendant-business-hours.png)

Business hours can be set for each auto attendant. If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default. Business hours can be set with breaks in time during the day, and all of the hours that are not set as business hours are considered after-hours. You can set different incoming call-handling options and greetings for after-hours.

Depending on how you have configured your auto attendants and call queues, you may only need to specify after-hours call routing for auto attendants with direct phone numbers.

If you want separate call routing for after-hours callers, then specify your business hours for each day. Click **Add new time** to specify multiple sets of hours for a given day, for example, to specify a lunch break.

Once you have specified your business hours, then choose your call routing options for after hours. The same options are available as for the business hours call routing that you specified above.

Click **Next** when you're done.

## Call flows during holidays

![](media/auto-attendant-holiday-greeting.png)

Your auto attendant can have a call flow for each [Holiday you've set up](set-up-holidays-in-teams.md). You can add up to 20 scheduled holidays to each auto attendant.

1. On the Holiday call settings page, click **Add**.

2. Type a name for this holiday setting.

3. From the **Holiday** dropdown, choose the holiday that you want to use.

4. Choose the type of greeting that you want to use.

    ![](media/auto-attendant-holiday-actions.png)

5. Choose if you want to **Disconnect** or **Redirect** the call.

6. If you chose to redirect, choose the call routing destination for the call.

7. Click **Save**.

![](media/auto-attendant-holiday-call-settings.png)

Repeat the procedure as needed for each additional holiday.

When you've added all your holidays, click **Next**.

## Dial scope

![](media/auto-attendant-dial-scope.png)

The *dial scope* defines which users are available in the directory when a caller uses dial-by-name or dial-by-extension. The default of **All online users** includes all users in your organization that are Online users with a Phone System license or hosted on-premises using Skype for Business Server.

You can include or exclude specific users by selecting **Custom user group** under **Include** or **Exclude** and choosing one or more Microsoft 365 groups, distribution lists, or security groups. For example, you might want to exclude executives in your organization from the dialing directory. (If a user is in both lists, they will be excluded from the directory.)

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory.

When you're done setting the dial scope, click **Next**.

## Resource accounts

All auto attendants must have an associated resource account.  First level auto attendants will need at least one resource account that has an associated service number. If you wish, you can assign several resource accounts to an auto attendant, each with a separate service number.

![](media/auto-attendant-add-resource-account.png)

To add a resource account, click **Add account** and search for the account that you want to add. Click **Add**, and then click **Add**.

![](media/auto-attendant-resource-account-assigned.png)

When you have finished adding service accounts, click **Submit**. This completes the auto attendant configuration.

## External phone number transfers - technical details

When transferring calls to an external phone number, the resource account associated with the auto attendant or call queue must have a phone number and a Microsoft 365 Phone System - Virtual User license. Additionally:

- For a resource account with a Calling Plan number, assign a [Calling Plan](calling-plans-for-office-365.md) license.
- For a resource account with a Direct Routing number, assign an [online voice routing policy](manage-voice-routing-policies.md).

The outbound phone number that's displayed is determined as follows:

  - For Calling Plan numbers, the original caller's phone number is displayed.
  - For Direct Routing numbers, the number sent is based on the P-Asserted-Identity (PAI) setting on the SBC, as follows:
    - If set to Disabled, the original caller's phone number is displayed. This is the default and recommended setting.
    - If set to Enabled, the resource account phone number is displayed.

Transfers between Calling Plan trunks and Direct Routing trunks aren't supported.

In a hybrid environment, to transfer an auto attendant call to the PSTN via Skype for Business PSTN integration, create a new on-premises user with call forwarding set to the PSTN number. The user must be enabled for Enterprise Voice and have a voice policy assigned. To learn more, see [Auto attendant call transfer to PSTN](https://docs.microsoft.com/SkypeForBusiness/plan/exchange-unified-messaging-online-migration-support#auto-attendant-call-transfer-to-pstn).

### Create an auto attendant with PowerShell

You can also use PowerShell to create and set up auto attendants. Here are the cmdlets that you need to manage an auto attendant:

- [New-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/new-csautoattendant?view=skype-ps)  
- [Set-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/set-csautoattendant?view=skype-ps)
- [Get-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/get-csautoattendant?view=skype-ps)
- [Get-CsAutoAttendantHolidays](https://docs.microsoft.com/powershell/module/skype/get-csautoattendantholidays?view=skype-ps)
- [Remove-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/remove-csautoattendant?view=skype-ps)
- [New-CsAutoAttendantMenu](https://docs.microsoft.com/powershell/module/skype/new-csautoattendantmenu?view=skype-ps)
- [New-CsOnlineAudioFile](https://docs.microsoft.com/powershell/module/skype/new-CsOnlineAudioFile?view=skype-ps)
- [New-CsAutoAttendantCallFlow](https://docs.microsoft.com/powershell/module/skype/New-CsAutoAttendantCallFlow?view=skype-ps)
- [Export-CsAutoAttendantHolidays](https://docs.microsoft.com/powershell/module/skype/export-csorganizationalautoattendantholidays?view=skype-ps)
- [New-CsOnlineTimeRange](https://docs.microsoft.com/powershell/module/skype/new-csonlinetimerange?view=skype-ps)
- [New-CsOnlineDateTimeRange](https://docs.microsoft.com/powershell/module/skype/new-csonlinedatetimerange?view=skype-ps)
- [New-CsOnlineSchedule](https://docs.microsoft.com/powershell/module/skype/New-CsOnlineSchedule?view=skype-ps)
- [Get-CsAutoAttendantSupportedTimeZone](https://docs.microsoft.com/powershell/module/skype/Get-CsAutoAttendantSupportedTimeZone?view=skype-ps)
- [New-CsAutoAttendantCallHandlingAssociation](https://docs.microsoft.com/powershell/module/skype/New-CsAutoAttendantCallHandlingAssociation?view=skype-ps)
- [Get-CsAutoAttendantSupportedLanguage](https://docs.microsoft.com/powershell/module/skype/Get-CsAutoAttendantSupportedLanguage?view=skype-ps)
- [Import-CsAutoAttendantHolidays](https://docs.microsoft.com/powershell/module/skype/import-csautoattendantholidays?view=skype-ps)
- [New-CsAutoAttendantCallableEntity](https://docs.microsoft.com/powershell/module/skype/New-CsAutoAttendantCallableEntity?view=skype-ps)


## Related topics

[Here's what you get with Phone System](/MicrosoftTeams/here-s-what-you-get-with-phone-system)

[Getting service phone numbers](/microsoftteams/getting-service-phone-numbers)

[Country and region availability for Audio Conferencing and Calling Plans](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)

[Small business example — Set up an auto attendant](/microsoftteams/tutorial-org-aa) 

[An introduction to Windows PowerShell and Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)
