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

# Create and configure resource accounts for Teams devices

This article provides steps to create resource accounts, required for Microsoft Teams Rooms on Windows, Microsoft Teams Rooms on Android, Microsoft Teams Rooms on Surface Hub, and hot desking on Teams displays.

> [!NOTE]
> **Skype for Business** <br><br>
> If you need to enable your resource account to also work with Skype for Business, see [Deploy Microsoft Teams Rooms with Skype for Business Server](with-skype-for-business-server-2015.md)

## Requirements

Depending on your environment, you'll need one or more roles to create the accounts.

|**Enviromnent**|**Required Roles**|
|:-----|:-----|
|Azure Active Directory  <br/> |Global Administrator or User Administrator  <br/> |
|Active Directory  <br/> |Active Directory Enterprise Admins, Domain Admins, or have delegated rights to create users. Azure Active Directory Connect Sync rights.  <br/> |
|Exchange Online  <br/> |Global Administrator or Exchange Administrator   <br/> |
|Exchange Server  <br/> |Exchange Organization Management or Recipient Management   <br/> |

## Overview

1. Create a new Microsoft Exchange resource account in the [Microsoft 365 admin center](with-office-365.md&tabs=m365-admin-center#create-a-resource-account), with [Exchange Online](with-office-365.md&&tabs=exchange-online#create-a-resource-account), or with [Exchange Server](with-office-365.md&&tabs=exchange-server#create-a-resource-account).<br><br>Or, if a room mailbox already exists and you want to convert it to a resource account, you can [Modify an existing Exchange room mailbox](with-office-365.md&tabs=existing-account#create-a-resource-account).

2. Then, [Configure your account](#configure-mailbox-properties) for Teams Meetings.

3. If the resource account is going to be associated with a shared device, such as Teams displays with hot desking, [Turn off password expiration](#turn-off-password-expiration).

4. Lastly, [assign licenses](#assign-meeting-room-license) so the account can access Microsoft Teams.

From there, there are [additional steps](#next-steps) you can review, including distribution groups, network capability, and calling.

## Create a resource account

> [!NOTE]
> When naming your resource accounts, we recommend using a standard naming convention, such as adding "mtr-" to the beginning of the e-mail address. This will help with creating dynamic groups to ease management in Azure Active Directory.

Create a resource account using a method from one of the following tabs:

#### [In Microsoft 365 admin center](#tab/m365-admin-center)

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

#### [**Modify an existing Exchange room mailbox**](#tab/existing-account)

To modify an existing room mailbox to become a resource account, use the following syntax:

``` PowerShell
Set-Mailbox -Identity <RoomMailboxIdentity> -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
```

This example enables the account for the existing room mailbox that has the alias value ConferenceRoom02, and sets the password to 9898P@$$W0rd.

``` PowerShell
Set-Mailbox -Identity ConferenceRoom02 -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '9898P@$$W0rd' -AsPlainText -Force)
```

If you're in an Exchange hybrid configuration, run the Exchange hybrid steps in the [Exchange Online tab](with-office-365.md&tabs=exchange-online#create-a-resource-account).

For detailed syntax and parameter information, see [New-Mailbox](/powershell/module/exchange/mailboxes/new-mailbox) and [Set-Mailbox](/powershell/module/exchange/mailboxes/set-mailbox).

> [!NOTE]
> If you are creating this account for Teams Room on Surface Hub, you should also enable ActiveSync on this account. This will allow you to send e-mail directly from the Surface Hub, such as sending a Whiteboard. See [Applying ActiveSync policies to device accounts (Surface Hub)](/surface-hub/apply-activesync-policies-for-surface-hub-device-accounts) to learn more.

---

## Configure mailbox properties

In Exchange PowerShell, either online or on-premises, configure the following settings on the room mailbox to improve the meeting experience:

- **AutomateProcessing: `AutoAccept`** Meeting organizers receive the room reservation decision directly without human intervention.

- **AddOrganizerToSubject: `$false`** The meeting organizer isn't added to the subject of the meeting request.

- **DeleteComments: `$false`** Keep any text in the message body of incoming meeting requests. This is required to process external Teams and third-party meetings to provide One Touch Join experience.

- **DeleteSubject: `$false`** Keep the subject of incoming meeting requests.

- **ProcessExternalMeetingMessages: `$true`** Specifies whether to process meeting requests that originate outside the Exchange organization. Required for external Teams meetings and [third-party meetings](/microsoftteams/rooms/third-party-join).

- **RemovePrivateProperty: `$false`** Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.

- **AddAdditionalResponse: `$true`** The text specified by the AdditionalResponse parameter is added to meeting requests.

- **AdditionalResponse: "This is a Microsoft Teams Meeting room!"** The additional text to add to the meeting acceptance response.

This example configures these settings on a room mailbox named ConferenceRoom01.

``` PowerShell
Set-CalendarProcessing -Identity "ConferenceRoom01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -ProcessExternalMeetingMessages $true -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
```

For detailed syntax and parameter information, see [Set-CalendarProcessing](/powershell/module/exchange/mailboxes/set-calendarprocessing).

   ---

## Turn off password expiration

You now need to set the resource account so that the password never expires. If the password expires, the resource account will no longer sign in on the device when the password expiry period is reached. The password will then need to be changed for the resource account and then updated on each device.
  
> [!NOTE]
> Setting **Password never expires** is a requirement for shared Microsoft Teams devices. If your domain rules may prohibit passwords that don't expire, you'll need to create an exception for each Microsoft Teams device resource account.

Follow the steps in one of the following tabs to turn on password expiration. 

#### [**Azure Active Directory 2.0**](#tab/azure-active-directory2-password/)

See [Set a password to never expire](/microsoft-365/admin/add-users/set-password-to-never-expire?view=o365-worldwide#set-a-password-to-never-expire).

This example sets the password for the account ConferenceRoom01@contoso.com to never expire.

```PowerShell
Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -PasswordPolicies DisablePasswordExpiration
```

#### [**Azure Active Directory 1.0**](#tab/azure-active-directory1-password/)

 1. Connect to MS Online PowerShell:

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

1. Connect to Active Directory PowerShell: 

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

## Assign a Meeting Room license

The resource account needs a Microsoft 365 or Office 365 license to sign into Microsoft Teams. 

> [!NOTE]
> The Meeting Room license is required for the hot desking on Teams displays.

First, follow the steps in one of the following tabs to assign a usage location to your resource account. The location determines what license SKUs are available for your account.

#### [**Active Directory 2.0**](#tab/active-directory2-license/)

1. Connect to Azure AD
  
```PowerShell
Connect-AzureAD
```

 For details about Active Directory, see [Azure Active Directory PowerShell for Graph](/powershell/azure/active-directory/overview?view=azureadps-2.0).

2. The resource account needs to have a valid Microsoft 365 or Office 365 license to ensure a successful sign-in to Teams. You need to assign a usage location to your resource account—this determines what license SKUs are available. You'll make the assignment in the next step.
   
Use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.
   
```PowerShell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

3. You add a usage location and a license using the `Set-AzureADUser` cmdlet. In this case, the user is located in the United States (US).

```PowerShell
Set-AzureADUser -ObjectID ConferenceRoom01@contoso.com -UsageLocation 'US'
```

4. To assign the license, you use the `Set-AzureADUser` cmdlet. In order to assign the license successfully, you need to convert the license SKU ID (see step 2) into a PowerShell license type object and then assign that object to the resource account. In the following example, the license SKU ID is 6070a4c8-34c6-4937-8dfb-39bbc6397a60, and it's assigned to the account conferenceroom01@contoso.com: 

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

For details about Active Directory, see [Azure Active Directory (MSOnline).](/powershell/azure/active-directory/overview?view=azureadps-1.0)

2. The resource account needs to have a valid Microsoft 365 or Office 365 license to ensure a successful sign-in to Teams. You need to assign a usage location to your resource account—this determines what license SKUs are available. You'll make the assignment in the next step.
   
Use `Get-MsolAccountSku` to retrieve a list of available SKUs for your Microsoft 365 or Office 365 organization.
   
3. Add a usage location and a license using the `Set-MsolUser` cmdlet. In this case, the user is located in the United States (US).

```PowerShell
Set-MsolUser -UserPrincipalName 'ConferenceRoom01@contoso.com' -UsageLocation 'US'
```

4. To assign the license, you use the `Set-MsolUser` cmdlet. In the following example, the "contoso:MEETING_ROOM" license is assigned to the account conferenceroom01@contoso.com.

```PowerShell
Set-MsolUserLicense -UserPrincipalName 'ConferenceRoom01@contoso.com' -AddLicenses 'contoso:MEETING_ROOM'
```

---

After you assign the usage location to the resource account, see [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell).

To validate the account creation and license assignment, sign in to any Teams Client using the account you created.

## Next steps

### Configure distribution groups

When scheduling a meeting using Microsoft Teams, you have the option of populating the **Add location** field with the name of the room where you will be hosting the meeting. To populate this list, you need to create Exchange distribution groups and then add the appropriate Teams Rooms resource accounts to this lists.

For Exchange Online, see [Create and manage distribution list groups in Exchange Online](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) for more information.

For Exchange Server, see [Manage distribution groups](/Exchange/recipients/distribution-groups?view=exchserver-2019)

### Network and bandwidth

If necessary, you may need to apply custom network or bandwidth policies or Meeting policies to this account. For more information on network and bandwidth policies, see [Meeting policy settings for audio & video](/microsoftteams/meeting-policies-audio-and-video). 

For Teams Rooms, we recommend you set the meeting policy bandwidth to 10MBps. We recommend that for collaboration purposes, keep the PowerPoint Live, Whiteboard, and Shared notes settings to on. You may want to change the “Participants & guests” settings to be unique for meeting rooms. For example, review the lobby settings such as which attendees to automatically admit to meetings. 

For more information on Teams meeting policies, see [Manage meeting policies in Microsoft Teams](/microsoftteams/meeting-policies-overview).

If you need to enable the resource account for Microsoft Teams Phone System, see [Assign, change, or remove a phone number for a user](/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user).

### Enable calling

Teams supports the ability to make and receive phone calls to the Public Switched Telephone Network (PSTN). There are no unique requirements to enable calling with resource accounts. You enable the resource account for calling in the same way you enable a regular user.

For information, see [Microsoft Teams Phone](https://www.microsoft.com/microsoft-teams/microsoft-teams-phone) page.

## Related topics

[Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)

[Deploy Microsoft Teams Rooms](rooms-deploy.md)

[Manage Microsoft Teams Rooms](rooms-manage.md)

[Microsoft Teams Rooms Licensing](rooms-licensing.md)
