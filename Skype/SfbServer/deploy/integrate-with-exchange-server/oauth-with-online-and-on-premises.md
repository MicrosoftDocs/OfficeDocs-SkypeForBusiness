---
title: "Integration between Skype for Business Online and Exchange server"
ms.reviewer: cbland
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 02/17/2022
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom:
  - has-azure-ad-ps-ref
ms.collection: IT_Skype16
ms.assetid: ffe4c3ba-7bab-49f1-b229-5142a87f94e6
description: "Configuring OAuth authentication between Exchange on premises and Skype for Business Online enables the Skype for Business and Exchange Integration features described in Feature support."
---

# Configure Integration and OAuth between Skype for Business Online and Exchange Server 

Configuring integration between Exchange server and Skype for Business Online enables the Skype for Business and Exchange Integration features described in [Feature support](../../plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support).

This topic applies to integration with Exchange Server 2013 through 2019.

## What do you need to know before you begin?

- Estimated time to complete this task: 15 minutes

-  You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the [Exchange and Shell infrastructure permissions](/exchange/exchange-and-shell-infrastructure-permissions-exchange-2013-help) topic.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center]( https://go.microsoft.com/fwlink/p/?LinkId=746512).

- For information about compatibility, see [Skype for Business compatibility with Office apps](../../plan-your-deployment/clients-and-devices/compatibility-with-office.md).

## Configure integration between Exchange Server and O365

### Step 1: Configure OAuth authentication between Exchange Server and O365

Perform the steps in the following article:

[Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help)

### Step 2: Create a new Mail User account for the Skype for Business Online Partner Application

This step is done on the Exchange server. It will create a mail user and assign it the appropriate management role rights. This account will then be used in the next step.

Specify a verified domain for your Exchange organization. This domain should be the same domain used as the primary SMTP domain used for the on-premises Exchange accounts. This domain is referred as \<your Verified Domain\> in the following procedure. Also, the \<DomainControllerFQDN\> should be the FQDN of a domain controller.

```powershell
$user = New-MailUser -Name SfBOnline-ApplicationAccount -ExternalEmailAddress SfBOnline-ApplicationAccount@<your Verified Domain> -DomainController <DomainControllerFQDN>
```

This command will hide the new mail user from address lists.

```powershell
Set-MailUser -Identity $user.Identity -HiddenFromAddressListsEnabled $True -DomainController <DomainControllerFQDN>
```

These next two commands will assign the UserApplication and ArchiveApplication management role to this new account.

```powershell
New-ManagementRoleAssignment -Role UserApplication -User $user.Identity -DomainController <DomainControllerFQDN>
```

```powershell
New-ManagementRoleAssignment -Role ArchiveApplication -User $user.Identity -DomainController <DomainControllerFQDN>
```

### Step 3: Create and enable a Partner Application for Skype for Business Online 

Create a new partner application and will use the account you just created. Run the following command in the Exchange PowerShell in your on-premises Exchange organization.

```powershell
New-PartnerApplication -Name SfBOnline -ApplicationIdentifier 00000004-0000-0ff1-ce00-000000000000 -Enabled $True -LinkedAccount $user.Identity
```

### Step 4: Export the on-premises authorization certificate

Run a PowerShell script to export the on-premises authorization certificate, which you will import to your Skype for Business Online organization in the next step.

Save the following text to a PowerShell script file named, for example, ExportAuthCert.ps1.

```powershell
$thumbprint = (Get-AuthConfig).CurrentCertificateThumbprint
if((test-path $env:SYSTEMDRIVE\OAuthConfig) -eq $false) {
    md $env:SYSTEMDRIVE\OAuthConfig
}
cd $env:SYSTEMDRIVE\OAuthConfig
$oAuthCert = (dir Cert:\LocalMachine\My) | where {$_.Thumbprint -match $thumbprint}
$certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
$certBytes = $oAuthCert.Export($certType)
$CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
[System.IO.File]::WriteAllBytes($CertFile, $certBytes)
```

In Exchange PowerShell in your on-premises Exchange organization, run the PowerShell script that you just created. For example: .\ExportAuthCert.ps1

<a name='step-5-upload-the-on-premises-authorization-certificate-to-azure-active-directory-acs'></a>

### Step 5: Upload the on-premises authorization certificate to Microsoft Entra ACS

Next, use Windows PowerShell to upload the on-premises authorization certificate that you exported in the previous step to Microsoft Entra Access Control Services (ACS). To do this, the Azure Active Directory module for Windows PowerShell cmdlets must already be installed. If it's not installed, go to [https://aka.ms/aadposh](/previous-versions/azure/jj151815(v=azure.100)) to install the Azure Active Directory module for Windows PowerShell. Complete the following steps after the Azure Active Directory module for Windows PowerShell is installed.

1. Click the **Azure Active Directory module for Windows PowerShell** shortcut to open a Windows PowerShell workspace that has the Microsoft Entra cmdlets installed. All commands in this step will be run using the Windows PowerShell for Microsoft Entra ID console.

2. Save the following text to a PowerShell script file named, for example,  `UploadAuthCert.ps1`.

   ```powershell
   Connect-MsolService
   Import-Module MSOnline
   $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
   $objFSO = New-Object -ComObject Scripting.FileSystemObject
   $CertFile = $objFSO.GetAbsolutePathName($CertFile);
   $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
   $cer.Import($CertFile)
   $binCert = $cer.GetRawCertData();
   $credValue = [System.Convert]::ToBase64String($binCert)
   $ServiceName = "00000004-0000-0ff1-ce00-000000000000"
   $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName
   New-MsolServicePrincipalCredential -AppPrincipalId $p.AppPrincipalId -Type asymmetric -Usage Verify -Value $credValue
   ```

3. Run the PowerShell script that you created in the previous step. For example:  `.\UploadAuthCert.ps1`

4. After you start the script, a credentials dialog box is displayed. Enter the credentials for the tenant administrator account of your Microsoft Online Microsoft Entra organization. After running the script, leave the Windows PowerShell for Microsoft Entra session open. You will use this to run a PowerShell script in the next step.

### Step 6: Verify that the Certificate has Uploaded to the Skype for Business Service Principal
1. In the PowerShell opened and authenticated to Microsoft Entra ID, run the following

   ```powershell
   Get-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
   ```
2. Press Enter when prompted for ReturnKeyValues
3. Confirm you see a key listed with start date and end data that matches your Exchange Oauth certificate start and end dates

### Verify your success

Verify that the configuration is correct by verifying some of the features are working successfully. 

1. Confirm that Skype for Business users with Cloud Voicemail service, in an organization with a Hybrid Exchange Server configuration, can successfully change their voicemail greetings.

2. Confirm conversation history for mobile clients is visible in the Outlook Conversation History folder.

3. Confirm that archived chat messages are deposited in the user's on-premises mailbox in the Purges folder using [EWSEditor](/archive/blogs/webdav_101/where-to-get-ewseditor).

Alternately, look at your traffic. The traffic in an OAuth handshake is really distinctive (and doesn't look like Basic authentication), particularly around realms, where you’ll begin to see issuer traffic that looks like this: 00000004-0000-0ff1-ce00-000000000000@ (sometimes with a / before the @ sign), in the tokens that are being passed. You won’t see a username or password, which is the point of OAuth. But you will see   the ‘Office’ issuer – in this case ‘4’ is Skype for Business – and the realm of your subscription.

If you want to be sure you’re successfully using OAuth, make certain you know what to expect and know what the traffic should look like. So [here’s what to expect](https://tools.ietf.org/html/draft-ietf-oauth-v2-23#page-34).

Here's an [example of setting one up](/archive/blogs/kaevans/updated-fiddler-oauth-inspector), but you can use any network tracing tool you like to undertake this process.

## Related topics

[Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help)
