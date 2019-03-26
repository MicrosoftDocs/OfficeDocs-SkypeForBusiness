---
title: "Configure OAuth between Skype for Business Online and Exchange on premises"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 8/8/2017
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: ffe4c3ba-7bab-49f1-b229-5142a87f94e6
description: "Configuring OAuth authentication between Exchange on premises and Skype for Business Online enables the Skype for Business and Exchange Integration features described in Feature support."
---

# Configure OAuth between Skype for Business Online and Exchange on premises

Configuring OAuth authentication between Exchange on premises and Skype for Business Online enables the Skype for Business and Exchange Integration features described in [Feature support](../../plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support).

This topic applies to Exchange Server 2016 and Exchange Server 2013.

## What do you need to know before you begin?

- Estimated time to complete this task: 15 minutes

-  You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the [Exchange and Shell infrastructure permissions](https://go.microsoft.com/fwlink/p/?LinkId=746511) topic.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center]( https://go.microsoft.com/fwlink/p/?LinkId=746512).

## Configure OAuth authentication between your on-premises Exchange and Skype for Business organizations

### Step 1: Create an authorization server object for your Skype for Business Online organization

Specify a verified domain for your Skype for Business Online organization. This domain should be the same domain used as the primary SIP domain used for the cloud-based accounts. This domain is referred as \<your Verified Domain\> in the following procedure.

Run the following command in the Exchange Management Shell (the Exchange PowerShell) in your on-premises Exchange organization.

```
New-AuthServer -Name "WindowsAzureACS" -AuthMetadataUrl "https://accounts.accesscontrol.windows.net/<your Verified Domain>/metadata/json/1"
```

### Step 2: Enable the partner application for your Skype for Business Online organization

Run the following command in the Exchange PowerShell in your on-premises Exchange organization.

```
Get-PartnerApplication | ?{$_.ApplicationIdentifier -eq "00000002-0000-0ff1-ce00-000000000000" -and $_.Realm -eq ""} | Set-PartnerApplication -Enabled $true
```

### Step 3: Create a new Mail User account for the Skype for Business Online Partner Application

This step is done on-premises. It will create a mail user and assign it the appropriate management role rights. This account will then be used in the next step.

Specify a verified domain for your Exchange organization. This domain should be the same domain used as the primary SMTP domain used for the on-premises Exchange accounts. This domain is referred as \<your Verified Domain\> in the following procedure. Also, the \<DomainControllerFQDN\> should be the FQDN of a domain controller.

```
$user = New-MailUser -Name SfBOnline-ApplicationAccount -ExternalEmailAddress SfBOnline-ApplicationAccount@<your Verified Domain> -DomainController <DomainControllerFQDN>
```

This command will hide the new mail user from address lists.

```
Set-MailUser -Identity $user.Identity -HiddenFromAddressListsEnabled $True -DomainController <DomainControllerFQDN>
```

These next two commands will assign the UserApplication and ArchiveApplication management role to this new account.

```
New-ManagementRoleAssignment -Role UserApplication -User $user.Identity -DomainController <DomainControllerFQDN>
```

```
New-ManagementRoleAssignment -Role ArchiveApplication -User $user.Identity -DomainController <DomainControllerFQDN>
```

### Step 4: Create and enable a Partner Application for Skype for Business Online

Create a new partner application and will use the account you just created. Run the following command in the Exchange PowerShell in your on-premises Exchange organization.

```
New-PartnerApplication -Name SfBOnline -ApplicationIdentifier 00000004-0000-0ff1-ce00-000000000000 -Enabled $True -LinkedAccount $user.Identity
```

### Step 5: Export the on-premises authorization certificate

Run a PowerShell script to export the on-premises authorization certificate, which you will import to your Skype for Business Online organization in the next step.

Save the following text to a PowerShell script file named, for example, ExportAuthCert.ps1.

```
$thumbprint = (Get-AuthConfig).CurrentCertificateThumbprint
if((test-path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
{
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

### Step 6: Upload the on-premises authorization certificate to Azure Active Directory ACS

Next, use Windows PowerShell to upload the on-premises authorization certificate that you exported in the previous step to Azure Active Directory Access Control Services (ACS). To do this, the Azure Active Directory Module for Windows PowerShell cmdlets must already be installed. If it's not installed, go to [https://aka.ms/aadposh](https://aka.ms/aadposh) to install the Azure Active Directory Module for Windows PowerShell. Complete the following steps after the Azure Active Directory Module for Windows PowerShell is installed.

1. Click the **Azure Active Directory Module for Windows PowerShell** shortcut to open a Windows PowerShell workspace that has the Azure AD cmdlets installed. All commands in this step will be run using the Windows PowerShell for Azure Active Directory console.

2. Save the following text to a PowerShell script file named, for example,  `UploadAuthCert.ps1`.

   ```
   Connect-MsolService;
   Import-Module msonlineextended;
   $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
   $objFSO = New-Object -ComObject Scripting.FileSystemObject;
   $CertFile = $objFSO.GetAbsolutePathName($CertFile);
   $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
   $cer.Import($CertFile);
   $binCert = $cer.GetRawCertData();
   $credValue = [System.Convert]::ToBase64String($binCert);
   $ServiceName = "00000004-0000-0ff1-ce00-000000000000";
   $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName
   New-MsolServicePrincipalCredential -AppPrincipalId $p.AppPrincipalId -Type asymmetric -Usage Verify -Value $credValue
   ```

3. Run the PowerShell script that you created in the previous step. For example:  `.\UploadAuthCert.ps1`

4. After you start the script, a credentials dialog box is displayed. Enter the credentials for the tenant administrator account of your Microsoft Online Azure AD organization. After running the script, leave the Windows PowerShell for Azure AD session open. You will use this to run a PowerShell script in the next step.

### Step 7: Register the hostname authorities for the SMTP domain

Specify a verified domain for your Exchange organization. This domain should be the same domain used as the primary SMTP domain used for the on-premises Exchange accounts. This domain is referred as \<your Verified Domain\> in the following procedure.

> [!NOTE]
> Successfully running the following script requires that the Windows PowerShell for Azure Active Directory is connected to your Microsoft Online Azure AD tenant, as explained in step 4 in the previous section.

1. Save the following text to a PowerShell script file named, for example, RegisterEndpoints.ps1. This example uses a wildcard to register all endpoints for contoso.com. Replace <your Verified Domain> with a the FQDN for your on-premises Exchange server.

   ```
   $externalAuthority="*.<your Verified Domain>"
   $ServiceName = "00000002-0000-0ff1-ce00-000000000000";
   $p = Get-MsolServicePrincipal -ServicePrincipalName $ServiceName;
   $spn = [string]::Format("{0}/{1}", $ServiceName, $externalAuthority);
   $p.ServicePrincipalNames.Add($spn);
   Set-MsolServicePrincipal -ObjectID $p.ObjectId -ServicePrincipalNames $p.ServicePrincipalNames;
   ```

2. In Windows PowerShell for Azure Active Directory, run the Windows PowerShell script that you created in the previous step. For example: `.\RegisterEndpoints.ps1`

### Verify your success

Verify that the OAuth configuration is correct by verifying some of the features are working successfully, such as having conversation history for mobile clients visible in the Outlook Conversation History folder.

1. Start the Skype for Business mobile app on your Windows Phone or iOS device and sign in as a Skype for Business Online user with an Exchange 2016 or Exchange 2013 on-premises mailbox.

2. Have an instant messaging conversation with another Skype for Business Online user.

3. Close the IM conversation window.

4. Start Outlook for this user and verify that the conversation is visible in the Outlook Conversation history folder.

Alternately, look at your traffic. The traffic in an OAuth handshake is really distinctive (and doesn't look like Basic authentication), particularly around realms, where you’ll begin to see issuer traffic that looks like this: 00000004-0000-0ff1-ce00-000000000000@ (sometimes with a / before the @ sign), in the tokens that are being passed. You won’t see a username or password, which is the point of OAuth. But you will see   the ‘Office’ issuer – in this case ‘4’ is Skype for Business – and the realm of your subscription.

If you want to be sure you’re successfully using OAuth, make certain you know what to expect and know what the traffic should look like. So [here’s what to expect](https://tools.ietf.org/html/draft-ietf-oauth-v2-23#page-34), here’s a pretty standard [example of OAuth traffic in a Microsoft application](https://download.microsoft.com/download/8/5/8/858F2155-D48D-4C68-9205-29460FD7698F/[MS-SPS2SAUTH].pdf)  (really helpful to read, though it doesn't use Refresh tokens), and there are Fiddler extensions that will let you look into your OAuth JWT (JSON Web Token).

Here's an [example of setting one up](https://blogs.msdn.microsoft.com/kaevans/2015/03/30/updated-fiddler-oauth-inspector/), but you can use any network tracing tool you like to undertake this process.

## Related topics

[Configure OAuth authentication between Exchange and Exchange Online organizations](https://docs.microsoft.com/en-us/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help)
