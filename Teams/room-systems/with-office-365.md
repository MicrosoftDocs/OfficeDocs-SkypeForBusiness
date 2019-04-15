---
title: "Deploy Microsoft Teams Rooms with Office 365"
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
- M365-voice
ms.custom:
ms.assetid: f09f4c2a-2608-473a-9a27-f94017d6e9dd
description: "Read this topic for information on how to deploy Microsoft Teams Rooms with Office 365."
---

# Deploy Microsoft Teams Rooms with Office 365

Read this topic for information on how to deploy Microsoft Teams Rooms with Office 365, where Skype for Business and Exchange are both online.

The easiest way to set up user accounts is to configure them using remote Windows PowerShell. Microsoft provides [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), a script that will help create new user accounts, or validate existing resource accounts you have in order to help you turn them into compatible Microsoft Teams Rooms user accounts. If you prefer, you can follow the steps below to configure accounts your Microsoft Teams Rooms device will use.

## Requirements

Before you deploy Microsoft Teams Rooms with Office 365, be sure you have met the requirements. For more information, see [Microsoft Teams Rooms requirements](requirements.md).

To enable Skype for Business, you must have the following:

- Skype for Business Online (Plan 2, or an Enterprise-based plan) or higher in your Office 365 plan. The plan needs to allow dial-in conferencing capabilities.

- If you need dial-in capabilities from a meeting, you will need an audio conferencing and Phone System license.  If you need dial-out capabilities from a meeting, you will need a domestic or domestic and international Calling Plan.

- Your tenant users must have Exchange mailboxes.

- Your Microsoft Teams Rooms account does require at a minimum a Skype for Business Online (Plan 2) license, but it does not require an Exchange Online license. See [Microsoft Teams Rooms Licensing](/SfbOnline/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-room-systems-v2.md) for details.

For details on Skype for Business Online Plans, see the [Skype for Business Online Service Description](https://technet.microsoft.com/library/jj822172.aspx).

### Add a device account

1. Connect to Exchange Online PowerShell. For instructions, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).

2. In Exchange Online PowerShell, create a new room mailbox or modify an existing room mailbox. By default, room mailboxes don't have associated accounts, so you'll need to add an account when you create or modify a room mailbox that allows it to authenticate with Skype Room Systems v2.

   - To create a new room mailbox, use the following syntax:

     ``` PowerShell
     New-Mailbox -Name "<Unique Name>" -Alias <Alias> -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID <Account> -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
     ```

     This example creates a new room mailbox with the following settings:

     - Name: Project-Rigel-01

     - Alias: ProjectRigel01

     - Account: ProjectRigel01@contoso.onmicrosoft.com

     - Account password: P@$$W0rd5959

     ``` PowerShell
     New-Mailbox -Name "Project-Rigel-01" -Alias ProjectRigel01 -Room -EnableRoomMailboxAccount $true -MicrosoftOnlineServicesID ProjectRigel01@contoso.onmicrosoft.com -RoomMailboxPassword (ConvertTo-SecureString -String 'P@$$W0rd5959' -AsPlainText -Force)
     ```

   - To modify an existing room mailbox, use the following syntax:

     ``` PowerShell
     Set-Mailbox -Identity <RoomMailboxIdentity> -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)
     ```

     This example enables the account for the existing room mailbox that has the alias value ProjectRigel02, and sets the password to 9898P@$$W0rd. Note that the account will be ProjectRigel02@contoso.onmicrosoft.com because of the existing alias value.

     ``` PowerShell
     Set-Mailbox -Identity ProjectRigel02 -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '9898P@$$W0rd' -AsPlainText -Force)
     ```

   For detailed syntax and parameter information, see [New-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/new-mailbox) and [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/set-mailbox).


3. In Exchange Online PowerShell, configure the following settings on the room mailbox to improve the meeting experience:

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

4. Connect to MS Online PowerShell to make Active Directory settings by running the `Connect-MsolService -Credential $cred` powershell cmdlet.   For details about Active Directory, see [Azure ActiveDirectory (MSOnline) 1.0](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-1.0). <!-- or [Azure Active Directory PowerShell 2.0](https://docs.microsoft.com/en-us/powershell/azure/active-directory/overview?view=azureadps-2.0) for the new module -->  
    1. If you do not want the password to expire, use the following syntax:

    ``` PowerShell
    Set-MsolUser -UserPrincipalName $acctUpn -PasswordNeverExpires $true
    ```
<!--
   ``` PowerShell
   Set-AzureADUserPassword -UserPrincipalName <Account> -EnforceChangePasswordPolicy $false
   ```  -->

   This example sets the password for the account ProjectRigel01@contoso.onmicrosoft.com to never expire.

  ``` PowerShell
    Set-MsolUser -UserPrincipalName $acctUpn -PasswordNeverExpires $true
  ```
<!-- 
   ``` PowerShell
   Set-AzureADUserPassword -UserPrincipalName ProjectRigel01@contoso.onmicrosoft.com -EnforceChangePasswordPolicy $false
   ``` -->

   You can also set a phone number for the account by running the following command:

  ``` PowerShell
    Set-MsolUser -UserPrincipalName <upn> -PhoneNumber <phone number>
  ```
<!-- 
   ``` PowerShell
   Set-AzureADUser -UserPrincipalName <Account> -PhoneNumber "<PhoneNumber>"
   ```  -->

6. The device account needs to have a valid Office 365 license, or Exchange and Skype for Business will not work. If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account. You can use `Get-MsolAccountSku` <!-- Get-AzureADSubscribedSku --> to retrieve a list of available SKUs for your Office 365 tenant as follows:

  ``` Powershell
  Get-MsolAccountSku
  ```
<!--
   ``` Powershell
   Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
   ```  -->

   Next, you can add a license using the `Set-MsolUserLicense` <!--Set-AzureADUserLicense --> cmdlet. In this case, $strLicense is the SKU code that you see (for example, contoso:STANDARDPACK).

  ``` PowerShell
   Set-MsolUser -UserPrincipalName $acctUpn -UsageLocation "US"
   Get-MsolAccountSku
   Set-MsolUserLicense -UserPrincipalName $acctUpn -AddLicenses $strLicense
  ``` 
<!-- 
   ``` Powershell
   Set-AzureADUserLicense -UserPrincipalName $acctUpn -UsageLocation "US"
   Get-AzureADSubscribedSku
   Set-AzureADUserLicense -UserPrincipalName $acctUpn -AddLicenses $strLicense
   ```   -->

   For detailed instructions, see [Assign licenses to user accounts with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell#use-the-microsoft-azure-active-directory-module-for-windows-powershell).

7. Next, you need to enable the device account with Skype for Business. Be sure your environment meets the requirements defined in [Microsoft Teams Rooms requirements](requirements.md).

   Start a remote [Windows PowerShell session](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell) as follows (be sure to [install Skype for Business Online PowerShell components](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/download-and-install-the-skype-for-business-online-connector)):

   ``` Powershell
   Import-Module SkypeOnlineConnector  
   $cssess=New-CsOnlineSession -Credential $cred  
   Import-PSSession $cssess -AllowClobber
   ```

   Next, enable your Microsoft Teams Rooms account for Skype for Business Server by running the following cmdlet:

   ``` Powershell
   Enable-CsMeetingRoom -Identity $rm -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```

   Obtain the RegistrarPool information from the new user account being setup, as shown in this example:

    ``` Powershell
    Get-CsOnlineUser -Identity $rm | Select -Expand RegistrarPool
    ```

    > [!NOTE]
    > New user accounts might not be created on the same registrar pool as existing user accounts in the tenant. The command above will prevent errors in account setup due to this situation.

After you've completed the preceding steps to enable your Microsoft Teams Rooms account in Skype for Business Online, you need to assign a license to Microsoft Teams Rooms device. Using the Office 365 administrative portal, assign either a Skype for Business Online (Plan 2) or a Skype for Business Online (Plan 3) license to the device.

### Assign a license to your account

1. Login as a tenant administrator, open the Office 365 Administrative Portal, and click on the Admin app.

2. Click **Users and Groups** and then click **Add users, reset passwords, and more**.

3. Select the Microsoft Teams Rooms account, and then click or tap the pen icon, which means edit.

4. Click on the **Licenses** option.

5. In the **Assign licenses** section, you need to select Skype for Business Online (Plan 2) or Skype for Business Online (Plan 3), depending on your licensing and what you've decided in terms of needing Enterprise Voice. You'll have to use a Plan 3 license if you want to use Cloud PBX on Microsoft Teams Rooms. Minimally you will need CloudPBX for voice connectivity. Then configure hybrid voice or PSTN calling based on the PSTN connectivity method. See [Microsoft Teams Rooms licenses](https://docs.microsoft.com/en-us/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-room-systems-v2) for more details.

6. Click **Save** to complete the task.

## Sample: Room account setup in Exchange Online and Skype for Business Online

Exchange Online PowerShell commands:

``` Powershell
New-Mailbox -MicrosoftOnlineServicesID Rigel1@contoso.com -Alias rigel1 -Name "Rigel 1" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String '<Password>' -AsPlainText -Force)

Set-CalendarProcessing -Identity rigel1 -AutomateProcessing AutoAccept-AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true
-AdditionalResponse "This is a Rigel room!"
```

Azure Active Directory PowerShell commands:

``` PowerShell
Set-MsolUser -UserPrincipalName rigel1@contoso.com -PasswordNeverExpires $true -UsageLocation "US"
Set-MsolUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:O365_BUSINESS_PREMIUM"
Set-MsolUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:MCOEV"
Set-MsolUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:MCOPSTN2"
```

<!-- 
``` PowerShell
Set-AzureADUserLicense -UserPrincipalName rigel1@contoso.com -PasswordNeverExpires $true -UsageLocation "US"
Set-AzureADUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:O365_BUSINESS_PREMIUM"
Set-AzureADUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:MCOEV"
Set-AzureADUserLicense -UserPrincipalName rigel1@contoso.com -AddLicenses "sfblab:MCOPSTN2"
```  -->

Skype for Business PowerShell command:

``` PowerShell
Enable-CsMeetingRoom -Identity rigel1@contoso.onmicrosoft.com -RegistrarPool sippooldm21a05.infra.lync.com
-SipAddressType EmailAddress
```

> [!NOTE]
> This adds CloudPBX and PSTNCallingDomesticAndInternational. Additionally, you will need to use the Admin interface to assign a phone number.

## Validate

For validation, you should be able to use any Skype for Business client to sign in to the account you created.

## See also

[Configure accounts for Microsoft Teams Rooms](room-systems-v2-configure-accounts.md)

[Plan for Microsoft Teams Rooms](skype-room-systems-v2-0.md)

[Deploy Microsoft Teams Rooms](room-systems-v2.md)

[Configure a Microsoft Teams Rooms console](console.md)

[Manage Microsoft Teams Rooms](skype-room-systems-v2.md)

[Microsoft Teams Rooms Licensing](/SfbOnline/skype-for-business-and-microsoft-teams-add-on-licensing/license-options-based-on-your-plan/skype-room-systems-v2.md)
