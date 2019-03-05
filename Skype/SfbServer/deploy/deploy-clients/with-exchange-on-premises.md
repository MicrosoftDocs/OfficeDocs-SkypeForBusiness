---
title: "Deploy Skype Room Systems v2 with Exchange on premises"
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.reviewer: davgroom
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.custom: Strat_SB_Admin
ms.assetid: 24860c05-40a4-436b-a44e-f5fcb9129e98
description: "Read this topic for information on how to deploy Skype Room Systems v2 in a hybrid environment with Exchange on premises."
---

# Deploy Skype Room Systems v2 with Exchange on premises

Read this topic for information on how to deploy Skype Room Systems v2 in a hybrid environment with Exchange on premises and Skype for Business Online.
  
If your organization has a mix of services, with some hosted on premises and some hosted online, then your configuration will depend on where each service is hosted. This topic covers hybrid deployments for Skype Room Systems v2 with Exchange hosted on premises. Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them. The following process will work for many configurations. If the process isn't right for your setup, we recommend that you use Windows PowerShell to achieve the same end result as documented here, and for other deployment options.

Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Skype Room Systems v2 user accounts. If you prefer, you can follow the steps below to configure accounts your Skype Room Systems v2 device will use.
  
## Requirements

Before you deploy Skype Room Systems v2 with Exchange on premises, be sure you have met the requirements. For more information, see [Skype Room Systems v2 requirements](../../plan-your-deployment/clients-and-devices/requirements.md).
  
If you are deploying Skype Room Systems v2 with Exchange on premises, you will be using Active Directory administrative tools to add an email address for your on-premises domain account. This account will be synced to Office 365. You will need to:
  
- Create an account and synchronize the account with Active Directory.
- Enable the remote mailbox and set properties.
- Assign an Office 365 license.
- Enable the device account with Skype for Business Server. To enable the device account your environment will need to meet the following prerequisites:

  - You'll need to have Skype for Business Online (Plan 2) or higher in your Office 365 plan. The plan needs to support conferencing capability.
  - If you need Enterprise Voice (PSTN telephony) using telephony service providers for Skype Room Systems v2 you need Skype for Business Online (Plan 3).
  - Your tenant users must have Exchange mailboxes.
  - Your Skype Room Systems v2 account does require a Skype for Business Online (Plan 2) or Skype for Business Online (Plan 3) license, but it does not require an Exchange Online license.

- Assign a Skype for Business Server license to your Skype Room Systems v2 account.

### Create an account and synchronize with Active Directory

1. In the **Active Directory Users and Computers AD** tool, right-click on the folder or Organizational Unit that your Skype Room Systems v2 accounts will be created in, click **New**, and then click **User**.
2. Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box. Click **Next**.
3. Type the password for this account. You'll need to retype it for verification. Make sure the **Password never expires** checkbox is the only option selected.

    > [!NOTE]
    > Selecting **Password never expires** is a requirement for Skype for Business Server on Skype Room Systems v2. Your domain rules may prohibit passwords that don't expire. If so, you'll need to create an exception for each Skype Room Systems v2 device account.
  
4. After you've created the account, run a directory synchronization. When it's complete, go to the users page in your Office 365 admin center and verify that the account created in the previous steps has merged to online.

### Enable the remote mailbox and set properties

1. Enable the remote mailbox by opening your on-premises Exchange management shell with administrator permissions and run the following command:

   ``` Powershell
   Enable-Mailbox 'PROJECTRIGEL01@contoso.com' -Room
   ```

2. Start a remote Windows PowerShell session and connect to Microsoft Exchange. From your Office 365 tenant, run the following commands:

   ``` Powershell
   $org='contoso.com'
   $cred=Get-Credential $admin@$org
   $sess = New-PSSession -ConfigurationName Microsoft.Exchange -Credential $cred -AllowRedirection -Authentication Basic -ConnectionUri "https://<ExchangeServerFQDN>/PowerShell"
   Import-PSSession $sess
   ```

3. To improve the meeting experience, you'll need to set the Exchange properties on the device account as follows:

   ``` Powershell
   Set-CalendarProcessing -Identity 'PROJECTRIGEL01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false
   -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'PROJECTRIGEL01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse 'This is a Skype Meeting room!'
   ``` Powershell
    For more information about which properties you need to set, see Exchange properties.

4. You will need to connect to Azure AD to apply some account settings. You can run this command to connect:

   ``` Powershell
   Connect-AzureAD -Credential $cred
   ```

### Assign an Office 365 license

1. The device account needs to have a valid Office 365 license to ensure that Exchange and Skype for Business Server will work. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account.
2. Next, use Get-AzureADSubscribedSku to retrieve a list of available SKUs for your Office 365 tenant.
3. Once you list out the SKUs, you can add a license using the Set-AzureADUserLicense cmdlet. In this case, $strLicense is the SKU code that you see (for example, contoso:STANDARDPACK).

   ``` Powershell
   Set-AzureADUserLicense -UserPrincipalName rigel1@contoso.com -PasswordNeverExpires $true -UsageLocation "US"

   Get-AzureADSubscribedSku
   Set-AzureADUserLicense -UserPrincipalName $acctUpn -AddLicenses $strLicense

   ```

### Enable the device account with Skype for Business

1. Create a remote Windows PowerShell session from a PC as follows:

   ``` Powershell
   Import-Module SkypeOnlineConnector  
   $cssess=New-CsOnlineSession -Credential $cred  
   Import-PSSession $cssess -AllowClobber
   ```

2. To enable your Skype Room Systems v2 account for Skype for Business Server, run this command:

   ``` Powershell
   Enable-CsMeetingRoom -Identity $rm -RegistrarPool'sippoolbl20a04.infra.lync.com' -SipAddressType EmailAddress
   ```

   If you aren't sure what value to use for the RegistrarPool parameter in your environment, you can get the value from an existing Skype for Business Server user using this command

   ``` Powershell
   Get-CsOnlineUser -Identity 'alice@contoso.com'| fl *registrarpool*
   ```

### Assign a Skype for Business license to your Skype Room Systems v2 account

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