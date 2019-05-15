---
title: "Deploy Web downloadable clients in Skype for Business Server"
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.reviewer: PhillipGarding
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b6301e98-051c-4e4b-8e10-ec922a8f508a
description: "Summary: Deploy the Skype for Business Web App and Skype Meetings App used with Skype for Business."
---

# Deploy Web downloadable clients in Skype for Business Server

**Summary:** Deploy the Skype for Business 2015 Web App and Skype Meetings App used with Skype for Business Server.

Skype for Business Web App is an Internet Information Services (IIS) web client that is installed on the server running Skype for Business Server and by default it is deployed on demand to meeting users who do not already have the Skype for Business client. These meeting users are more often than not connecting from outside your network. Whenever a user clicks a meeting URL but does not have the Skype for Business client installed, the user is presented with the option to join the meeting by using the latest version of Skype for Business Web App, Skype Meetings App, or Skype for Business for Mac.

The voice, video, and sharing features in Skype for Business Web App require a Microsoft ActiveX control that is used as a plugin by the user's browser. You can either install the ActiveX control in advance or allow users to install it when prompted, which happens the first time they use Skype for Business Web App or the first time they access a feature that requires the ActiveX control.

> [!NOTE]
> In Skype for Business Server Edge Server deployments, an HTTPS reverse proxy in the perimeter network is required for Skype for Business Web App client access. You must also publish simple URLs. For details, see [Setting Up Reverse Proxy Servers](https://technet.microsoft.com/library/00bc138a-243f-4389-bfa5-9c62fcc95132.aspx) and [DNS requirements for simple URLs in Skype for Business Server](../../plan-your-deployment/network-requirements/simple-urls.md).

## Enable Multi-Factor Authentication for Skype for Business Web App
<a name="MFA"> </a>

Skype for Business Web App,  Skype Meetings App, and Skype for Business for Mac support multi-factor authentication. In addition to user name and password, you can require additional authentication methods, such as smart cards or PINs, to authenticate users who are joining from external networks when they sign in to Skype for Business meetings. You can enable multi-factor authentication by deploying Active Directory Federation Service (AD FS) federation server and enabling passive authentication in Skype for Business Server. After AD FS is configured, external users who attempt to join Skype for Business meetings are presented with an AD FS multi-factor authentication webpage that contains the user name and password challenge along with any additional authentication methods that you have configured.

> [!IMPORTANT]
> The following are important considerations if you plan to configure AD FS for multi-factor authentication:

- Multi-factor ADFS authentication works if the meeting participant and organizer are both in the same organization or are both from an AD FS federated organization. Multi-factor ADFS authentication does not work for Lync federated users because the Lync server web infrastructure does not currently support it.

- If you use hardware load balancers, enable cookie persistence on the load balancers so that all requests from the Skype for Business Web App or Meetings App clients are handled by the same Front End Server.

- When you establish a relying party trust between Skype for Business Server and AD FS servers, assign a token life that is long enough to span the maximum length of your Skype for Business meetings. Typically, a token life of 240 minutes is sufficient.

- This configuration does not apply to Lync mobile clients.

### Configure Multi-Factor Authentication

1. Install an AD FS federation server role. For details, see the [Active Directory Federation Services 2.0 Deployment Guide](https://go.microsoft.com/fwlink/p/?linkid=267511)

2. Create certificates for AD FS. For more information, see ["Federation server certificates"](https://go.microsoft.com/fwlink/p/?LinkId=285376) section of the Plan for and deploy AD FS for use with single sign-on topic.

3. From the Windows PowerShell command-line interface, run the following command:

    ```
    add-pssnapin Microsoft.Adfs.powershell
    ```

4. Establish a partnership by running the following command:

    ```
    Add-ADFSRelyingPartyTrust -Name ContosoApp -MetadataURL https://lyncpool.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml
    ```

5. Set the following relying party rules:

    ```
   $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.contoso.com/authorization/claims/permit", Value = "true");'$IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.contoso.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
   Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
   Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
   ```

## Disable BranchCache
<a name="MFA"> </a>

The BranchCache feature in Windows 7 and Windows Server 2008 R2 can interfere with Skype for Business Web App web components. To prevent issues for Skype for Business Web App users, make sure that BranchCache is not enabled.

For details about disabling BranchCache, see the [BranchCache Deployment Guide](https://docs.microsoft.com/windows-server/networking/branchcache/deploy/branchcache-deployment-guide).

## Verifying Skype for Business Web App Deployment
<a name="MFA"> </a>

You can use the Test-CsUcwaConference cmdlet to verify that a pair of test users can participate in a conference using the Unified Communications Web API (UCWA). For details about this cmdlet, see [Test-CsUcwaConference](https://docs.microsoft.com/powershell/module/skype/test-csucwaconference?view=skype-ps) in the Skype for Business Server Management Shell documentation.

## Troubleshooting Plug-in Installation on Windows Server 2008 R2
<a name="MFA"> </a>

If installation of the plug-in fails on a computer running Windows Server 2008 R2, you may need to modify the Internet Explorer security setting or the DisableMSI registry key setting.

### Modify the security setting in Internet Explorer

1. Open Internet Explorer.

2. Click **Tools**, click **Internet Options**, and then click **Advanced**.

3. Scroll down to the **Security** section.

4. Clear **Do not save encrypted pages to disk**, and then click **OK**.

    > [!NOTE]
    > If selected, this setting will also cause an error when trying to download an attachment from Skype for Business Web App.

5. Rejoin the meeting. The plug-in should download without errors.

### Modify the DisableMSI Registry setting

1. Click **Start**, and then click **Run**.

2. To access the Registry Editor, type **regedit**.

3. Navigate to HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Installer.

4. Edit or add the DisableMSI registry key of type REG_DWORD and set it to 0.

5. Rejoin the meeting.

## Enable Skype Meetings App to replace Skype for Business Web App (Optional, Skype for Business Server 2015 only)
<a name="SMA_Enable"> </a>

This procedure is optional, and applies to Skype for Business Server 2015 CU5 and later. If you do not use it, external users will continue to join meetings using Skype for Business Web App.

### Enable simplified meeting join and Skype Meetings App

1. When you enable access to the Content Delivery Network (CDN), users will have the ability to connect to CDN online and get Skype Meetings App (on Windows) and Skype for Business for Mac (on Mac), and will use the simplified meeting join experience.

   ```
   Set-CsWebServiceConfiguration -MeetingUxUseCdn $True
   ```

2. Allow client side logging telemetry from the meeting join web page or the Skype Meetings App to be sent to Microsoft servers (the command defaults to false).

   ```
   Set-CsWebServiceConfiguration -MeetingUxEnableTelemetry $True
   ```

    Information sent to Microsoft is in strict compliance with [Skype for Business data collection practices](https://docs.microsoft.com/skypeforbusiness/legal-and-regulatory/data-collection-practices).

3. Set the timeout before fall back to the locally hosted Skype for Business Web App experience if CDN isn't available. The default value is 6 seconds. If this value is set to 0, there will be no timeout.

   ```
   Set-CsWebServiceConfiguration -JoinLauncherCdnTimeout (New-TimeSpan -Seconds 10)
   ```

## See also
<a name="SMA_Enable"> </a>

[Plan for Meetings clients (Web App and Meetings App)](../../plan-your-deployment/clients-and-devices/meetings-clients.md)

[Configure the meeting join page in Skype for Business Server](../../manage/conferencing/meeting-join-page.md)

[Microsoft Online Services Privacy Statement](https://www.microsoft.com/en-us/privacystatement/OnlineServices/Default.aspx)

[Licensing Terms and Documentation](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;amp;DocumentTypeId=31)
