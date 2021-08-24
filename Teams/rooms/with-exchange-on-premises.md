---
title: Deploy Microsoft Teams Rooms with Exchange on-premises
ms.author: dstrome
author: dstrome
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.topic: quickstart
ms.service: msteams
f1.keywords:
- NOCSH
localization_priority: Normal
ms.custom: 
 - Strat_SB_Admin
 - seo-marvel-apr2020
ms.assetid: 24860c05-40a4-436b-a44e-f5fcb9129e98
ms.collection: 
  - M365-collaboration
description: "Read this topic for information on how to deploy Microsoft Teams Rooms in a hybrid environment with Exchange on premises."
---

# Deploy Microsoft Teams Rooms with Exchange on premises

Read this topic for information on how to deploy Microsoft Teams Rooms in a hybrid environment with Exchange on-premises and Microsoft Teams.
  
If your organization has a mix of services, with some hosted on premises and some hosted online, then your configuration will depend on where each service is hosted. This topic covers hybrid deployments for Microsoft Teams Rooms with Exchange hosted on premises. Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them. The following process will work for many configurations. If the process isn't right for your setup, we recommend that you use Windows PowerShell to achieve the same end result as documented here, and for other deployment options.

Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Microsoft Teams Rooms user accounts. If you prefer, you can follow the steps below to configure accounts your Microsoft Teams Rooms device will use.
  
## Requirements

Before you deploy Microsoft Teams Rooms with Exchange on premises, be sure you have met the requirements. For more information, see [Microsoft Teams Rooms requirements](requirements.md).
  
If you are deploying Microsoft Teams Rooms with Exchange on premises, you will be using Active Directory administrative tools to add an email address for your on-premises domain account. This account will be synced to Microsoft 365 or Office 365. You will need to:
  
- Create an account and synchronize the account with Azure Active Directory.

- Enable the remote mailbox and set properties.

- Assign an Microsoft 365 or Office 365 license.

### Create an account and synchronize with Azure Active Directory

1. In the **Active Directory Users and Computers** tool, right-click on the folder or Organizational Unit that your Microsoft Teams Rooms accounts will be created in, click **New**, and then click **User**.

2. Type the display name into the **Full name** box, and the alias into the **User logon name** box. Click **Next**.

3. Type the password for this account. You'll need to retype it for verification. Make sure the **Password never expires** checkbox is the only option selected.

    > [!NOTE]
    > Selecting **Password never expires** is a requirement for Microsoft Teams Rooms. Your domain rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Microsoft Teams Rooms device account.
  
4. After you've created the account, run a directory synchronization. When it's complete, go to the users page in your Microsoft 365 admin center and verify that the account created in the previous steps has merged to online.

### Enable the remote mailbox and set properties

1. [Open the Exchange Management Shell](/powershell/exchange/exchange-server/open-the-exchange-management-shell) or [connect to your Exchange server using remote PowerShell](/powershell/exchange/exchange-server/connect-to-exchange-servers-using-remote-powershell).

2. In Exchange PowerShell, create a mailbox for the account (mailbox-enable the account) by running the following command:

   ```PowerShell
   Enable-Mailbox PROJECTRIGEL01@contoso.com -Room
   ```

   For detailed syntax and parameter information, see [Enable-Mailbox](/powershell/module/exchange/mailboxes/enable-mailbox).

3. In Exchange PowerShell, configure the following settings on the room mailbox to improve the meeting experience:

   - AutomateProcessing: AutoAccept (Meeting organizers receive the room reservation decision directly without human intervention: free = accept; busy = decline.)

   - AddOrganizerToSubject: $false (The meeting organizer is not added to the subject of the meeting request.)

   - DeleteComments: $false (Keep any text in the message body of incoming meeting requests.)

   - DeleteSubject: $false (Keep the subject of incoming meeting requests.)

   - RemovePrivateProperty: $false (Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.)

   - AddAdditionalResponse: $true (The text specified by the AdditionalResponse parameter is added to meeting requests.)

   - AdditionalResponse: "This is a Microsft Teams Meeting room!" (The additional text to add to the meeting request.)

   This example configures these settings on the room mailbox named Project-Rigel-01.

   ```PowerShell
   Set-CalendarProcessing -Identity "Project-Rigel-01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
   ```

   For detailed syntax and parameter information, see [Set-CalendarProcessing](/powershell/module/exchange/mailboxes/set-calendarprocessing).

### Assign a Microsoft 365 or Office 365 license

1. Connect to Azure Active Directory. For details about Azure Active Directory, see [Azure ActiveDirectory (MSOnline) 1.0](/powershell/azure/active-directory/overview?view=azureadps-1.0). 

   > [!NOTE]
   > [Azure Active Directory PowerShell 2.0](/powershell/azure/active-directory/overview?view=azureadps-2.0) is not supported. 

2. The device account needs to have a valid Microsoft 365 or Office 365 license, or Exchange and Microsoft Teams will not work. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account. You can use `Get-MsolAccountSku` <!-- Get-AzureADSubscribedSku --> to retrieve a list of available SKUs.

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

   For detailed instructions, see [Assign licenses to user accounts with Office 365 PowerShell](/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell#use-the-microsoft-azure-active-directory-module-for-windows-powershell).

For validation, you should be able to use any client to log in to this account.
  
## Related topics

[Configure accounts for Microsoft Teams Rooms](rooms-configure-accounts.md)

[Plan for Microsoft Teams Rooms](rooms-plan.md)
  
[Deploy Microsoft Teams Rooms](rooms-deploy.md)
  
[Configure a Microsoft Teams Rooms console](console.md)
  
[Manage Microsoft Teams Rooms](rooms-manage.md)
