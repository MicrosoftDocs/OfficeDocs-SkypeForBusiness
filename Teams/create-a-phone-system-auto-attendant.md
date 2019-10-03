---
title: "Set up a Cloud auto attendant"
ms.author: jambirk
author: jambirk
manager: serdars
ms.reviewer: waseemh
ms.topic: article
ms.assetid: 6fc2687c-0abf-43b8-aa54-7c3b2a84b67c
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
- Phone System
description: "Learn how to set up and test Cloud auto attendants for Microsoft Teams."
---

# Set up a Cloud auto attendant

Auto attendants let people call your organization and navigate a menu system to speak to the right department, call queue, person, or an operator. You can create auto attendants for your organization with the Microsoft Teams admin center, or with Powershell. To create an auto attendant, go to **Voice** in the left navigation, and then select **Auto attendants** > **Add new**.

If you want to learn more about auto attendants, see [What are Cloud auto attendants?](/microsoftteams/what-are-phone-system-auto-attendants)

> [!NOTE]
> This article applies to both Microsoft Teams and Skype for Business Online.

Phone numbers are not directly assigned to the auto attendant, but rather to a [resource account](manage-resource-accounts.md) that is associated to the auto attendant.

Auto attendant implementations often involve several auto attendants. A *first-level* auto attendant usually has a resource account with an assigned phone number. A nested auto attendant is used as a second-level menu that the *first-level* auto attendant connects  as call to. A *nested* auto attendant isn't required to  have a phone number assigned to its resource account.

## Step 1 — Get started

- An auto attendant is required to have an associated resource account. See [Manage resource accounts in Teams](manage-resource-accounts.md) for details on resource accounts and all licenses required. When you create a new auto attendant in Teams after November 1st, 2019, the required auto attendant is automatically created and linked with the new auto attendant.

> [!TIP]
> To redirect calls to an operator or a menu option that is an Online user with a Phone System license, you will need to enable them for Enterprise Voice. See [Assign Skype for Business licenses](/skypeforbusiness/skype-for-business-and-microsoft-teams-add-on-licensing/assign-skype-for-business-and-microsoft-teams-licenses) or [Assign Microsoft Teams licenses](assign-teams-licenses.md). You can also use Windows PowerShell. For example, run: `Set-CsUser -identity "Amos Marble" -EnterpriseVoiceEnabled $true`

## Step 2 — Create auto attendants

> [!IMPORTANT]
> Every auto attendant is required to have an associated [resource account](manage-resource-accounts.md). You must create the resource account first, then you can associate it to the auto attendant.

### With the Microsoft Teams admin center

In the **Microsoft Teams admin center**, click   **Voice** > **Auto attendants**, then click **+ New**:

#### General info page

![Screenshot of the My Auto Attendant page](media/edacec94-9384-4a87-be0a-5c49a151287e.png)

* * *

![Icon of the number 1, a callout in the previous screenshot](media/teamscallout1.png)

**Name** Enter a display name for your auto attendant. The name is required and can contain up to 64 characters, including spaces. The **Name** is listed in a column on the **Auto attendants** tab.

* * *

<a name="phonenumber"> </a>

<!-- 
![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)

**Phone number (optional)** Enter the service phone number you want to assign to the new resource account this wizard creates and links to the new auto attendant. If you intend this auto attendant to be a nested auto attendant, it doesn't need a phone number. You can add one if for some reason you require several ways to connect to the auto attendant system.

> [!NOTE]
> Auto attendants created after November 1st, 2019 also create a new [resource account](manage-resource-accounts.md) that is associated with the auto attendant. If a phone number is applied to the auto attendant's resource account,  a Phone System - Virtual user license is applied to the resource account if one is available.

* * * -->

![Icon of the number 3,  a callout in the previous screenshot](media/teamscallout3.png)

<a name="timezone"> </a> 

**Time zone** You must set the time zone for your auto attendant. The setting can be the same as the time zone of the main address listed for your organization, or a different time zone. Each auto attendant can have a different time zone. The business hours set for the auto attendant are based on this time zone.

* * *

![Icon of the number 4,  a callout in the previous screenshot](media/teamscallout4.png)

<a name="operator"> </a>

**Operator** This is optional (but recommended). You can set the **Operator** option to allow callers to break out of the menus and speak to a designated person.

The 0 key is assigned to Operator by default.

If you set an Operator, tell people who call about the option in **Edit menu options** on the **Business hours call handling** page. If you set an operator on your auto attendant, you enter the corresponding prompt text in the **Callers will hear** box or change your audio file to include this option. For example, "For the Operator, press zero."

You have several ways to set the Operator:

- **No operator** disables the "Operator" and "Press 0" options.
- **Person in your organization** with a Phone System license that is enabled for Enterprise Voice or assigned Calling Plans in Office 365. You can also set it up so the caller is sent to voicemail. To send a caller to voicemail, select **Person in your organization** and set that account's settings to send calls directly to voicemail.

     > [!Note]
     > **Person in your organization** can be an Online user or a user hosted on-premises using Skype for Business Server.

- **Auto attendant** Select the name of the resource account linked to an auto attendant that has already been created. Callers that request an operator are redirected there.
- **Call queue** Select the name of the resource account linked to a call queue that has already been created. Callers that request an operator are redirected there.

![Icon of the number 5,  a callout in the previous screenshot](media/teamscallout5.png)

<a name="language"> </a>

**Language** Select the language that you want to use for your auto attendant. The auto attendant uses that language with callers, and all system prompts are played in this language.

 * * *

![Icon of the number 6,  a callout in the previous screenshot](media/teamscallout6.png)

**Enable voice inputs** Speech recognition is available if this option is selected. Callers can use voice input in the  [language you set](set-auto-attendant-languages-for-audio-conferencing-in-teams.md). If you want to only let people use their phone keypad, you can disable speech recognition by setting it to off.

* * *  

When you finish with your selections, click **Next**.

#### Call flow

> [!TIP]
> You can choose to set up a custom business hours schedule, with different call flow behaviors during and after business hours. To set a custome schedule, set the optional [Call flow for after hours](#call-flow-for-after-hours). By default, an auto attendant uses business hours call flows.

You can set up customized greetings, prompts, and menus that people hear when they reach your auto attendant.

![Screenshot: Business hours call handling page Greeting section](media/2a33b1f7-d362-47a7-bf32-ef702bc878e8.png)

* * *

![Icon of the number 1,  a callout in the previous screenshot](media/teamscallout1.png)

<a name="greetingsandrouting"> </a>

**First play a greeting message** A greeting is optional and can be set to **On** or **Off**. If you select **Off**, the caller doesn't hear a message or greeting before the call is handled by one of the actions you select later. You can also upload an audio file (in .wav, mp3 or .wma formats), or create a custom greeting using Text-to-Speech.

> [!NOTE]
> A greeting is most valuable for a first-level auto attendant. A nested auto attendant often doesn't need a greeting.

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)

 **Use recorded greeting** This option lets you use a built-in sound recording app to **Record** the greeting and then **Upload** your audio file (in a .wav, .mp3 or .wma format). You can also **Upload** a professionally recorded greeting message.

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)
 **Write your greeting** If you choose this option, enter the text you want the system to read (up to 1000 characters) in the field provided. For example, enter "Welcome to Contoso. Your call is important to us." Output is created by text-to-voice software.

* * *

You can select what happens next to calls from the following actions:

![Icon of the number 4,  a callout in the previous screenshot](media/teamscallout4.png)

 **Then route the call**  can be set to **On** or **Off**. If you select **Off**, the caller is disconnected after the greeting plays. If you select **On**, there are a number of options:

![Icon of the number 5,  a callout in the previous screenshot](media/teamscallout5.png) 

<a name="redirectcalls"> </a>

**Redirect call to** sends the caller to the chosen destination without choosing from options.

- **Person in your organization** The account you choose must have a Phone System license enabled for Enterprise Voice or have an assigned Calling Plan in Office 365. You can set it up so the caller can be sent to voicemail: select **Person in your organization** and set that account to have calls forwarded directly to voicemail.

> [!Note]
> **Person in your organization** can be an Online user or a user hosted on-premises using Skype for Business Server.

- **Auto attendant** Select the name of an existing auto attendant.
- **Call queue** Select the name of an auto attendant that has already been created.
- **External phone number** routes the caller to a phone number outside your local system.
- **Operator** directs the call to a user you designate as an Operator. If you haven't previously set up an operator, an option to create one now shows up. The 0 key is assigned to Operator by default. Options for setting an Operator are:

  - **No operator** disables the "Operator" and "Press 0" options.
  - **Person in your organization** can be an Online user or a user hosted on-premises using Skype for Business Server. They must have a Phone System license that is enabled for Enterprise Voice or assigned Calling Plans in Office 365. Search for the operator in the **Destination for your operator** field.
  - **Auto attendant** lets you choose the name of an existing auto attendant.
  - **Call queue** lets you select an existing call queue.
  - **Group Voicemail** routes the call to a voicemail box that you select.


![Screenshot: call handling page Actions section](media/2a33b1f7-d362-47a7-bf32-ef702bc878e8b.png)


![Icon of the number 1,  a callout in the previous screenshot](media/teamscallout1.png)

 **Play call menu** lets you set up a prompts and options for the caller to choose. Select this instead of the **Redirect call to** option and the **Call menu builder** appears.

**Call menu builder** Menu options using a telephone keypad or a voice command can be added or removed in this dialog. To delete a menu option, remove the voice command entry and set **Redirect to** back to **Select**.

> [!TIP]
> Update menu prompt text or re-record the audio prompts when you remove options. The menu prompt played for callers isn't automatically updated.  
>
> Any menu option can be added and removed in any order, and the key mappings don't have to be continuous. It is possible, for example, to create a menu with keys 0, 1, and 3 mapped to options, while the key 2 isn't used.

> [!NOTE]
> The keys \* (Repeat) and \# (Back) are reserved by the system and can't be reassigned. If speech recognition is enabled, pressing * will correspond with "Repeat" and # will correspond with the "Back" voice commands.

To set up your menu options, for each **Dial key**:

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png) **The voice command that will connect to destination** column for an option can be up to 64 characters long, and can contain multiple words like "Customer Service" or "Operations and Grounds." If speech recognition is enabled, the name is automatically recognized, and the caller is able to press 3, say "three," or say "Customer Service" to select the option mapped to key 3.

![Icon of the number 3,  a callout in the previous screenshot](media/teamscallout3.png)
The **Redirect to** option sets where the call goes if the corresponding key is pressed, or the option is selected using speech recognition. The call can be sent to:

<!-- Is the Operator behavior changing here? Looks like operator is only an available option for dial key 0 -->

- **Operator** If an operator is already set up, the option is automatically mapped to key 0, but can also be deleted or reassigned to a different key. If operator isn't set to any key, the voice command "Operator" is also disabled. The caller who selects this option is sent to the designated Operator.
- **Person in your organization** can be an Online user or a user hosted on-premises using Skype for Business Server. The user must have a Phone System license that is enabled for Enterprise Voice or assigned Calling Plans in Office 365. Search for the person in the **Search by name** field.
- **Auto attendant** Select the name of an existing auto attendant in the **Search by name** field. You will also have to select a resource account associated to the auto attendant. The caller who selects this option is sent to that auto attendant.
- **Call queue** Select the name of an existing call queue in the **Search by name** field. You will also have to select a resource account associated to the call queue. The caller who selects this option is sent to that call queue, where the call is answered by a call agent.
- **External phone number** routes the caller to a designated phone number outside your local system.<!-- does this have prerequisites like direct routing? -->
- **Group Voicemail** routes the call to a voicemail box that you select.

* * *

![Icon of the number 4,  a callout in the previous screenshot](media/teamscallout4.png)

**Instructions for callers** lets you choose **Use recorded call instructions** or **Write your call instructions**.  

If you choose **Use recorded call instructions**, you have the option to record and upload new or prerecorded sound files to play as menu instructions. The same app used in recording the auto attendant greeting is used here.

If you choose **Write your call instructions**, enter the script  you want the system to read (up to 1000 characters). For example, you might enter text that begins "Please choose from one of the following menu options ... " and provide a script written to reflect your configuration.

* * *

When you are finished with your selections, you can click **Next** if you want to change advanced settings, or click **Submit** if you want to use default settings for things like business hours, holidays, .

#### Advanced settings (optional)

There are four additional screens that you can configure or leave at defaults as you choose.

##### Call flow for after hours

By default, an auto attendant's business hours are set to 24/7, and the call flow options for *after hours* calls are disabled because all hours are considered *business hours*. When you select the **Setup custom business hours** option, the **Call flow for after hours** page configures the call handling rules used by the auto attendant after hours. The options available are the same, the difference is the ability to set a schedule for different menus and behaviors.

A system of auto attendants may only need to set after hours call handling behavior for the first-level auto attendant. Nested auto attendants may not even be called by the first-level auto attendant, but alternately the system can define after-hours behavior for each auto attendant it uses.

Initially, the business hours are defined to start at 12:00 am and end at 12:00 pm, Sunday through Saturday. All hours that aren't during business hours are considered *after hours*.


![screenshot of the after hours call flow settings](media/aa-afterhour.png)
 * * *

![Icon of the number 1,  a callout in the previous screenshot](media/teamscallout1.png)
You can click **Reset to 24/7** to make all hours business hours again for this auto attendant.

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)
Select the **Clear all** option to unselect all changes in the schedule and define business hours to start at 12:00 am and end at 12:00 pm, Sunday through Saturday

![Icon of the number 3,  a callout in the previous screenshot](media/teamscallout3.png)
To customize start or end time for a day of the week, click on **Start at** or **End at** time you wish to reset and select the new time from the list that appears. The list allows you to select business hours in 15-minute intervals, and the business hours you select here are based on the time zone that you set on the **General info** page.

![Icon of the number 4,  a callout in the previous screenshot](media/teamscallout4.png)
To set up a break (a lunch break, for example), select **Add time slot** for that day of the week to create a new table row, and select new start and end times. You can set multiple breaks within business hours.

![Icon of the number 5,  a callout in the previous screenshot](media/teamscallout5.png)
 The **Apply to all days** option can be used to reset all days of the week to match the settings for that day. This makes setting weekdays and weekends to different hours easier.

![Icon of the number 6,  a callout in the previous screenshot](media/teamscallout6.png)

The [Call flow](#call-flow) options available after hours are the same as the options available during business hours.


* * *

When you are finished with your selections, click **Next**.

##### Call flow during holidays

<a name="holidaygreetings"> </a>

You can add up to 20 scheduled holidays to each auto attendant.

> [!TIP]
> To create Holidays you can go the the screen at **Org-wide settings** > **Holidays** or you can create them when creating a new call flow.

To set a custom call flow for holidays on the auto attendant with no holidays set, click **New call flow** the see the **New holiday call flow** screen.

![Screenshot: add a call handler](media/50a5ce88-7f39-4210-808a-da7ced969854b.png)

* * *

![Icon of the number 1,  a callout in the previous screenshot](media/teamscallout1.png)

Enter a **Name** for your new call flow.

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)

If you've already created holidays, you'll see them in the **Holiday** pull-down menu and can select them. You might see an unused option that you can edit into what you need. If not, click on **+ Add new** to create a new Holiday.  See [Set up holidays in Microsoft Teams](set-up-holidays-in-teams.md) for the steps used to create a holiday. 

A holiday call flow name can be up to 64 characters long and must be unique for the organization. For example, you can't have two holiday call flows named "Thanksgiving" in the same organization. Your auto attendant can have a call flow for each Holiday you've set up, but you might want to have a common set of behaviors planned other than a customized greeting.

![Icon of the number 3,  a callout in the previous screenshot](media/teamscallout3.png)

The [Call flow](#call-flow) options available after hours are the same as the options available during business hours.

> [!Note]
> By default, all calls received during a holiday period are set to disconnect after the greeting (if any), so you must specify a redirect if you want a custom behavior.

![Screenshot of the call flows during holidays page](media/50a5ce88-7f39-4210-808a-da7ced969854.png)

Once you have created a Holiday call flow, it will show up on the **Call Flows during holidays** screen. 

#### Dial scope

<a name="dialscope"> </a>

On this page, you can set who is listed in your directory and available for Dial by Name when a person calls your organization. Dial by name is set to **Off** by default.

![Screenshot showing the Dial scope page](media/1bcb185c-00db-43a7-b5c4-9b021c0627f7.png)

![Icon of the number 1,  a callout in the previous screenshot](media/teamscallout1.png) 

**Dial by name** If you enable this option, callers can search for people in your organization using Directory Search. You can select which users are listed as available or not available for Dial by Name in the other fields. Any online user with a Phone System license, or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with Dial by Name.

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)

**Include only custom user groups** This option lets you search for and select an Office 365 Group, distribution list, or security group already created in your organization. Users are added to the directory if they are in the chosen Office 365 Group, distribution list, or security group and they are **Online users with a Phone System license** or hosted on-premises using Skype for Business Server. You can add multiple Office 365 Groups, distribution lists, and security groups to the directory.

If you leave this blank when Dial by Name is enabled, all eligible users are included in directory search.

![Icon of the number 3,  a callout in the previous screenshot](media/teamscallout3.png)

**Exclude custom user groups** You can search for an Office 365 Group, distribution list, or security group that has been created in your organization. Users in that group are excluded from directory search. You can add multiple Office 365 Groups, distribution lists, and security groups.

If you leave this blank when Dial by Name is enabled, all eligible users are included in directory search.

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory. When someone uses Dial by Name with speech recognition, new accounts may not be available for this feature.

After you enter all the required fields and set up call handling menus and options, click **Next**.

#### Resource accounts

A first level auto attendant will definitely need at least one resource account with an associated service number. If you wish, you can assign several resource accounts, each with a separate service number, to an auto attendant.

![screenshot: optional resource account management](media/aa-ra-optional.png) 

![Icon of the number 1,  a callout in the previous screenshot](media/teamscallout1.png)
To add one or more existing and unassigned resource accounts to the auto attendant, click **+ Add resource accounts** and search and select them from the provided dialogs.

![Icon of the number 2,  a callout in the previous screenshot](media/teamscallout2.png)

The resource account created while creating the auto attendant is shown in a list, and designated the **current auto attendant**.

## Edit and test auto attendants

After you save your new auto attendant, it is listed on the **Auto attendants** page. That page allows you to quickly see some of the options that you have set up, including the name, phone number, language, and status.

If you want to change auto attendant settings, select the auto attendant, and then in the Action pane click **Edit**.

To quickly place a test call to your auto attendant, click the **Test** button in the Action pane.

## Summary view

You can use the Summary page to review the settings you've created.

![screenshot of the new attendant summary view](media/aa-new-summary.png)

Press the **Create** button to finish setup of your new auto attendant.

### Create an auto attendant with Powershell

You can also use PowerShell to create and set up auto attendants. Here are the cmdlets that you need to manage an auto attendant:

- [New-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/new-csautoattendant?view=skype-ps)  
- [Set-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/set-csautoattendant?view=skype-ps)
- [Get-CsAutoAttendant](https://docs.microsoft.com/powershell/module/skype/new-csautoattendant?view=skype-ps)
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

### More about Windows PowerShell

- Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Microsoft Teams from a single point of administration that can simplify your daily work. To get started with Windows PowerShell, see these topics:

  - [An introduction to Windows PowerShell and Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

  - [Why you need to use Office 365 PowerShell](https://docs.microsoft.com/en-us/office365/enterprise/powershell/why-you-need-to-use-office-365-powershell)

- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Microsoft 365 admin center, such as making setting changes for many users at once. Learn about these advantages in the following topics:

  - [Manage Office 365 with Office 365 PowerShell](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-office-365-with-office-365-powershell)

  - [Using Windows PowerShell to manage Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

## Related topics

[Here's what you get with Phone System in Office 365](/MicrosoftTeams/here-s-what-you-get-with-phone-system)

[Getting service phone numbers](/microsoftteams/getting-service-phone-numbers)

[Country and region availability for Audio Conferencing and Calling Plans](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)

[New-CsOrganizationalAutoAttendant](https://docs.microsoft.com/en-us/powershell/module/skype/new-csorganizationalautoattendant?view=skype-ps)  

[What are Cloud auto attendants?](what-are-phone-system-auto-attendants.md)

[Small business example — Set up an auto attendant](/microsoftteams/tutorial-org-aa)  
