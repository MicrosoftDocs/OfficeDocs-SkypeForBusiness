---
title: "Deploy Microsoft Teams Rooms with Exchange on premises"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.custom: Strat_SB_Admin
ms.assetid: 24860c05-40a4-436b-a44e-f5fcb9129e98
ms.collection: M365-voice
description: "Read this topic for information on how to deploy Microsoft Teams Rooms in a hybrid environment with Exchange on premises."
---

# Deploy Microsoft Teams Rooms with Exchange on premises

Read this topic for information on how to deploy Microsoft Teams Rooms in a hybrid environment with Exchange on premises and Microsoft Teams or Skype for Business Online.
  
If your organization has a mix of services, with some hosted on premises and some hosted online, then your configuration will depend on where each service is hosted. This topic covers hybrid deployments for Microsoft Teams Rooms with Exchange hosted on premises. Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them. The following process will work for many configurations. If the process isn't right for your setup, we recommend that you use Windows PowerShell to achieve the same end result as documented here, and for other deployment options.

Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Microsoft Teams Rooms user accounts. If you prefer, you can follow the steps below to configure accounts your Microsoft Teams Rooms device will use.
  
## Requirements

Before you deploy Microsoft Teams Rooms with Exchange on premises, be sure you have met the requirements. For more information, see [Microsoft Teams Rooms requirements](requirements.md).
  
If you are deploying Microsoft Teams Rooms with Exchange on premises, you will be using Active Directory administrative tools to add an email address for your on-premises domain account. This account will be synced to Office 365. You will need to:
  
- Create an account and synchronize the account with Active Directory.

- Enable the remote mailbox and set properties.

- Assign an Office 365 license.

- Enable the device account with Skype for Business Server. To enable the device account your environment will need to meet the following prerequisites:

  - You'll need to have Skype for Business Online (Plan 2) or higher in your Office 365 plan. The plan needs to support conferencing capability.
  
  - - If you need Enterprise Voice (PSTN telephony) using telephony service providers for Microsoft Teams Rooms you need Skype for Business Online (Plan 3).
  
  - - Your tenant users must have Exchange mailboxes.
  
  - - Your Microsoft Teams Rooms account does require a Skype for Business Online (Plan 2) or Skype for Business Online (Plan 3) license, but it does not require an Exchange Online license.

- Assign a Skype for Business Server license to your Microsoft Teams Rooms account.

### Create an account and synchronize with Active Directory

1. In the **Active Directory Users and Computers** tool, right-click on the folder or Organizational Unit that your Microsoft Teams Rooms accounts will be created in, click **New**, and then click **User**.

2. Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box. Click **Next**.

3. Type the password for this account. You'll need to retype it for verification. Make sure the **Password never expires** checkbox is the only option selected.

    > [!NOTE]
    > Selecting **Password never expires** is a requirement for Skype for Business Server on Microsoft Teams Rooms. Your domain rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Microsoft Teams Rooms device account.
  
4. After you've created the account, run a directory synchronization. When it's complete, go to the users page in your Microsoft 365 admin center and verify that the account created in the previous steps has merged to online.

### Enable the remote mailbox and set properties

1. [Open the Exchange Management Shell](https://docs.microsoft.com/powershell/exchange/exchange-server/open-the-exchange-management-shell) or [connect to your Exchange server using remote PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell).

2. In Exchange PowerShell, crate a mailbox for the account (mailbox-enable the account)by running the following command:

   ``` Powershell
   Enable-Mailbox PROJECTRIGEL01@contoso.com -Room
   ```

   For detailed syntax and parameter information, see [Enable-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/enable-mailbox).

3. In Exchange PowerShell, configure the following settings on the room mailbox to improve the meeting experience:

   - AutomateProcessing: AutoAccept (Meeting organizers receive the room reservation decision directly without human intervention: free = accept; busy = decline.)

   - AddOrganizerToSubject: $false (The meeting organizer is not added to the subject of the meeting request.)

   - DeleteComments: $false (Keep any text in the message body of incoming meeting requests.)

   - DeleteSubject: $false (Keep the subject of incoming meeting requests.)

   - RemovePrivateProperty: $false (Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.)

   - AddAdditionalResponse: $true (The text specified by the AdditionalResponse parameter is added to meeting requests.)

   - AdditionalResponse: "This is a Skype Meeting room!" (The additional text to add to the meeting request.)

   This example configures these settings on the room mailbox named Project-Rigel-01.

   ``` PowerShell
   Set-CalendarProcessing -Identity "Project-Rigel-01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Skype Meeting room!"
   ```

   For detailed syntax and parameter information, see [Set-CalendarProcessing](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-calendarprocessing).

### Assign an Office 365 license

1. Connect to Azure Active Directory. For details about Active Directory, see [Azure ActiveDirectory (MSOnline) 1.0](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0). 

   > [!NOTE]
   > [Azure Active Directory PowerShell 2.0](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-2.0) is not supported. 

2. The device account needs to have a valid Office 365 license, or Exchange and Microsoft Teams will not work. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account. You can use `Get-MsolAccountSku` <!-- Get-AzureADSubscribedSku --> to retrieve a list of available SKUs.

<!--   ``` Powershell
   Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
   ``` -->

3. Next, you can add a license using the `Set-MsolUserLicense` <!-- Set-AzureADUserLicense --> cmdlet. In this case, $strLicense is the SKU code that you see (for example, contoso:STANDARDPACK).

  ``` PowerShell
  Set-MsolUser -UserPrincipalName 'PROJECTRIGEL01@contoso.com' -UsageLocation 'US'
  Get-MsolAccountSku
  Set-MsolUserLicense -UserPrincipalName 'PROJECTRIGEL01@contoso.com' -AddLicenses $strLicense
  ```

<!--   ``` Powershell
   Set-AzureADUserLicense -UserPrincipalName $acctUpn -UsageLocation "US"
   Get-AzureADSubscribedSku
   Set-AzureADUserLicense -UserPrincipalName $acctUpn -AddLicenses $strLicense
   ```  -->

   For detailed instructions, see [Assign licenses to user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell#use-the-microsoft-azure-active-directory-module-for-windows-powershell).

### Enable the device account

Skype for Business Online PowerShell is used to manage services for both Microsoft Teams and Skype for Business Online.

1. Create a remote Windows PowerShell session from a PC as follows:

   ``` Powershell
   Import-Module SkypeOnlineConnector  
   $cssess=New-CsOnlineSession -Credential $cred  
   Import-PSSession $cssess -AllowClobber
   ```

2. To enable your Microsoft Teams Rooms account, run this command:

   ``` Powershell
   Enable-CsMeetingRoom -Identity $rm -RegistrarPool'sippoolbl20a04.infra.lync.com' -SipAddressType EmailAddress
   ```

   If you aren't sure what value to use for the RegistrarPool parameter in your environment, you can get the value from an existing user using this command:

   ``` Powershell
   Get-CsOnlineUser -Identity 'alice@contoso.com'| fl *registrarpool*
   ```

### Assign a license to your Microsoft Teams Rooms account

1. Log in as a tenant administrator, open the Office 365 Administrative Portal, and click on the Admin app.
2. Click on **Users and Groups** and then click **Add users, reset passwords, and more**.
3. Click the Microsoft Teams Rooms account, and then click the pen icon to edit the account information.
4. Click **Licenses**.
5. In **Assign licenses**, select Skype for Business (Plan 2) or Skype for Business (Plan 3), depending on your licensing and Enterprise Voice requirements. You'll have to use a Plan 3 license if you want to use Enterprise Voice on your Microsoft Teams Rooms.
6. Click **Save**.

For validation, you should be able to use any client to log in to this account.
  
## See also

[Configure accounts for Microsoft Teams Rooms](room-systems-v2-configure-accounts.md)

[Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)
  
[Deploy Microsoft Teams Rooms](room-systems-v2.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)
