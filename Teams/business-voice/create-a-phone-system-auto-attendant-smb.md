---
title: "Set up an auto attendant for Microsoft Teams - small business tutorial"
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: colongma
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - Phone System
description: "Learn how to set up and test auto attendants for Microsoft 365 Business Voice."
--- 
# Set up an auto attendant - small business tutorial

Auto attendants let people call your organization and navigate a menu system to speak to the right department, call queue, person, or an operator. You can create auto attendants for your organization with the Microsoft Teams admin center.

Auto attendants can direct calls, based on callers' input, to one of the following destinations:

- **Person in the organization** - a person in your organization who is able to receive voice calls.
- **Voice app** - another auto attendant or a call queue.
- **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
- **Voicemail** - the voice mailbox associated with a Microsoft 365 group that you specify.
- **Operator** - the operator defined for the auto attendant. Defining an operator is optional. The operator can be defined as any of the other destinations in this list.


## Before you begin

Get the service numbers that you need for the auto attendants that you want to be accessible by direct dialing from outside your organization. This might include [transferring numbers from another provider](../phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [requesting new service numbers](../getting-service-phone-numbers.md).

Get a [Phone System - Virtual User license](../teams-add-on-licensing/virtual-user.md) for each auto attendant that you plan to create. These licenses are free, so we suggest getting a few extra in case you decide to make changes to your setup in the future.

<a name="steps"></a>

#### Follow these steps to set up your auto attendant

# [Step 1<br>Phone number](#tab/phone-number)

Each auto attendant that you create requires a resource account. This is similar to a user account, except the account is associated with an auto attendant or call queue instead of a person. In this step, we'll create the account, assign it a *Microsoft 365 Phone System - Virtual User* license, and then assign a service number.

### Create a resource account

You can create a resource account in the Teams admin center.

1. In the Teams admin center, expand **Org-wide settings**, and then click **Resource accounts**.

2. Click **Add**.

3. In the **Add resource account** pane, fill out **Display name**, **Username**, and choose **Auto attendant** for the **Resource account type**

    ![Screenshot of add resource account user interface](../media/resource-account-add.png)

4. Click **Save**.

The new account will appear in the list of accounts.

![Screenshot of a list of resource accounts](../media/resource-accounts-page.png)

### Assign a license

You must assign a *Microsoft 365 Phone System - Virtual User* license to the resource account.

1. In the Microsoft 365 admin center, click the resource account to which you want to assign a license.

2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft 365 Phone System - Virtual User**.

3. Click **Save changes**.

    ![Screenshot of assign licenses user interface in the Microsoft 365 admin center](../media/resource-account-assign-virtual-user-license.png)

### Assign a service number

If you need this auto attendant to be reachable by a phone number, then assign that number to the resource account.

1. In the Teams admin center, on the **Resource accounts** page, select the resource account to which you want to assign a service number, and then click **Assign/unassign**.

2. In the **Phone number type** dropdown, choose the type of number that you want to use.

3. In the **Assigned phone number** box, search for the number you want to use and click **Add**.

    ![Screenshot of the assign service number user interface](../media/resource-account-assign-phone-number.png)

4. Click **Save**.

> [!div class="nextstepaction"]
> [Step 2 - Auto attendant general info >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-auto-attendant-smb?branch=mikeplum-smb-voice&tabs=general-info#steps)

# [Step 2<br>Attendant general info](#tab/general-info)

To set up an auto attendant

1. In the Teams admin center, expand **Voice**, click **Auto attendants**, and then click **Add**.

2. Type a name for the auto attendant in the box at the top.

3. If you want to designate an operator, specify the destination for calls to the operator. This is optional (but recommended). You can set the **Operator** option to allow callers to break out of the menus and speak to a designated person.

4. Specify the time zone for this auto attendant. The time zone is used for calculating business hours if you create a separate call flow for after hours.

5. Specify a language for this auto attendant. This the language that will be used for system-generated voice prompts.

6. Choose if you want to enable voice inputs. When enabled, the name of every menu option becomes a speech-recognition keyword. For example, callers can say "One" to select the menu option mapped to key 1, or they can say "Sales" to select the menu option named "Sales."

    ![Screenshot of auto attendant settings for name, operator, time zone, language, and voice inputs](../media/auto-attendant-general-info-page-new.png)

7. Click **Next**.

> [!div class="nextstepaction"]
> [Step 3 - Call flow >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-auto-attendant-smb?branch=mikeplum-smb-voice&tabs=call-flow#steps)

# [Step 3<br>Call flow](#tab/call-flow)

![Screenshot of greeting message settings](../media/auto-attendant-call-flow-greeting-message.png)

Choose if you want to play a greeting when the auto attendant answers a call.

If you select **Play an audio file** you can use the **Upload file** button to upload a recorded greeting message saved as audio in .WAV, .MP3, or .WMA format. The recording can be no larger than 5 MB.

If you select **Type a greeting message** the system will read the text you the text that you type (up to 1000 characters) when the auto attendant answers a call.

![Screenshot of call routing settings](../media/auto-attendant-call-flow-route-call-message.png)

Choose how you want to route the call.

If you select **Disconnect**, the auto attendant will hang up the call.

If you select **Redirect call**, you can choose one of the call routing destinations.

If you select **Play menu options**, you can choose to **Play an audio file** or **Type in a greeting message** and then choose between menu options and directory search.

### Menu options

![Screenshot of dial key options](../media/auto-attendant-call-flow-menu-options-complete.png)

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

The required format to enter the extension in the user phone number field is either *+\<phone number>;ext=\<extension>* or *+\<phone number>;x\<extension>*.
Example: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678;ext=5678".

You can set the extension in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Azure Active Directory admin center](https://aad.portal.azure.com). It can take up to 12 hours before changes are available to auto attendants and call queues.

> [!NOTE]
> If you want to use both the **Dial by name** and **Dial by extension** features, you can assign a dial key on your main auto attendant to reach an auto attendant enabled for **Dial by name**. Within that auto attendant, you can assign the 1 key (which has no letters associated with it) to reach the **Dial by extension** auto attendant.

Once you have selected a **Directory search** option, click **Next**.

> [!div class="nextstepaction"]
> [Step 4 - After hours >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-auto-attendant-smb?branch=mikeplum-smb-voice&tabs=after-hours#steps)

# [Step 4<br>After hours](#tab/after-hours)

## Call flow for after hours

![Screenshot of after hours day and time settings](../media/auto-attendant-business-hours.png)

Business hours can be set for each auto attendant. If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default. Business hours can be set with breaks in time during the day, and all of the hours that are not set as business hours are considered after-hours. You can set different incoming call-handling options and greetings for after-hours.

Depending on how you have configured your auto attendants and call queues, you may only need to specify after-hours call routing for auto attendants with direct phone numbers.

If you want separate call routing for after-hours callers, then specify your business hours for each day. Click **Add new time** to specify multiple sets of hours for a given day, for example, to specify a lunch break.

Once you have specified your business hours, then choose your call routing options for after hours. The same options are available as for the business hours call routing that you specified above.

Click **Next** when you're done.

> [!div class="nextstepaction"]
> [Step 5 - Holidays >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-auto-attendant-smb?branch=mikeplum-smb-voice&tabs=holidays#steps)

# [Step 5<br>Holidays](#tab/holidays)

## Create a holiday

To create a holiday

1. In the Microsoft Teams admin center, go to **Org-wide settings** > **Holidays**.

2. Select **New holiday**.

3. Enter a name for the holiday.

4. Select **Add new date**.

5. Under **Start time**, select the calendar icon and choose the date when you'd like the holiday to begin.

6. Use the drop-down list to select a start time for the holiday.

7. Under **End time**, select the calendar icon and choose the date when you'd like the holiday to end.

8. Use the drop-down list to select an end time for the holiday. The **End time** must be after the **Start time**.  

   > [!NOTE]
   > If the holiday is for one full day (i.e., a 24 hour period), the **End time** should be set to the next day and the time to 12:00 AM. For example, if your organization is closed on January 1 for New Year's day, set the **Start time** to January 1 12:00 AM and set the **End time** to January 2 @ 12:00 AM.

9. Optionally, add more dates for recurring holidays.

10. Select **Save**.

    ![Screenshot of holidays user interface with dates set up for three years](../media/holidays-set-up.png)

## Call flows during holidays


![Screenshot of holiday and holiday greeting settings](../media/auto-attendant-holiday-greeting.png)

Your auto attendant can have a call flow for each [Holiday you've set up](../set-up-holidays-in-teams.md). You can add up to 20 scheduled holidays to each auto attendant.

1. On the Holiday call settings page, click **Add**.

2. Type a name for this holiday setting.

3. From the **Holiday** dropdown, choose the holiday that you want to use.

4. Choose the type of greeting that you want to use.

    ![Screenshot of holiday call action settings](../media/auto-attendant-holiday-actions.png)

5. Choose if you want to **Disconnect** or **Redirect** the call.

6. If you chose to redirect, choose the call routing destination for the call.

7. Click **Save**.

![Screenshot of holiday settings with holidays listed](../media/auto-attendant-holiday-call-settings.png)

Repeat the procedure as needed for each additional holiday.

When you've added all your holidays, click **Next**.

> [!div class="nextstepaction"]
> [Step 6 - Dial scope >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-auto-attendant-smb?branch=mikeplum-smb-voice&tabs=dial-scope#steps)

# [Step 6<br>Dial scope](#tab/dial-scope)

## Dial scope

![Screenshot of dial scope include and exclude options](../media/auto-attendant-dial-scope.png)

The *dial scope* defines which users are available in the directory when a caller uses dial-by-name or dial-by-extension. The default of **All online users** includes all users in your organization that are Online users with a Phone System license or hosted on-premises using Skype for Business Server.

You can include or exclude specific users by selecting **Custom user group** under **Include** or **Exclude** and choosing one or more Microsoft 365 groups, distribution lists, or security groups. For example, you might want to exclude executives in your organization from the dialing directory. (If a user is in both lists, they will be excluded from the directory.)

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory.

When you're done setting the dial scope, click **Next**.

> [!div class="nextstepaction"]
> [Step 7 - Resource accounts >](https://review.docs.microsoft.com/microsoftteams/business-voice/create-a-phone-system-auto-attendant-smb?branch=mikeplum-smb-voice&tabs=resource-accounts#steps)

# [Step 7<br>Resource accounts](#tab/resource-accounts)

## Resource accounts

All auto attendants must have an associated resource account.  First level auto attendants will need at least one resource account that has an associated service number. If you wish, you can assign several resource accounts to an auto attendant, each with a separate service number.

![Screenshot of resource account add accounts panel](../media/auto-attendant-add-resource-account.png)

To add a resource account, click **Add account** and search for the account that you want to add. Click **Add**, and then click **Add**.

![Screenshot of resource account list showing resource account with assigned service number](../media/auto-attendant-resource-account-assigned.png)

When you have finished adding service accounts, click **Submit**. This completes the auto attendant configuration.

---


