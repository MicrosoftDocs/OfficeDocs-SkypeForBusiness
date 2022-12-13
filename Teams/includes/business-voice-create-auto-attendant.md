## Video demonstration

This video shows a basic example of how to create an auto attendant in Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWEnCG?autoplay=false]

### Follow these steps to set up your auto attendant

# [Step 1 - General info](#tab/general-info)

## General info

![Screenshot of auto attendant settings for name, operator, time zone, language, and voice inputs.](../media/auto-attendant-general-info-page-new.png)

1. Type a name for the auto attendant in the box at the top.

2. To designate an operator, specify the destination for calls to the operator. This designation is optional (but recommended). Set the **Operator** option to allow callers to break out of the menus and speak to a designated person.

3. Specify the time zone for this auto attendant. The time zone is used for calculating business hours if you [create a separate call flow for after hours](?tabs=after-hours).

4. Specify a [supported language](../create-a-phone-system-auto-attendant-languages.md) for this auto attendant. This is the language that will be used for system-generated voice prompts.

5. Choose if you want to enable voice inputs. When enabled, the name of every menu option becomes a speech-recognition keyword. For example, callers can say "One" to select the menu option mapped to key 1, or they can say "Sales" to select the menu option named "Sales."

   > [!NOTE]
   > If you choose a language in Step 4 that doesn't support voice inputs this option will be disabled.

6. Select **Next**.

# [Step 2 - Call flow](#tab/call-flow)

## Call flow

![Screenshot of greeting message settings.](../media/auto-attendant-call-flow-greeting-message.png)

Choose if you want to play a greeting when the auto attendant answers a call.

If you select **Play an audio file** you can use the **Upload file** button to upload a recorded greeting message saved as audio in .WAV, .MP3, or .WMA format. The recording can be no larger than 5 MB.

If you select **Type a greeting message** the system will read the text that you type (up to 1000 characters) when the auto attendant answers a call.

![Screenshot of call routing settings.](../media/auto-attendant-call-flow-route-call-message.png)

Choose how you want to route the call.

If you select **Disconnect**, the auto attendant will hang up the call.

If you select **Redirect call**, you can choose one of the call routing destinations.

If you select **Play menu options**, you can choose to **Play an audio file** or **Type in a greeting message** and then choose between menu options and directory search.

### Menu options

![Screenshot of dial key options.](../media/auto-attendant-call-flow-menu-options-complete.png)

For dialing options, assign the 0-9 keys on the telephone keypad to one of the call routing destinations. (The keys \* (asterisk) and \# (pound) are reserved by the system and can't be reassigned. Pressing either of these keys will repeat the current menu.)

> [!NOTE]
> The # key only backs up to the most recent auto attendant. Once the boundary is crossed to a new auto attendant, the # key will not be able to take you to the previous one.

Key mappings don't have to be continuous. It's possible to create a menu with keys 0, 1, and 3 mapped to options, while the number 2 key isn't used.

We recommend mapping the zero key to the operator if you've configured one. If the operator isn't set to any key, the voice command "Operator" is also disabled.

For each menu option, specify the following settings:

- **Dial key** - the key on the telephone keypad to access this option. If voice inputs are available, callers can also say this number to access the option.

- **Voice command** - defines the voice command that a caller can give to access this option, if voice inputs are enabled. It can contain multiple words like "Customer Service" or "Operations and Grounds." For example, the caller can press 2, say "two," or say "Sales" to select the option mapped to the two keys. This text is also rendered by text to speech for the service confirmation prompt, which might be something like "Transferring your call to sales."

- **Redirect to** - the call routing destination used when callers choose this option. If you are redirecting to an auto attendant or call queue, choose the resource account associated with it.

### Directory search

If you assign dial keys to destinations, we recommend that you choose **None** for **Directory search**. If a caller attempts to dial a name or extension using keys that are assigned to specific destinations, they might be unexpectedly routed to a destination before they finish entering the name or extension. We recommend that you create a separate auto attendant for directory search and have your main auto attendant link to it with a dial key.

If you didn't assign dial keys, then choose an option for **Directory search**.

**Dial by name** - If you enable this option, callers can say the user's name or type it on the telephone keypad. Any online user or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with Dial by name. (You can set who is and isn't included in the directory on the [Dial scope](?tabs=#dial-scope) page.)

**Dial by extension** - If you enable this option, callers can connect with users in your organization by dialing their phone extension. Any online user or any user hosted on-premises using Skype for Business Server, is an eligible user and can be found with **Dial by extension**. (You can set who is and isn't included in the directory on the [Dial scope](?tabs=dial-scope) page.)

Users you want to make available for Dial By Extension need to have an extension specified as part of one of the following phone attributes defined in Active Directory (and synchronized via Azure AD Connect) or Azure Active Directory. For more information, see [Add users individually or in bulk](/microsoft-365/admin/add-users/add-users).

- OfficePhone/TelephoneNumber (AD and Azure AD)
- HomePhone (AD)
- Mobile/MobilePhone (AD and Azure AD)
- OtherTelephone (AD)

The required format to enter the extension in the user phone number field can be one of the following formats:

- *+\<phone number>;ext=\<extension>*
- *+\<phone number>x\<extension>*
- *x\<extension>*

- Example 1: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678;ext=5678"
- Example 2: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678x5678"
- Example 3: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "x5678"

You can set the extension in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Azure Active Directory admin center](https://aad.portal.azure.com). It can take up to 12 hours before changes are available to auto attendants and call queues.

> [!NOTE]
> If you want to use both the **Dial by name** and **Dial by extension** features, you can assign a dial key on your main auto attendant to reach an auto attendant enabled for **Dial by name**. Within that auto attendant, you can assign the 1 key (which has no letters associated with it) to reach the **Dial by extension** auto attendant.

For more information, see [Dial and voice reference](../dial-voice-reference.md).

Once you have selected a **Directory search** option, select **Next**.

# [Step 3 - After hours](#tab/after-hours)

## Call flow for after hours

![Screenshot of after hours day and time settings.](../media/auto-attendant-business-hours.png)

Business hours can be set for each auto attendant. If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default. Business hours can be set with breaks in time during the day, and all of the hours that are not set as business hours are considered after-hours. You can set different incoming call-handling options and greetings for after-hours.

Depending on how you have configured your auto attendants and call queues, you may only need to specify after-hours call routing for auto attendants with direct phone numbers.

If you want separate call routing for after-hours callers, then specify your business hours for each day. Select **Add new time** to specify multiple sets of hours for a given day, for example, to specify a lunch break.

Once you've specified your business hours, then choose your call routing options for after hours. The same options are available as for the business hours call routing that you specified above.

Select **Next** when you're done.

# [Step 4 - Holidays](#tab/holidays)

## Call flows during holidays

![Screenshot of holiday and holiday greeting settings.](../media/auto-attendant-holiday-greeting.png)

Your auto attendant can have a call flow for each [Holiday you've set up](../set-up-holidays-in-teams.md). You can add up to 20 scheduled holidays to each auto attendant.

1. On the Holiday call settings page, select **Add**.

2. Type a name for this holiday setting.

3. From the **Holiday** dropdown, choose the holiday that you want to use.

4. Choose the type of greeting that you want to use.

    ![Screenshot of holiday call action settings.](../media/auto-attendant-holiday-actions.png)

5. Choose if you want to **Disconnect** or **Redirect** the call.

6. If you chose to redirect, choose the call routing destination for the call.

7. Select **Save**.

![Screenshot of holiday settings with holidays listed.](../media/auto-attendant-holiday-call-settings.png)

Repeat the procedure as needed for each additional holiday.

When you've added all your holidays, select **Next**.

# [Step 5 - Dial scope](#tab/dial-scope)

## Dial scope

![Screenshot of dial scope include and exclude options.](../media/auto-attendant-dial-scope.png)

The *dial scope* defines which users are available in the directory when a caller uses dial-by-name or dial-by-extension. The default of **All online users** includes all users in your organization that are Online users or hosted on-premises using Skype for Business Server.

You can include or exclude specific users by selecting **Custom user group** under **Include** or **Exclude** and choosing one or more Microsoft 365 groups, distribution lists, or security groups. For example, you might want to exclude executives in your organization from the dialing directory. (If a user is in both lists, they will be excluded from the directory.)

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory.

When you're done setting the dial scope, select **Next**.

# [Step 6 - Resource accounts](#tab/resource-accounts)

## Resource accounts

All auto attendants must have an associated resource account.  First-level auto attendants will need at least one resource account that has an associated service number. If you wish, you can assign several resource accounts to an auto attendant, each with a separate service number.

![Screenshot of resource account add accounts panel.](../media/auto-attendant-add-resource-account.png)

To add a resource account, select **Add account** and search for the account that you want to add. Select **Add**, and then select **Add**.

![Screenshot of resource account list showing resource account with assigned service number.](../media/auto-attendant-resource-account-assigned.png)

When you have finished adding resource accounts, select **Submit** to complete auto attendant configuration.

For more information, see [Manage Teams resource accounts](../manage-resource-accounts.md).

---
