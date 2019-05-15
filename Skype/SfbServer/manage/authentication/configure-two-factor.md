---
title: "Configure two-factor authentication in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: c24e0891-e108-4cb6-9902-c6a4c8e68455
description: "Summary: Configure two-factor authentication in Skype for Business Server."
---

# Configure two-factor authentication in Skype for Business Server

**Summary:** Configure two-factor authentication in Skype for Business Server.

The following sections describe the steps necessary to configure two-factor authentication for your deployment. For more information about Two-factor authentication, see [Enabling Office 365 multi-factor authentication for online administrators - Grid User Post](https://go.microsoft.com/fwlink/p/?LinkId=313332).

## Configure an Enterprise Root Certificate Authority to Support Smart Card Authentication

The following steps describe how to configure an Enterprise Root CA to support Smart Card Authentication:

For information on how to install an Enterprise Root CA, see [Install an Enterprise Root Certification Authority](https://go.microsoft.com/fwlink/p/?LinkID=313364).

1. Log in to the Enterprise CA computer using a Domain Admin account.

2. Launch System Manager, and verify that the Certificate Authority Web Enrollment role is installed.

3. From the **Administrative Tools** menu, open the **Certification Authority** management console.

4. In the Navigation pane, expand **Certification Authority**.

5. Right click on **Certificate Templates**, select **New**, then select **Certificate Template to Issue**.

6. Select **Enrollment Agent**, **Smartcard User**, and **Smartcard Logon**.

7. Click **OK**.

8. Right click on **Certificate Templates**.

9. Select **Manage**.

10. Open the properties of the Smartcard User template.

11. Click on the **Security** tab.

12. Change the permissions as follows:

    - Add individual user AD accounts with Read/Enroll (Allow) permissions, or

    - Add a security group containing smart card users with Read/Enroll (Allow) permissions, or

    - Add the Domain Users group with Read/Enroll (Allow) permissions

## Configure Windows 8 for Virtual Smart Cards

One factor to consider when deploying two-factor authentication and smart card technology is the cost of implementation. Windows 8 provides a number of new security capabilities, and one of the most interesting new features is support for virtual smart cards.

For computers equipped with a Trusted Platform Module (TPM) chip that meets specification version 1.2, organizations can now get the benefits of smart card logon without making any additional investments in hardware. For more information, see [Using Virtual Smart Cards with Windows 8](https://go.microsoft.com/fwlink/p/?LinkId=313365).

### To Configure Windows 8 for Virtual Smart Cards

1. Log in to the Windows 8 computer using the credentials of a Skype for Business-enabled user.

2. At the Windows 8 Start screen, move your cursor to the bottom right corner of the screen.

3. Select the **Search** option, and then search forCommand Prompt.

4. Right click on **Command Prompt**, and then select **Run as Administrator**.

5. Open the Trusted Platform Module (TPM) Management console by running the following command:

  ```
  Tpm.msc
  ```

6. From the TPM management console, verify that your TPM specification version is at least 1.2

    > [!NOTE]
    > If you receive a dialog stating that a Compatible Trust Platform Module (TPM) cannot be found, verify that the computer has a compatible TPM module and that it is enabled in the system BIOS.

7. Close the TPM management console

8. From the command prompt, create a new virtual smart card using the following command:

  ```
  TpmVscMgr create /name MyVSC /pin default /adminkey random /generate
  ```

    > [!NOTE]
    > To provide a custom PIN value when creating the virtual smart card, use /pin prompt instead.

9. From the command prompt, open the Computer Management console by running the following command:

  ```
  CompMgmt.msc
  ```

10. In the Computer Management console, select **Device Management**.

11. Expand **Smart card readers**.

12. Verify that the new virtual smart card reader has been created successfully.

## Enroll users for smart card authentication

There are generally two methods for enrolling users for smart card authentication. The easier method involves having users enroll directly for smart card authentication using web enrollment, while the more complex method involves using an enrollment agent. This topic focuses on self-enrollment for smartcard certificates.

For more information on enrolling on behalf of users as an enrollment agent, see [Enroll for Certificates on Behalf of Other Users](https://go.microsoft.com/fwlink/p/?LinkID=313367).

### To Enroll Users for Smart Card Authentication

1. Log in to the Windows 8 workstation using the credentials of a Skype for Business-enabled user.

2. Launch Internet Explorer.

3. Browse to the **Certificate Authority Web Enrollment** page (e.g. https://MyCA.contoso.com/certsrv).

    > [!NOTE]
    > If you are using Internet Explorer 10, you may need to view this website in Compatibility Mode.

4. On the **Welcome** Page, select **Request a certificate**.

5. Next, select **Advanced Request**.

6. Select **Create and submit a request to this CA**.

7. Select **Smartcard User** under the **Certificate Template** section and complete the advanced certificate request with the following values:

  - **Key Options** confirm he following settings:

    - Select the **Create new key set** radio button

    - For **CSP**, select **Microsoft Base Smart Card Crypto Provider**

    - For **Key Usage**, select **Exchange** (this is the only option available).

    - For **Key Size**, enter 2048

    - Confirm that **Automatic key container name** is selected

    - Leave the other boxes unchecked.

  - Under **Additional Options** confirm the following values:

    - For **Request Format** select **CMC**.

    - For **Hash Algorithm** select **sha1**.

    - For **Friendly Name** enterSmardcard Certificate.

8. If you are using a physical smartcard reader, insert the smart card into the device.

9. Click **Submit** to submit the certificate request.

10. When prompted, enter the PIN that was used to create the virtual smart card.

    > [!NOTE]
    > The default virtual smart card PIN value is '12345678'.

11. Once the certificate has been issued, click **Install this certificate** to complete the enrollment process.

    > [!NOTE]
    >  If your certificate request fails with the error "This Web browser does not support the generation of certificate requests," there are three possible ways to resolve the issue:

        a. Enable Compatibility View in Internet Explorer
        b. Enable the Turn on Intranet settings option in Internet Explorer
        c. Select the Reset all zones to default level setting under the Security tab in the Internet Explorer options menu.

## Configure Active Directory Federation Services (AD FS 2.0)

The following section describes how to configure Active Directory Federation Services (AD FS 2.0) to support multi-factor authentication. For information on how to install AD FS 2.0, see [AD FS 2.0 Step-by-Step and How To Guides](https://go.microsoft.com/fwlink/p/?LinkId=313374).

> [!NOTE]
> When installing AD FS 2.0, do not use the Windows Server Manager to add the Active Directory Federation Services role. Instead, download and install the [Active Directory Federation Services 2.0 RTW package](https://go.microsoft.com/fwlink/p/?LinkId=313375).

### To configure AD FS for two-factor Authentication

1. Log in to the AD FS 2.0 computer using a Domain Admin account.

2. Start Windows PowerShell.

3. From the Windows PowerShell command-line, run the following command:

  ```
  add-pssnapin Microsoft.Adfs.PowerShell
  ```

4. Establish a partnership with each server that will be enabled for passive authentication by running the following command, replacing the server name specific to your deployment:

  ```
  Add-ADFSRelyingPartyTrust -Name SfBPool01-PassiveAuth -MetadataURL https://SfBpool01.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml
  ```

5. From the Administrative Tools menu, launch the AD FS 2.0 Management console.

6. Expand **Trust Relationships** > **Relying Party Trusts**.

7. Verify that a new trust has been created for your Skype for Business Server.

8. Create and assign an Issuance Authorization Rule for your relying party trust using Windows PowerShell by running the following commands:

  ```
  $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "https://schemas.microsoft.com/authorization/claims/permit", Value = "true");'
  ```

  ```
  Set-ADFSRelyingPartyTrust -TargetName SfBPool01-PassiveAuth
-IssuanceAuthorizationRules $IssuanceAuthorizationRules
  ```

9. Create and assign an Issuance Transform Rule for your relying party trust using Windows PowerShell by running the following commands:

  ```
  $IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
  ```

  ```
  Set-ADFSRelyingPartyTrust -TargetName SfBPool01-PassiveAuth -IssuanceTransformRules $IssuanceTransformRules
  ```

10. From the AD FS 2.0 Management console, right click on your relying party trust and select **Edit Claim Rules**.

11. Select the **Issuance Authorization Rules** tab and verify that the new authorization rule was created successfully.

12. Select the **Issuance Transform Rules** tab and verify that the new transform rule was created successfully.

## Configuring AD FS 2.0 to support client authentication

There are two possible authentication types that can be configured to allow AD FS 2.0 to support authentication using smart cards:

- Forms-based authentication (FBA)

- Transport Layer Security Client Authentication

Using forms-based authentication, you can develop a web page that allows users to authenticate either by using their username/password or by using their smart card and PIN. This topic focuses on how to implement Transport Layer Security Client Authentication with AD FS 2.0. For more information about AD FS 2.0 authentication types, see [AD FS 2.0: How to Change the Local Authentication Type](https://go.microsoft.com/fwlink/p/?LinkId=313384).

### To Configure AD FS 2.0 to Support Client Authentication

1. Log in to the AD FS 2.0 computer using a Domain Admin account.

2. Launch Windows Explorer.

3. Browse to C:\inetpub\adfs\ls

4. Make a backup copy of the existing web.config file.

5. Open the existing web.config file using Notepad.

6. From the Menu bar, select **Edit** and then select **Find**.

7. Search for \<localAuthenticationTypes\>.

    Note that there are four authentication types listed, one per line.

8. Move the line containing the TLSClient authentication type to the top of the list in the section.

9. Save and Close the web.config file.

10. Launch a Command Prompt with elevated privileges.

11. Restart IIS by running the following command:

  ```
  IISReset /Restart /NoForce
  ```

## Configuring Skype for Business Server passive authentication

The following section describes how to configure Skype for Business Server to support passive authentication. Once enabled, users who are enabled for two-factor authentication will be required to use a physical or virtual smart card and a valid PIN to sign in using the Skype for Business client.

> [!NOTE]
> It is strongly recommended that customers enable passive authentication for Registrar and Web Services at the service level. If passive authentication is enabled for Registrar and Web Services at the global level, it will likely result in organization-wide authentication failures for users who are not signing in with the supported desktop client.

### Web Service Configuration

The following steps describe how to create a custom web service configuration for Directors, Enterprise Pools, and Standard Edition servers that will be enabled for passive authentication.

### To create a custom web service configuration

1. Log in to your Skype for Business Server Front End server using a Skype for Business administrator account.

2. Launch the Skype for Business Server Management Shell.

3. From the Skype for Business Server Management Shell command-line, create a new Web Service configuration for each Director, Enterprise Pool, and Standard Edition server that will be enabled for passive authentication by running the following command:

  ```
  New-CsWebServiceConfiguration -Identity "Service:WebServer:SfBPool01.contoso.com" -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
  ```

    > [!CAUTION]
    > The value for the WsFedPassiveMetadataUri FQDN is the Federation Service Name of your AD FS 2.0 server. The Federation Service Name value can be found in the AD FS 2.0 Management Console by right-clicking on **Service** from the navigation pane and then selecting **Edit Federation Service Properties**.

4. Verify that the UseWsFedPassiveAuth and WsFedPassiveMetadataUri values were set correctly by running the following command:

  ```
  Get-CsWebServiceConfiguration -identity "Service:WebServer:SfBPool01.contoso.com" | format-list UseWsFedPassiveAuth, WsFedPassiveMetadataUri
  ```

5. For clients, Passive Authentication is the least preferred authentication method for webticket authentication. For all Directors, Enterprise Pools, and Standard Edition servers that will be enabled for passive authentication, all other authentication types must be disabled in Skype for Business Web Services by running the following cmdlet:

  ```
  Set-CsWebServiceConfiguration -Identity "Service:WebServer:SfBPool01.contoso.com" -UseCertificateAuth $false -UsePinAuth $false -UseWindowsAuth NONE
  ```

6. Verify that all other authentication types have been successfully disabled by running the following cmdlet:

  ```
  Get-CsWebServiceConfiguration -Identity "Service:WebServer:SfBPool01.contoso.com" | format-list UseCertificateAuth, UsePinAuth, UseWindowsAuth
  ```

### Proxy Configuration

When certificate authentication is disabled for Skype for Business Web Services, the Skype for Business client will use a less preferred authentication type, such as Kerberos or NTLM, to authenticate to the Registrar service. Certificate authentication is still needed to allow the client to retrieve a webticket, however, Kerberos and NTLM must be disabled for the Registrar service.

The following steps describe how to create a custom proxy configuration for Edge Pools, Enterprise Pools, and Standard Edition servers that will be enabled for passive authentication.

### To create a custom proxy configuration

1. From the Skype for Business Server Management Shell command-line, create a new proxy configuration for each Skype for Business Server Edge Pool, Enterprise Pool, and Standard Edition server that will be enabled for passive authentication by running the following commands:

  ```
  New-CsProxyConfiguration -Identity "Service:EdgeServer:EdgePool01.contoso.com" -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
  ```

  ```
  New-CsProxyConfiguration -Identity "Service:Registrar:SfBPool01.contoso.com" -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
  ```

2. Verify that all other proxy authentication types have been successfully disabled by running the following command:

  ```
  Get-CsProxyConfiguration -Identity "Service:Registrar:SfBPool01.contoso.com" | format-list UseKerberosForClientToProxyAuth, UseNtlmForClientToProxyAuth, UseCertifcateForClientToProxyAuth
  ```

## See also

[Manage two-factor authentication in Skype for Business Server](two-factor-authentication.md)

[Use two-factor authentication with Skype for Business client and Skype for Business Server](use-two-factor.md)
