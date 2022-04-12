## Video demonstration

This video shows a basic example of how to create an auto attendant in Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWEnCG?autoplay=false]

## Before you begin

Get the service numbers (service numbers are a special type of phone number that are used by auto attendants) that you need for the auto attendants that you want to be accessible by direct dialing from outside your organization. This might include [transferring numbers from another provider](../phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [requesting new service numbers](../getting-service-phone-numbers.md).

Each auto attendant needs to be assigned a *Microsoft Teams Phone Standard - Virtual User* license. When you purchased Teams Phone Standard or Teams Phone with Calling Plan bundle licenses, you also received a number of *Microsoft Teams Phone Standard - Virtual User* licenses, so you probably don't need to request more. However, if you need more in the future, you can get them by following the instructions in [Teams Phone Standard - Virtual User license](../teams-add-on-licensing/virtual-user.md).

If you want to have your auto attendant route calls differently on holidays, then [create the holidays that you want to use](../set-up-holidays-in-teams.md) before you create the auto attendant.

<a name="steps"></a>

### Follow these steps to set up your auto attendant

# [Step 1 - Phone number](#tab/phone-number)

## Assign a phone number

Each auto attendant that you create requires a resource account. This is similar to a user account, except the account is associated with an auto attendant or call queue instead of a person. In this step, we'll create the account, assign it a *Microsoft Teams Phone Standard - Virtual User* license, and then assign a service number.

### Create a resource account

You can create a resource account in the Teams admin center.

1. In the Teams admin center, expand **Org-wide settings**, and then select **Resource accounts**.

2. Select **Add**.

3. In the **Add resource account** pane, fill out **Display name**, **Username**, and choose **Auto attendant** for the **Resource account type**

4. Select **Save**.

    The new account will appear in the list of accounts.

### Assign a license

You must assign a *Microsoft Teams Phone Standard - Virtual User* license to the resource account.

1. In the Microsoft 365 admin center, select the resource account to which you want to assign a license.

2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft Teams Phone Standard - Virtual User**.

3. Select **Save changes**.

### Assign a service number

If you need this auto attendant to be reachable by a phone number, then assign that number to the resource account.

1. In the Teams admin center, on the **Resource accounts** page, select the resource account to which you want to assign a service number, and then select **Assign/unassign**.

2. In the **Phone number type** dropdown, choose the type of number that you want to use.

3. In the **Assigned phone number** box, search for the number you want to use and select **Add**.

4. Select **Save**.

> [!div class="nextstepaction"]
> [Step 2 - Auto attendant general info >](?tabs=general-info#steps)

# [Step 2 - Attendant general info](#tab/general-info)

## Prepare auto attendants

To set up an auto attendant

1. In the Teams admin center, expand **Voice**, select **Auto attendants**, and then select **Add**.

2. Type a name for the auto attendant in the box at the top.

3. If you want to designate an operator, specify the destination for calls to the operator. This is optional (but recommended). You can set the **Operator** option to allow callers to break out of the menus and speak to a designated person.

4. Specify the time zone for this auto attendant. The time zone is used for calculating business hours if you [create a separate call flow for after hours](?tabs=call-flow#steps).

5. Specify a [supported language](../create-a-phone-system-auto-attendant-languages.md) for this auto attendant. This is the language that will be used for system-generated voice prompts.

6. Choose if you want to enable voice inputs. When enabled, the name of every menu option becomes a speech-recognition keyword. For example, callers can say "One" to select the menu option mapped to key 1, or they can say "Sales" to select the menu option named "Sales."

7. Select **Next**.

> [!div class="nextstepaction"]
> [Step 3 - Call flow >](?tabs=call-flow#steps)

# [Step 3 - Call flow](#tab/call-flow)

## Set up call flows

Choose your call flow options:

1. Choose if you want to play a greeting when the auto attendant answers a call.

    If you select **Play an audio file** you can use the **Upload file** button to upload a recorded greeting message saved as audio in .WAV, .MP3, or .WMA format. The recording can be no larger than 5 MB.

    If you select **Type a greeting message** the system will read the text you the text that you type (up to 1000 characters) when the auto attendant answers a call.

2. Choose how you want to route the call.

    If you select **Disconnect**, the auto attendant will hang up the call.

    If you select **Redirect call**, you can choose one of the call routing destinations.

    If you select **Play menu options**, you can choose to **Play an audio file** or **Type in a greeting message** and then choose between menu options and directory search.

3. If you want callers to use dial keys to navigate, then under **Set menu options**, choose what you want to happen when callers press a dial key. (If you're creating this auto attendant as a company directory, leave the dial key options blank.)

    The keys \* (asterisk) and \# (pound) are reserved by the system and can't be reassigned. Pressing either of these keys will repeat the current menu.

    Also, the \# key only backs up to the most recent auto attendant. Once the boundary is crossed to a new auto attendant, the \# key will not be able to take you to the previous one.

    You can set any of the dial keys to the following destinations:

    - **Person in the organization** - a person in your organization who is able to receive voice calls.
    - **Voice app** - another auto attendant or a call queue.
    - **External phone number** - any phone number. Use this format: +[country code][area code][phone number]
    - **Voicemail** - the voice mailbox associated with a Microsoft 365 group that you specify. You can choose if you want voicemail transcriptions and the "Please leave a message after the tone." system prompt.
    - **Operator** - the operator defined for the auto attendant. Defining an operator is optional. The operator can be defined as any of the other destinations in this list.

    We recommend setting 0 key to the operator.

    For each menu option, specify the following:

    - **Dial key** - the key on the telephone keypad to access this option. If voice inputs are available, callers can also say this number to access the option.

    - **Voice command** - defines the voice command that a caller can give to access this option, if voice inputs are enabled. It can contain multiple words like "Customer Service" or "Operations and Grounds."

    - **Redirect to** - where you want the call to go when callers choose this option. If you are redirecting to an auto attendant or call queue, choose the resource account associated with it.

4. Directory search

    If you assign dial keys to destinations, we recommend that you choose **None** for **Directory search**. If a caller attempts to dial a name or extension using keys that are assigned to specific destinations, they might be routed to a destination before they finish entering the name or extension. We recommend that you create a separate auto attendant for directory search and have your main auto attendant link to it with a dial key.

    If you didn't assign dial keys, then choose an option for **Directory search**.

    **Dial by name** - If you use this option, callers can say the user's name or type it on the telephone keypad. Under **Directory search**, select **Dial by name**. Any online user with a Teams Phone Standard license, Teams Phone with Calling Plan bundle license, or any user hosted on-premises using Skype for Business Server is an eligible user and can be found with Dial by name.

    You can set who is and isn't included in the directory on the [Dial scope](?tabs=dial-scope#steps) tab.

    **Dial by extension** - If you use this option, callers can connect with users in your organization by dialing their phone extension. You can choose **Dial by extension**, however the extension must be configured in Azure Active Directory.

    Users you want to make available for **Dial By extension** need to have an extension specified as part of one of the following phones attributes. See [Add users individually or in bulk](/microsoft-365/admin/add-users/add-users) for more information.

    - OfficePhone
    - HomePhone
    - Mobile/MobilePhone
    - TelephoneNumber/PhoneNumber
    - OtherTelephone

    The required format to enter the extension in the user phone number field can be one of the following formats:

    - *+\<phone number>;ext=\<extension>*
    - *+\<phone number>x\<extension>*
    - *x\<extension>*

    - Example 1: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678;ext=5678"
    - Example 2: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "+15555555678x5678"
    - Example 3: Set-MsolUser -UserPrincipalName usern@domain.com -Phonenumber "x5678"

    You can set the extension in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Azure Active Directory admin center](https://aad.portal.azure.com). It can take up to 12 hours before changes are available to auto attendants and call queues.

    > [!NOTE]
    > If you want to use both the **Dial by name** and **Dial by extension** features, you can assign a dial key on your main auto attendant to reach an auto attendant enabled for **Dial by name**. Within that auto attendant, you can assign the 1 key (which has no letters associated with it) to reach the **Dial by extension** auto attendant.

5. Once you have selected a **Directory search** option, select **Next**.

> [!div class="nextstepaction"]
> [Step 4 - After hours call flow >](?tabs=after-hours#steps)

# [Step 4 - After hours](#tab/after-hours)

## After hours call flow

Business hours can be set for each auto attendant. If business hours aren't set, all days and all hours in the day are considered business hours because a 24/7 schedule is set by default. Business hours can be set with breaks in time during the day, and all of the hours that are not set as business hours are considered after-hours. You can set different incoming call-handling options and greetings for after-hours.

Depending on how you have configured your auto attendants and call queues, you may only need to specify after-hours call routing for auto attendants with direct phone numbers.

If you want separate call routing for after-hours callers, then specify your business hours for each day. Select **Add new time** to specify multiple sets of hours for a given day, for example, to specify a lunch break.

Once you have specified your business hours, then choose your call routing options for after hours. The same options are available as for the business hours call routing that you specified in **Step 3 - Call flow**.

Select **Next** when you're done.

> [!div class="nextstepaction"]
> [Step 5 - Holiday call flow >](?tabs=holidays#steps)

# [Step 5 - Holidays](#tab/holidays)

## Holidays call flow

Your auto attendant can have a call flow for each [Holiday you've set up](../set-up-holidays-in-teams.md). You can add up to 20 scheduled holidays to each auto attendant.

1. On the Holiday call settings page, select **Add**.

2. Type a name for this holiday setting.

3. From the **Holiday** dropdown, choose the holiday that you want to use.

4. Choose the type of greeting that you want to use.

5. Choose if you want to **Disconnect** or **Redirect** the call.

6. If you chose to redirect, choose the call routing destination for the call.

7. Select **Save**.

    Repeat the procedure as needed for each additional holiday.

    When you've added all your holidays, select **Next**.

> [!div class="nextstepaction"]
> [Step 6 - Choose who's in the directory >](?tabs=dial-scope#steps)

# [Step 6 - Directory members](#tab/dial-scope)

## Define dial scope

The *dial scope* defines which users are available in the directory when a caller uses dial-by-name or dial-by-extension. The default of **All online users** includes all users in your organization that are Online users with a Teams Phone license.

You can include or exclude specific users by selecting **Custom user group** under **Include** or **Exclude** and choosing one or more Microsoft 365 groups, distribution lists, or security groups. For example, you might want to exclude executives in your organization from the dialing directory. (If a user is in both lists, they will be excluded from the directory.)

> [!NOTE]
> It might take up to 36 hours for a new user to have their name listed in the directory.

When you're done setting the dial scope, select **Next**.

> [!div class="nextstepaction"]
> [Step 7 - Assign a resource account >](?tabs=resource-accounts#steps)

# [Step 7 - Resource accounts](#tab/resource-accounts)

## Assign resource accounts

All auto attendants must have an associated resource account.  First level auto attendants will need at least one resource account that has an associated service number. If you wish, you can assign several resource accounts to an auto attendant, each with a separate service number.

To add a resource account

1. Select **Add** and search for the account that you want to add. Select **Add**, and then select **Add**.

2. When you have finished adding service accounts, select **Submit**.

    This completes the auto attendant configuration.

See [Manage Teams resource accounts](../manage-resource-accounts.md) for more information.

---
