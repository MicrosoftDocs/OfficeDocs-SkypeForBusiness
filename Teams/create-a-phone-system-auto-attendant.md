---
title: Set up a Microsoft Teams Auto attendant
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 01/31/2024
ms.topic: article
ms.assetid: 6fc2687c-0abf-43b8-aa54-7c3b2a84b67c
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: 
  - Phone System
description: Learn how to set up and manage Auto attendants in Microsoft Teams.
--- 

# Set up a Microsoft Teams Auto attendant

Auto attendants let people call your organization and navigate a menu system to speak to the right department, Call queue, person, or an operator. You can create Auto attendants for your organization with the Microsoft Teams admin center or with PowerShell.

Be sure you've read [Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md) and followed the [getting started steps](plan-auto-attendant-call-queue.md#getting-started) before you follow the procedures in this article.

Auto attendants can redirect calls, based on callers' input, to one of the following destinations:

- **Operator** - the operator defined for the Auto attendant. Defining an operator is optional. The operator can be defined as any of the other destinations in this list.
- **Person in the organization** - a person in your organization who can receive voice calls. This person can be an online user or a user hosted on-premises using Skype for Business Server.
- **Voice app** - another Auto attendant or a Call queue. Choose the resource account associated with the Auto attendant or Call queue when choosing this destination.
- **Voicemail** - the voice mailbox associated with a Microsoft 365 group that you specify. You can choose if you want voicemail transcriptions and the "Please leave a message after the tone." system prompt.
  - In Microsoft 365 admin center, enable **Let people outside the organization email this team** for the Microsoft 365 group that you specify.
- **External phone number** - any phone number. See [external transfer technical details](create-a-phone-system-auto-attendant.md?tabs=general-info#external-phone-number-transfers---technical-details).
- **Announcement (Audio file)** - Play an audio file. The system plays the announcement, and then returns to the Auto attendant menu. See [Supported audio file formats](plan-auto-attendant-call-queue.md#supported-audio-file-formats).
- **Announcement (Typed)** - Type in a message. Text you want the system to read. You can enter up to 1000 characters. The system plays the announcement, and then returns to the Auto attendant menu.

> [!NOTE]
> When redirecting calls to a **Person in the organization**, that person must be voice enabled. For details on enabling voice, see [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

>[!IMPORTANT]
> While defining an **Operator** is optional, it's recommended.  Auto attendants redirect calls to the operator if there is an error in the Auto attendant configuration due to a user or shared voicemail account being deleted or if the caller doesn't make any selection after listening to the menu three consecutive times.
>
> If an operator isn't defined, the Auto attendant drops the call.
>
> In addition to defining an operator, the operator needs to be one of the configured menu choices.

## What's new for Auto attendants in the past six months

- February 16 - [Support click-to-call web based calling](/azure/communication-services/quickstarts/voice-video-calling/get-started-teams-auto-attendant)

## Steps to create an Auto attendant

The steps to add an Auto attendant are:

1. Set up general information.
1. Set up call flows.
1. Set up dial scope.
1. Set up resource accounts.
1. Set up authorized users.

The steps outlined in the article create Auto attendants using the Teams admin center. For instructions to **create Auto attendants using PowerShell**, see [Creating Auto attendants with PowerShell cmdlets](create-a-phone-system-auto-attendant-via-cmdlets.md).

## Follow these steps to set up your Auto attendant

## [Step 1: General info](#tab/general-info)

## Step 1: Set the Auto attendant's general information

To set up an Auto attendant, in the [Teams admin center](https://admin.teams.microsoft.com/), expand **Voice**, select **Auto attendants**, and then select **Add**.

1. Type a name for the Auto attendant in the box at the top.

1. To designate an operator, specify the destination for calls to the operator. This designation is optional but recommended. Set the **Operator** option to allow callers to break out of the menus and speak to a designated person.

1. Specify the time zone for this Auto attendant. The time zone is used for calculating business hours if you [create a separate call flow for after hours](?tabs=after-hours).

1. Specify a [supported language](create-a-phone-system-auto-attendant-languages.md) for this Auto attendant. This language is used for system-generated voice prompts.

   > [!IMPORTANT]
   > When using *Text to Speech*, the text must be entered in the selected language as the system doesn't perform translation.
   >
   > All words are pronounced in the selected language.

1. Choose if you want to enable voice inputs. When enabled, the name of every menu option becomes a speech-recognition keyword. For example, callers can say "One" to select the menu option mapped to key 1, or they can say "Sales" to select the menu option named "Sales." If you choose a language in Step 4 that doesn't support voice inputs, this option isn't available.

Once you've set your Auto attendant's general info, select **Next**.

## [Step 2: Call flows](#tab/call-flow)

## Step 2: Call flows

## Step 2.1: Set up the basic call flow

### Set a greeting

- If you select **Play an audio file** you can use the **Upload file** button to upload a recorded greeting message saved as audio in .WAV, .MP3, or .WMA format. The recording can be no larger than 5 MB.

- If you select **Type a greeting message**, the system reads the text that you enter (up to 1000 characters) when the Auto attendant answers a call.

### Route the call

- If you select **Disconnect**, the Auto attendant hangs up the call.
- If you select **Redirect call**, you can choose one of the call routing destinations.
- If you select **Play menu options**, you can choose to **Play an audio file** or **Type in a greeting message** and then choose between menu options and directory search.

#### Play menu options

For dialing options, assign the 0-9, \* (asterisk) and \# (pound) keys on the telephone keypad to one of the call routing destinations.

Key mappings don't have to be continuous. It's possible to create a menu with keys 0, 1, and 3 mapped to options, while the number 2 key isn't used.

We recommend mapping the zero key to the operator if you've configured one. If the operator isn't set to any key, the voice command "Operator" is also disabled.

For each menu option, specify the following settings:

- **Dial key** - the key on the telephone keypad to access this option. If voice inputs are available, callers can also say this number to access the option.

- **Voice command** - defines the voice command that a caller can give to access this option, if voice inputs are enabled. It can contain multiple words like "Customer Service" or "Operations and Grounds." For example, the caller can press 2, say "two," or say "Sales" to select the option mapped to the two keys. This text is also rendered by text to speech for the service confirmation prompt, which might be something like "Transferring your call to sales."

- **Redirect to** - the call routing destination used when callers choose this option. If you're redirecting to an Auto attendant or Call queue, choose the resource account associated with it.

### Directory search

If you assign dial keys to destinations, we recommend that you choose **None** for **Directory search**. Dial keys are matched before directory searches are performed. If a caller starts to enter a name or extension using dial keys that are assigned to specific destinations, they're routed to that destination before they finish entering the name or extension. We recommend that you create a separate Auto attendant for directory search and have your main Auto attendant link to it with a dial key.

If you didn't assign dial keys, then choose an option for **Directory search**.

**Dial by name** - If you enable this option, callers can say the user's name or type it on the telephone keypad. Any online user or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with Dial by name.

**Dial by extension** - If you enable this option, callers can connect with users in your organization by dialing their phone extension. Any online user or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with **Dial by extension**. (You can set who is and isn't included in the directory on the [Dial scope](?tabs=dial-scope) page.)

> [!NOTE]
> If you want to use both the **Dial by name** and **Dial by extension** features, you can assign a dial key on your main Auto attendant to reach an Auto attendant enabled for **Dial by name**. Within that Auto attendant, you can assign the 1 key (which has no letters associated with it) to reach the **Dial by extension** Auto attendant.

For more information, see the [Dial and voice reference](dial-voice-reference.md).

Once you've set your basic call flow options, select **Next**.

## Step 2.2: Set up call flow for after hours (optional)

Business hours can be set for each Auto attendant.

- If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default.
- Business hours can be set with breaks in time during the day, and all of the hours that aren't set as business hours are considered after-hours.
- You can set different incoming call-handling options and greetings for after-hours.

Depending on how you've configured your Auto attendants and Call queues, you might only need to specify after-hours call routing for Auto attendants with direct phone numbers.

If you want separate call routing for after-hours callers, then specify your business hours for each day.

1. Next to the weekday in the table, adjust the **Start at** and **End at** times.
1. If needed, select **Add new time** to specify multiple sets of hours for a given day, for example, to specify a lunch break.
1. Choose your call routing options for after hours. The same general call flow options are available for after hours too.

Once you've added your after hours call flow, select **Next**.

## Step 2.3: Set up call flows for holidays (optional)

Your Auto attendant can have a call flow for each [Holiday you've set up](set-up-holidays-in-teams.md). You can add up to 20 holiday sets to each Auto attendant. Each holiday set can contain up to 50 unique date ranges. Holiday dates must be unique across all holiday sets being added to the Auto attendant.

1. On the Holiday call settings page, select **Add**.

1. Type a name for this holiday setting.

1. From the **Holiday** dropdown, choose the holiday you want to use.

1. Choose the type of greeting that you want to use.

1. Choose if you want to **Disconnect**, **Redirect** or **Play menu options** the call.

    1. If you chose to redirect, choose the call routing destination for the call.
    1. If you choose to play menu options, configure the **Play menu options**.

1. Select **Save**.

Repeat the procedure as needed for each additional holiday.

Once you've added all your holiday hours, select **Next**.

## [Step 3: Dial scope](#tab/dial-scope)

## Step 3: Set up dial scope (optional)

The *dial scope* defines which users are available in the directory when a caller uses dial-by-name or dial-by-extension. The default of **All online users** includes all users in your organization that are Online users or hosted on-premises using Skype for Business Server.

You can include or exclude specific users by selecting **Custom user group** under **Include** or **Exclude** and choosing one or more Microsoft 365 groups, distribution lists, or security groups. For example, you might want to exclude executives in your organization from the dialing directory.

If a user is in both lists or if they're hidden from the Exchange GAL, they're excluded from the directory.

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory.

Once you've selected your **Dial scope** options, select **Next**.

## [Step 4: Resource accounts](#tab/resource-accounts)

## Step 4: Assign resource accounts

Before you can create and manage resource accounts, you must do the following:

- [Obtain Microsoft Teams Phone Resource Account licenses](manage-resource-accounts.md#obtain-microsoft-teams-phone-resource-account-licenses)
- [Obtain phone numbers](manage-resource-accounts.md#obtain-phone-numbers)
- [Assign permissions for managing a resource account](manage-resource-accounts.md#assign-permissions-for-managing-a-resource-account)

All Auto attendants must have an associated resource account. All resource accounts must be assigned a [Microsoft Teams Phone Resource Account license](teams-add-on-licensing/virtual-user.md). If you wish, you can assign several resource accounts to an Auto attendant.

For details on how to create resource accounts and ready them for use with auto attendants, see [Manage Teams resource accounts](manage-resource-accounts.md).

Once you've added resource accounts, select **Next**.

## [Step 5: Authorized users](#tab/authorized-users)

## Step 5: Authorized users

**Authorized users** specifies the users who are authorized to make changes to this Auto attendant.  The capabilities that the users have are determined based on the [Teams voice applications policy](./manage-voice-applications-policies.md) that is assigned to the user.

To **add a user** to the authorized users:

1. Select **Add**, search for the user, select **Add**, and then select **Add**.

> [!IMPORTANT]
> A user must have a policy assigned that enables at least one type of configuration change and must also be assigned as an authorized user to at least one Auto attendant or Call queue.
>
> A user won't be able to make any configuration changes if:
>
> - The user has a policy assigned but isn't assigned as an authorized user to at least one Auto attendant or Call queue.
> - The user is assigned as an authorized user to at least one Auto attendant or Call queue but doesn't have a policy assigned.

> [!NOTE]
> A maximum of 15 authorized users can be assigned to the Auto attendant.

For more information, see [Set up authorized users](./aa-cq-authorized-users.md).

---

## Resources for complex scenarios

### External phone number transfers - technical details

Refer to the [Prerequisites](plan-auto-attendant-call-queue.md#prerequisites) in order to allow Auto attendants to transfer calls externally.  In addition,

- For a resource account with a [Calling Plan license](calling-plans-for-office-365.md) or [Operator Connect](operator-connect-plan.md) number, the external transfer phone number must be entered in E.164 format (+[country code][area code][phone number]).

- For a resource account with a Microsoft Teams Phone License and Direct Routing online voice routing policy, the external transfer phone number format is dependant on the [Session Border Controller (SBC)](direct-routing-connect-the-sbc.md) settings.

The outbound phone number that's displayed is determined as follows:

- For Calling Plan and Operator Connect numbers, the original caller's phone number is displayed.
- For Direct Routing numbers, the number sent is based on the P-Asserted-Identity (PAI) setting on the SBC, as follows:
  - If set to Disabled, the original caller's phone number is displayed. Disabled is the default and recommended setting.
  - If set to Enabled, the resource account phone number is displayed.

In a Skype for Business hybrid environment, to transfer an Auto attendant call to the PSTN, create a new on-premises user with call forwarding set to the PSTN number. The user must be enabled for Enterprise Voice and have a voice policy assigned. To learn more, see [Auto attendant call transfer to PSTN](/SkypeForBusiness/plan/exchange-unified-messaging-online-migration-support#auto-attendant-call-transfer-to-pstn).

### Auto Attendant Diagnostic Tool

If you're an administrator, you can use the following diagnostic tool to validate that an Auto attendant is able to receive calls:

1. Select **Run Tests**, which populates the diagnostic in the Microsoft 365 Admin Center.

   > [!div class="nextstepaction"]
   > [Run Tests: Teams Auto Attendant](https://aka.ms/TeamsAADiag)

1. In the Run diagnostic pane, enter the Resource Account in the **Username or Email** field, and then select **Run Tests**.

1. The tests identify tenant, policy, or resource account configurations that are preventing the Auto attendant from receiving calls and also provide steps to fix any problems identified.

## Related articles

[Here's what you get with Teams Phone](./here-s-what-you-get-with-phone-system.md)

[Routing calls with Auto attendants and Call queues](plan-your-call-routing-flow.md)

[Getting service phone numbers](./getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](./country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
