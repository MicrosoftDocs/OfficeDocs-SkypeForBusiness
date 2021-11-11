---
title: "Deploy Microsoft Teams Rooms with Exchange Online"
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
ms.assetid: f3ba85b8-442c-4133-963f-76f1c8a1fff9
description: "Read this topic for information on how to deploy Microsoft Teams Rooms with Exchange Online."
---

# Deploy Microsoft Teams Rooms with Exchange Online

Read this topic for information on how to deploy Microsoft Teams Rooms with Exchange Online.
  
If your organization has a mix of services, with some hosted on premises and some hosted online, then your configuration will depend on where each service is hosted. This topic covers hybrid deployments for Microsoft Teams Rooms with Exchange hosted online. Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them. The following process will work for many configurations. If the process isn't right for your setup, we recommend that you use Windows PowerShell to achieve the same end result as documented here, and for other deployment options.

## Requirements

Before you deploy Microsoft Teams Rooms with Exchange Online, be sure you have met the requirements. For more information, see [Microsoft Teams Rooms requirements](requirements.md).
  
To deploy Microsoft Teams Rooms with Exchange Online, follow the steps below. Be sure you have the right permissions to run the cmdlets. 

   > [!NOTE]
   >  The [Azure Active Directory Module for Windows PowerShell cmdlets](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0) in this section (for example,  Set-MsolUser) have been tested in setting up accounts for Microsoft Teams Rooms. It's possible that other cmdlets may work, however, they haven't been tested in this specific scenario.

If you deployed Active Directory Federation Services (AD FS), you may have to convert the user account to a managed user before you follow these steps, and then convert the user back to a federated user after you complete these steps.
  
### Create an account and set Exchange properties

1. Start a remote Windows PowerShell session on a PC and connect to Exchange Online as follows:

    ``` Powershell
   Connect-ExchangeOnline
    ```

2. After establishing a session, you'll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox. This will allow the account to authenticate into Microsoft Teams Rooms.

   If you're changing an existing resource mailbox:

   ``` Powershell
   Set-Mailbox -Identity 'ConferenceRoom01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

    If you're creating a new resource mailbox:

   ``` Powershell
   New-Mailbox -MicrosoftOnlineServicesID 'ConferenceRoom01@contoso.com' -Alias ConferenceRoom01 -Name 'ConferenceRoom01' -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

3. To improve the meeting experience, you'll need to set the Exchange properties on the user account as follows:

   ``` Powershell
   Set-CalendarProcessing -Identity 'ConferenceRoom01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'ConferenceRoom01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Rooms enabled  room!"
   ```

### Add an email address for your on-premises domain account

1. In **Active Directory Users and Computers AD** tool, right-click on the container or Organizational Unit that your Microsoft Teams Rooms accounts will be created in, click **New**, and then click **User**.
2. Type the display name (- Identity ) from the prior cmdlet (Set-Mailbox or New-Mailbox) into the **Full name** box, and the alias into the **User logon name** box. Click **Next**.
3. Type the password for this account. You'll need to retype it for verification. Make sure the **Password never expires** checkbox is the only option selected.

    > [!NOTE]
    > Selecting **Password never expires** is a requirement for Microsoft Teams Rooms. Your domain rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Microsoft Teams Rooms user account.
  
4. Click **Finish** to create the account.
5. After you have created the account, run a directory synchronization. This can be accomplished by using [Set-MsolDirSyncConfiguration](https://docs.microsoft.com/powershell/module/msonline/set-msoldirsyncconfiguration?view=azureadps-1.0) in PowerShell. When that is complete, go to the users page and verify that the two accounts created in the previous steps have merged.

### Assign an Office 365 license

1. First, connect to Azure AD to apply some account settings. You can run this cmdlet to connect. For details about Active Directory, see [Azure ActiveDirectory (MSOnline) 1.0](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-1.0).

   > [!NOTE]
   > [Azure Active Directory PowerShell 2.0](https://docs.microsoft.com/powershell/azure/active-directory/overview?view=azureadps-2.0) is not supported.

    ``` PowerShell
   Connect-MsolService
    ```

2. The user account needs to have a valid Office 365 license to connect to Microsoft Teams. If you have the license, you need to assign a usage location to your user account—this determines what license SKUs are available for your account.
3. Use 'Get-MsolAccountSku' to retrieve a list of available SKUs for your Office 365 tenant.
4. Once you list out the SKUs, you can add a license using the 'Set-MsolUserLicense' <!-- Set-AzureADUserLicense--> cmdlet. 

    ```PowerShell
     Set-MsolUser -UserPrincipalName 'ConferenceRoom01@contoso.com' -UsageLocation 'US'
     Get-MsolAccountSku
     Set-MsolUserLicense -UserPrincipalName 'ConferenceRoom01@contoso.com' -AddLicenses 'contoso:MEETING_ROOM
    ```

## Validate

For validation, you should be able to use any Microsoft Teams client to sign in to the account you created.
  
## See also

[Update room mailboxes with additional metadata to  provides a better search and room suggestion experience](https://docs.microsoft.com/powershell/module/exchange/set-place)

[Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)
  
[Deploy Microsoft Teams Rooms](rooms-deploy.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)
