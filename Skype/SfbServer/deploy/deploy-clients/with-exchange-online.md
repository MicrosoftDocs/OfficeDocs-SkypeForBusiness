---
title: "Deploy Skype Room Systems v2 with Exchange Online"
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Admin
ms.custom:
ms.assetid: f3ba85b8-442c-4133-963f-76f1c8a1fff9
description: "Read this topic for information on how to deploy Skype Room Systems v2 with Exchange Online."
---

# Deploy Skype Room Systems v2 with Exchange Online

Read this topic for information on how to deploy Skype Room Systems v2 with Exchange Online and Skype for Business Server on-premises.
  
If your organization has a mix of services, with some hosted on premises and some hosted online, then your configuration will depend on where each service is hosted. This topic covers hybrid deployments for Skype Room Systems v2 with Exchange hosted online. Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them. The following process will work for many configurations. If the process isn't right for your setup, we recommend that you use Windows PowerShell to achieve the same end result as documented here, and for other deployment options.

The easiest way to set up user accounts is to configure them using remote Windows PowerShell. Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Skype Room Systems v2 user accounts. If you prefer, you can follow the steps below to configure accounts your Skype Room Systems v2 device will use.

## Requirements

Before you deploy Skype Room Systems v2 with Exchange Online, be sure you have met the requirements. For more information, see [Skype Room Systems v2 requirements](../../plan-your-deployment/clients-and-devices/requirements.md).
  
To deploy Skype Room Systems v2 with Exchange Online, follow the steps below. Be sure you have the right permissions to run the associated cmdlets.
  
### Create an account and set Exchange properties

1. Start a remote Windows PowerShell session on a PC and connect to Exchange Online as follows:

``` Powershell
Set-ExecutionPolicy Unrestricted
$org='contoso.microsoft.com'
$cred=Get-Credential $admin@$org
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic  -AllowRedirection
```

2. After establishing a session, you'll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox. This will allow the account to authenticate into Skype Room Systems v2.

   If you're changing an existing resource mailbox:

   ``` Powershell
   Set-Mailbox -Identity 'PROJECTRIGEL01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

    If you're creating a new resource mailbox:

   ``` Powershell
   New-Mailbox -MicrosoftOnlineServicesID 'PROJECTRIGEL01@contoso.com' -Alias PROJECTRIGEL01 -Name "Project-Rigel-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

3. To improve the meeting experience, you'll need to set the Exchange properties on the user account as follows:

   ``` Powershell
   Set-CalendarProcessing -Identity 'PROJECTRIGEL01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'PROJECTRIGEL01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Skype Meeting room!"
   ```

4. You need to connect to Azure AD to apply some account settings. You can run this cmdlet to connect.

  ``` PowerShell
 Connect-MsolService -Credential $cred
  ```
<!--   ``` Powershell
   Connect-AzureAD -Credential $cred
   ``` -->

### Add an email address for your on-premises domain account

1. In **Active Directory Users and Computers AD** tool, right-click on the folder or Organizational Unit that your Skype Room Systems v2 accounts will be created in, click **New**, and then click **User**.
2. Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box. Click **Next**.
3. Type the password for this account. You'll need to retype it for verification. Make sure the **Password never expires** checkbox is the only option selected.

    > [!NOTE]
    > Selecting **Password never expires** is a requirement for Skype for Business Server on Skype Room Systems v2. Your domain rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Skype Room Systems v2 user account.
  
4. Click **Finish** to create the account.
5. After you've created the account, run a directory synchronization. When it's complete, go to the users page and verify that the two accounts created in the previous steps have merged.

### Assign an Office 365 license

1. The user account needs to have a valid Office 365 license to ensure that Exchange and Skype for Business Server will work. If you have the license, you need to assign a usage location to your user account—this determines what license SKUs are available for your account.
2. Next, use `Get-MsolAccountSku` <!--Get-AzureADSubscribedSku--> to retrieve a list of available SKUs for your Office 365 tenant.
3. Once you list out the SKUs, you can add a license using the `Set-MsolUserLicense` <!-- Set-AzureADUserLicense--> cmdlet. In this case, $strLicense is the SKU code that you see (for example, contoso:STANDARDPACK). 

  ```
    Set-MsolUser -UserPrincipalName 'PROJECTRIGEL01@contoso.com' -UsageLocation 'US'
   Get-MsolAccountSku
   Set-MsolUserLicense -UserPrincipalName 'PROJECTRIGEL01@contoso.com' -AddLicenses $strLicense
  ```
<!--   ``` Powershell
   Set-AzureADUserLicense -UserPrincipalName 'PROJECTRIGEL01@contoso.com' -UsageLocation 'US'
   Get-AzureADSubscribedSku
   Set-AzureADUserLicense -UserPrincipalName 'PROJECTRIGEL01@contoso.com' -AddLicenses $strLicense
   ``` -->

### Enable the user account with Skype for Business Server

1. Create a remote Windows PowerShell session from a PC as follows:

    ``` Powershell
    Import-Module SkypeOnlineConnector  
    $cssess=New-CsOnlineSession -Credential $cred  
    Import-PSSession $cssess -AllowClobber
    ```

2. To enable your Skype Room Systems v2 account for Skype for Business Server, run this command:

   ``` Powershell
   Enable-CsMeetingRoom -Identity $rm -RegistrarPool 'sippoolbl20a04.infra.lync.com' -SipAddressType EmailAddress
   ```

    If you aren't sure what value to use for the RegistrarPool parameter in your environment, you can get the value from an existing Skype for Business Server user using this command

   ``` Powershell
   Get-CsOnlineUser -Identity 'alice@contoso.com'| fl *registrarpool*
   ```

### Assign a Skype for Business Server license to your Skype Room Systems v2 account

1. Log in as a tenant administrator, open the Office 365 Administrative Portal, and click on the Admin app.
2. Click on **Users and Groups** and then click **Add users, reset passwords, and more**.
3. Click the Skype Room Systems v2 account, and then click the pen icon to edit the account information.
4. Click **Licenses**.
5. In **Assign licenses**, select Skype for Business (Plan 2) or Skype for Business (Plan 3), depending on your licensing and Enterprise Voice requirements. You'll have to use a Plan 3 license if you want to use Enterprise Voice on your Skype Room Systems v2.
6. Click **Save**.

For validation, you should be able to use any Skype for Business client to log in to this account.
  
## See also

[Configure accounts for Skype Room Systems v2](room-systems-v2-configure-accounts.md)

[Plan for Skype Room Systems v2](../../plan-your-deployment/clients-and-devices/skype-room-systems-v2-0.md)
  
[Deploy Skype Room Systems v2](room-systems-v2.md)
  
[Configure a Skype Room Systems v2 console](console.md)
  
[Manage Skype Room Systems v2](../../manage/skype-room-systems-v2/skype-room-systems-v2.md)