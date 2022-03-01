---
title: "Create resource accounts for Teams devices"
ms.author: czawideh
author: cazawideh
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
ms.custom: seo-marvel-apr2020
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: Read this topic for information on how to deploy Microsoft Teams Rooms with Microsoft 365 or Office 365.
---

# Create resource accounts for Teams devices

This article provides steps to create resource accounts, required for Microsoft Teams Rooms on Windows, Microsoft Teams Rooms on Android, Microsoft Teams Rooms on Surface Hub, and hot desking on Teams displays.

## Requirements

Depending on your environment, you'll need some or all of the following roles to create the accounts.

|**Enviromnent**|**Required Roles**|
|:-----|:-----|
|Azure Active Directory  <br/> |Global Administrator or User Administrator  <br/> |
|Active Directory  <br/> |Active Directory Enterprise Admins, Domain Admins, or have delegated rights to create users. Azure Active Directory Connect Sync rights.  <br/> |
|Exchange Online  <br/> |Global Administrator or Exchange Administrator   <br/> |
|Exchange Server  <br/> |Exchange Organization Management or Recipient Management   <br/> |

## Overview

1. You'll need to create a new Microsoft Exchange resource account using the Microsoft 365 admin center or PowerShell. Or, if a room mailbox already exists and you want to convert it to a resource account, see Modify an existing Exchange room mailbox account.

2. After creating resource accounts, you'll apply recommended parameter, such as automatically accepting meeting invites.

3. Shared Teams devices require that the resource account password doesn't expire, so you'll need to turn off password expiration.

4. Finally, you need to assign an appropriate Microsoft 365 or Office 365 license so the account can sign in to Microsoft Teams.

## Create a resource account

<a name="steps"></a>

> [!IMPORTANT]
> When naming your resource accounts, we recommend using a standard naming convention, such as adding "mtr-" to the beginning of the e-mail address. This will help with creating dynamic groups to ease management in Azure Active Directory.

#### [Using Microsoft 365 admin center](#tab/m365-admin-center)

Start by going to [Create a resource account in the Microsoft 365 admin center](/microsoftteams/devices/resource-account-ui) to create the account and set up its password and licensing.

You can change the settings of the resource mailbox, such as adding an additional response,  using Exchange admin center or via the PowerShell cmdlets shown in the [Configure mailbox properties](#configure-mailbox-properties) section of this article.

You may also need to apply bandwidth policies or meeting policies to this account. See the [Additional considerations](#additional-considerations) section of this article for more information.

#### [**With Exchange Online**](#tab/exchange-online)

1. Connect to [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

``` PowerShell
Connect-ExchangeOnline
```

2. By default, room mailboxes don't have associated accounts, so you'll need to add an account when you create a room mailbox that allows it to authenticate with Microsoft Teams.

If you're creating a new resource mailbox:

``` PowerShell
New-Mailbox -MicrosoftOnlineServicesID <Office365 ID> -Name <String> -Alias <string> -Room -EnableRoomMailboxAccount $true  -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
```

This example creates a new room mailbox with the following settings:

- Account: ConferenceRoom01@contoso.com
  
- Name: ConferenceRoom01

- Alias: ConferenceRoom01

- Account password: P@$$W0rd5959

``` PowerShell
New-Mailbox -MicrosoftOnlineServicesID ConferenceRoom01@contoso.com -Name "ConferenceRoom01" -Alias ConferenceRoom01 -Room -EnableRoomMailboxAccount $true  -RoomMailboxPassword (ConvertTo-SecureString -String 'P@$$W0rd5959' -AsPlainText -Force)
```

If you're not in an Exchange hybrid configuration, then you can continue to the next step.

If you're in an Exchange hybrid configuration, you'll also need to add an email address for your on-premises domain account

1. In the **Active Directory Users and Computers AD** tool, right-click on the container or Organizational Unit that your rooms accounts will be created in, select **New**, and then select **User**.

2. Enter the display name (- Identity ) from the prior cmdlet (Set-Mailbox or New-Mailbox) into the **Full name** box, and enter the alias into the **User logon name** box. Select **Next**.

3. Enter the password for this account. **Password never expires** should be the only checkbox option selected.

    > [!NOTE]
    > Selecting **Password never expires** is a requirement for Microsoft Teams Rooms. Your IT security rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Microsoft Teams Rooms resource account.
  
4. Select **Finish** to create the account.

5. After you create the account, run a directory synchronization. This can be accomplished by using [Set-MsolDirSyncConfiguration](/powershell/module/msonline/set-msoldirsyncconfiguration) in PowerShell. When that is complete, go to the **Users** page and verify that the two accounts created in the previous steps have merged.

#### [**With Exchange Server**](#tab/exchange-server)

  1. Connect to Exchange Management Shell. [Open the Exchange Management Shell](/powershell/exchange/exchange-server/open-the-exchange-management-shell) or [connect to your Exchange server using remote PowerShell](/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell).

   2. To create a new room mailbox:

   ``` PowerShell
   New-Mailbox -UserPrincipalName <UPN> -Name <String> -Alias <String> -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
   ```
     
   This example creates a new room mailbox with the following settings:

   - Account: ConferenceRoom01@contoso.com
  
   - Name: ConferenceRoom01

   - Alias: ConferenceRoom01

   - Account password: P@$$W0rd5959

   ``` PowerShell
   New-Mailbox -UserPrincipalName ConferenceRoom01@contoso.com -Name "ConferenceRoom01" -Alias ConferenceRoom01 -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'P@$$W0rd5959' -AsPlainText -Force)
   ```

---

#### [**Modify an existing account**](#tab/existing-account)

To modify an existing room mailbox to become a resource account, use the following syntax:

   ``` PowerShell
  Set-Mailbox -Identity <RoomMailboxIdentity> -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
   ```

   This example enables the account for the existing room mailbox that has the alias value ConferenceRoom02, and sets the password to 9898P@$$W0rd.

   ``` PowerShell
   Set-Mailbox -Identity ConferenceRoom02 -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '9898P@$$W0rd' -AsPlainText -Force)
  ```

If you are in an Exchange hybrid configuration, run the Exchange hybrid steps in the [Exchange Online tab](&tabs=exchange-online#steps).

   For detailed syntax and parameter information, see [New-Mailbox](/powershell/module/exchange/mailboxes/new-mailbox) and [Set-Mailbox](/powershell/module/exchange/mailboxes/set-mailbox).

   > [!NOTE]
   > If you are creating this account for Teams Room on Surface Hub, you should also enable ActiveSync on this account. This will allow you to send e-mail directly from the Surface Hub, such as sending a Whiteboard. See [Applying ActiveSync policies to device accounts (Surface Hub)](/surface-hub/apply-activesync-policies-for-surface-hub-device-accounts) for steps on how to do this.

---

## Configure mailbox properties

In Exchange PowerShell (either online or on-premises), configure the following settings on the room mailbox to improve the meeting experience:

   - AutomateProcessing: AutoAccept (Meeting organizers receive the room reservation decision directly without human intervention.)

   - AddOrganizerToSubject: $false (The meeting organizer is not added to the subject of the meeting request.)

   - DeleteComments: $false (Keep any text in the message body of incoming meeting requests.)

   - DeleteSubject: $false (Keep the subject of incoming meeting requests.)

   - ProcessExternalMeetingMessages: $true (Specifies whether to process meeting requests that originate outside the Exchange organization. Required for [Direct Guest Join](/microsoftteams/rooms/third-party-join).)

   - RemovePrivateProperty: $false (Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.)

   - AddAdditionalResponse: $true (The text specified by the AdditionalResponse parameter is added to meeting requests.)

   - AdditionalResponse: "This is a Microsoft Teams Meeting room!" (The additional text to add to the meeting acceptance response.)

   This example configures these settings on the room mailbox named ConferenceRoom01.

   ``` PowerShell
   Set-CalendarProcessing -Identity "ConferenceRoom01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -ProcessExternalMeetingMessages $true -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
   ```

   For detailed syntax and parameter information, see [Set-CalendarProcessing](/powershell/module/exchange/mailboxes/set-calendarprocessing).

   ---

## Turn off password expiration

You now need to set the resource account so that the password never expires.
   > [!NOTE]
   > Setting **Password never expires** is a requirement for shared Microsoft Teams devices. Your domain rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Microsoft Teams device resource account. <br><br>
   > If the password expires, the resource account will no longer sign in on the device when the password expiry period is reached. The password will then need to be changed for the resource account and also updated on each device.

<!-- version 1.1 -->
::: moniker range="=Azure Active Directory 2.0"

### **Azure Active Directory 2.0**

  1. Connect to Azure Active Directory PowerShell.
    `Connect-AzureAD` 
    For details about Active Directory, see [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/overview?view=azureadps-2.0).


   2. Set the password to never expire by using the following syntax:

      ```PowerShell
      Set-AzureADUser -ObjectID <UPN> -PasswordPolicies DisablePasswordExpiration
      ```
      This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

      ```PowerShell
      Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration
      ```
::: moniker-end

#### [**Azure Active Directory 1.0**](#tab/azure-active-directory1-password/)

 1. Connect to MS Online PowerShell. 
   ```PowerShell
   Connect-MsolService
   ```
   For details about Active Directory, see [Azure Active Directory (MSOnline).](/powershell/azure/active-directory/overview?view=azureadps-1.0)
2. Set the password to never expire by using the following syntax:
   ```PowerShell
   Set-MsolUser -Identity <samAccountName> -PasswordNeverExpires $true
   ```
   This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

   ```PowerShell
   Set-MsolUser -UserPrincipalName 'ConferenceRoom01@contoso.com' -PasswordNeverExpires $true
   ```

#### [**Active Directory (On premises)**](#tab/active-directory1-password/)

1. Connect to Active Directory PowerShell.
```PowerShell
   Import-Module ActiveDirectory
```
For details about Active Directory PowerShell, see [ActiveDirectory](/powershell/module/activedirectory/?view=windowsserver2022-ps).
2. Set the password to never expire by using the following syntax:
   ```PowerShell
   Set-ADUser -Identity <samAccountName> -PasswordNeverExpires $true
   ```
   This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

   ```PowerShell
   Set-ADUser -Identity ConferenceRoom01@contoso.com -PasswordNeverExpires $true
   ```
---

## Assign Meeting Room license
The resource account needs to have a valid Microsoft 365 or Office 365 license, or Microsoft Teams will not work. If you have the license, you need to assign a usage location to your resource account—this determines what license SKUs are available for your account.
   > [!NOTE]
   > The Meeting Room license is required for the hotdesking feature to work on Teams display.

#### [**Active Directory 2.0**](#tab/active-directory2-license/)
  1. Connect to Azure AD.
    `Connect-AzureAD` 
    For details about Active Directory, see [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/overview?view=azureadps-2.0).

2. The user account needs to have a valid Microsoft 365 or Office 365 license to ensure a successful sign-in to Teams. You need to assign a usage location to your resource account—this determines what license SKUs are available for your account. You'll make the assignment in the next step.
   
   Use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.
   ```PowerShell
   Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
   ```
   
3. You add a usage location and a license using the `Set-AzureADUser` cmdlet. In this case, the user is located in the United States (US).

    ```PowerShell
    Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -UsageLocation 'US'
    ```

4. To assign the license, you use the `Set-AzureADUser` cmdlet. In order to assign the license successfully, you need to convert the license SKU ID (found in step 2 above) in to a PowerShell license type object and then assigning that object to the resource account. In the below example, the license SKU ID is 6070a4c8-34c6-4937-8dfb-39bbc6397a60 and it is assigned to the account conferenceroom01@contoso.com.

   ```PowerShell
   #Create an object for a single license type
   $License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
   $License.SkuId = "6070a4c8-34c6-4937-8dfb-39bbc6397a60" 
   
   #Create an object for a multiple license type
   $Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
   
   #Add the single license object to the multiple license object
   $Licenses.AddLicenses = $License 
   
   #Assign the license to the resource account
   Set-AzureADUserLicense -ObjectId ConferenceRoom01@contoso.com -AssignedLicenses $Licenses
    ```

#### [**Active Directory 1.0**](#tab/active-directory1-license/)

1. Connect to MS Online PowerShell. 
   ```PowerShell
   Connect-MsolService
   ```
   For details about Active Directory, see [Azure Active Directory (MSOnline).](/powershell/azure/active-directory/overview?view=azureadps-1.0)

2. The user account needs to have a valid Microsoft 365 or Office 365 license to ensure a successful sign-in to Teams. You need to assign a usage location to your resource account—this determines what license SKUs are available for your account. You'll make the assignment in the next step.
   
   Use `Get-MsolAccountSku` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.
   ```PowerShell
    Get-MsolAccountSku
   ```
   
3. You add a usage location and a license using the `Set-MsolUser` cmdlet. In this case, the user is located in the United States (US).

    ```PowerShell
     Set-MsolUser -UserPrincipalName 'ConferenceRoom01@contoso.com' -UsageLocation 'US'
    ```

4. To assign the license, you use the `Set-MsolUser` cmdlet. In the below example, the "contoso:MEETING_ROOM" license is assigned to the account conferenceroom01@contoso.com.

   ```PowerShell
   Set-MsolUserLicense -UserPrincipalName 'ConferenceRoom01@contoso.com' -AddLicenses 'contoso:MEETING_ROOM'

    ```
---
   For detailed instructions, see [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell).

## Skype for Business
If you need to enable your resource account to also work with Skype for Business, see [Deploy Microsoft Teams Rooms with Skype for Business Server](with-skype-for-business-server-2015.md)

## Additional considerations
If necessary, you may need to apply custom network or bandwidth policies or Meeting policies to this account. For more information on network and bandwidth policies, see [Meeting policy settings for audio & video](/microsoftteams/meeting-policies-audio-and-video). For more information on Teams meeting policies, see [Manage meeting policies in Microsoft Teams](/microsoftteams/meeting-policies-overview).

If you need to enable the resource account for Microsoft Teams Phone System, see [Assign, change, or remove a phone number for a user](/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user).

## Enable calling
Teams supports the ability to make and receive phone calls to the Public Switched Telephone Network (PSTN). This feature can help you do things such as call into a remote audio conference from Teams Rooms or have someone call in to join a meeting.

There are no unique requirements to enable calling with Resource Accounts. You enable the Resource Account for calling in the same way you enable a regular user.

For information on on calling with Teams, you can visit the [Microsoft Teams Phone](https://www.microsoft.com/microsoft-teams/microsoft-teams-phone) page.

Visit the [Assign, change, or remove a phone number for a user](d:/Git/GitHub/OfficeDocs-SkypeForBusiness-pr/Teams/assign-change-or-remove-a-phone-number-for-a-user.md) article for instructions on how to assign a phone number.

## Validate

For validation, you should be able to use any Microsoft Teams client to sign in to the account you created.

## See also

[Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Microsoft Teams Rooms Licensing](rooms-licensing.md)
