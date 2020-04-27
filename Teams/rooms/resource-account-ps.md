---
title: "Creating Resource Accounts for collaborations bars for Microsoft Teams"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
ms.custom: 
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: "Read this topic for information on how to deploy Microsoft Teams Rooms with Office 365."
---

# Creating Resource Accounts for MIcrosoft Teams Rooms and collaborations bars for Microsoft Teams

Read this topic for information on how to create resource accounts for Microsoft Teams Rooms and collaboration bars for Microsoft Teams.

The easiest way to create a resource account is by using the Microsoft 365 admin center. [See this article on how to do this](resource-account-ui.md).

This article discusses creating a resource account using remote PowerShell.

## Requirements

Before you deploy Microsoft Teams Rooms with Office 365, be sure you have met the requirements. For more information, see [Microsoft Teams Rooms requirements](requirements.md).

- If you need dial-in capabilities from a meeting, you will need an Audio Conferencing and Phone System license.  If you need dial-out capabilities from a meeting, you will need an Audio Conferencing license.

- Your tenant users must have Exchange mailboxes.

- Your Microsoft Teams Rooms account does require at a minimum a Skype for Business Online (Plan 2) license, but it does not require an Exchange Online license. See [Microsoft Teams Rooms licenses](rooms-licensing.md) for details.

### Add a resource account

1. Connect to Exchange Online PowerShell. For instructions, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module).

2. In Exchange Online PowerShell, create a new room mailbox or modify an existing room mailbox.

   - To create a new room mailbox, use the following syntax:

     ``` PowerShell
     New-Mailbox -Name "<Unique Name>" -Alias <Alias> -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID <Account> -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
     ```

     This example creates a new room mailbox with the following settings:

     - Name: Huddle-Room-01

     - Alias: HuddleRoom01

     - Account: huddleroom01@contoso.onmicrosoft.com

     - Account password: P@$$W0rd5959

     ``` PowerShell
     New-Mailbox -Name "Huddle-Room-01" -Alias HuddleRoom01 -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID HuddleRoom01@contoso.onmicrosoft.com -RoomMailboxPassword (ConvertTo-SecureString -String 'P@$$W0rd5959' -AsPlainText -Force)
     ```

   - To modify an existing room mailbox, use the following syntax:

     ``` PowerShell
     Set-Mailbox -Identity <RoomMailboxIdentity> -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
     ```

     This example enables the account for the existing room mailbox that has the alias value HuddleRoom02, and sets the password to 9898P@$$W0rd. Note that the account will be HuddleRoom02@contoso.onmicrosoft.com because of the existing alias value.

     ``` PowerShell
     Set-Mailbox -Identity HuddleRoom02 -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '9898P@$$W0rd' -AsPlainText -Force)
     ```

   For detailed syntax and parameter information, see [New-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/new-mailbox) and [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox).


3. In Exchange Online PowerShell, configure the following settings on the room mailbox to improve the meeting experience:

   - AutomateProcessing: AutoAccept (Meeting organizers receive the room reservation decision directly without human intervention: free = accept; busy = decline.)

   - AddOrganizerToSubject: $false (The meeting organizer is not added to the subject of the meeting request.)

   - DeleteComments: $false (Keep any text in the message body of incoming meeting requests.)

   - DeleteSubject: $false (Keep the subject of incoming meeting requests.)

   - RemovePrivateProperty: $false (Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.)

   - AddAdditionalResponse: $true (The text specified by the AdditionalResponse parameter is added to meeting requests.)

   - AdditionalResponse: "This is a collaboration bar for Microsoft Teams Room!" (The additional text to add to the meeting request.)

   This example configures these settings on the room mailbox named Huddle-Room-01.

   ``` PowerShell
   Set-CalendarProcessing -Identity "Huddle-Room-01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a collaboration bar for Microsoft Teams Room!"
   ```

   For detailed syntax and parameter information, see [Set-CalendarProcessing](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-calendarprocessing).

4. Connect to MS Online PowerShell to make Active Directory settings by running the `Connect-MsolService -Credential $cred` powershell cmdlet.   For details about Active Directory, see [Azure ActiveDirectory (MSOnline) 1.0](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0). 

   > [!NOTE]
   > [Azure Active Directory PowerShell 2.0](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) is not supported. 

5.Set the password for huddleroom01@contoso.onmicrosoft.com to not expire using the following syntax:

    ``` PowerShell
    Set-MsolUser -UserPrincipalName huddleroom01@contoso.onmicrosoft.com -PasswordNeverExpires $true
    ```

6. The resource account needs to have a valid Office 365 license, preferably the Meeting Room SKU. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account. You can use `Get-MsolAccountSku` to retrieve a list of available SKUs for your Office 365 tenant as follows:

  ``` Powershell
  Get-MsolAccountSku
  ```
You can assign the license using Set-MsolUserLicense. 

  ``` Powershell
  Set-MsolUserLicense -UserPrincipalName huddleroom01@contoso.onmicrosoft.com -AddLicenses contoso:meeting_room
  ```
   For detailed instructions, see [Assign licenses to user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell#use-the-microsoft-azure-active-directory-module-for-windows-powershell).