---
title: "Deploying Lync Web App in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b6301e98-051c-4e4b-8e10-ec922a8f508a
description: "In this articleEnabling Multi-Factor Authentication for Lync Web AppBranchCache ConfigurationVerifying Lync Web App DeploymentTroubleshooting Plug-in Installation on Windows Server 2008 R2"
---

# Deploying Lync Web App in Lync Server 2013
[]
 **In this article**
  
[Enabling Multi-Factor Authentication for Lync Web App](#sectionSection0)
  
[BranchCache Configuration](#sectionSection1)
  
[Verifying Lync Web App Deployment](#sectionSection2)
  
[Troubleshooting Plug-in Installation on Windows Server 2008 R2](#sectionSection3)
  
Lync Web App is an Internet Information Services (IIS) web client that installs with Lync Server 2013 and is enabled by default. No additional steps are necessary to either enable Lync Web App on the server or deploy the web client to users. Whenever a user clicks a meeting URL but does not have the Lync 2013 client installed, the user is presented with the option to join the meeting by using the latest version of Lync Web App.
  
The voice, video, and sharing features in Lync Web App require a Microsoft ActiveX control. You can either install the ActiveX control in advance or allow users to install it when prompted, which happens the first time they use Lync Web App or the first time they access a feature that requires the ActiveX control.
  
> [!NOTE]
> In Lync Server 2013 Edge Server deployments, an HTTPS reverse proxy in the perimeter network is required for Lync Web App client access. You must also publish simple URLs. For details, see [Setting up reverse proxy servers for Lync Server 2013](setting-up-reverse-proxy-servers.md) and [Planning for simple URLs in Lync Server 2013](planning-for-simple-urls.md). 
  
## Enabling Multi-Factor Authentication for Lync Web App
<a name="sectionSection0"> </a>

The Lync Server 2013 version of Lync Web App supports multi-factor authentication. In addition to user name and password, you can require additional authentication methods, such as smart cards or PINs, to authenticate users who are joining from external networks when they sign in to Lync meetings. You can enable multi-factor authentication by deploying Active Directory Federation Service (AD FS) federation server and enabling passive authentication in Lync Server 2013. After AD FS is configured, external users who attempt to join Lync meetings are presented with an AD FS multi-factor authentication webpage that contains the user name and password challenge along with any additional authentication methods that you have configured.
  
> [!IMPORTANT]
>  The following are important considerations if you plan to configure AD FS for multi-factor authentication: >  Multi-factor ADFS authentication works if the meeting participant and organizer are both in the same organization or are both from an AD FS federated organization. Multi-factor ADFS authentication does not work for Lync federated users because the Lync server web infrastructure does not currently support it. >  If you use hardware load balancers, enable cookie persistence on the load balancers so that all requests from the Lync Web App client are handled by the same Front End Server. >  When you establish a relying party trust between Lync Server and AD FS servers, assign a token life that is long enough to span the maximum length of your Lync meetings. Typically, a token life of 240 minutes is sufficient. >  This configuration does not apply to Lync mobile clients. 
  
### To Configure Multi-Factor Authentication

1. Install an AD FS federation server role. For details, see the Active Directory Federation Services 2.0 Deployment Guide at [https://go.microsoft.com/fwlink/p/?linkid=267511](https://go.microsoft.com/fwlink/p/?linkid=267511)
    
2. Create certificates for AD FS. For more information, see the "Federation server certificates" section of the Plan for and deploy AD FS for use with single sign-on topic at [https://go.microsoft.com/fwlink/p/?LinkId=285376](https://go.microsoft.com/fwlink/p/?LinkId=285376).
    
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
  ```

  ```
  Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
  ```

  ```
  Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
  ```

## BranchCache Configuration
<a name="sectionSection1"> </a>

The BranchCache feature in Windows 7 and Windows Server 2008 R2 can interfere with Lync Web App web components. To prevent issues for Lync Web App users, make sure that BranchCache is not enabled. 
  
For details about disabling BranchCache, see the BranchCache Deployment Guide, which is available in Word format at the Microsoft Download Center at [http://go.microsoft.com/fwlink/p/?LinkId=268788](http://go.microsoft.com/fwlink/p/?LinkId=268788) and in HTML format in the Windows Server 2008 R2 Technical Library at [https://go.microsoft.com/fwlink/p/?LinkId=268789](https://go.microsoft.com/fwlink/p/?LinkId=268789).
  
## Verifying Lync Web App Deployment
<a name="sectionSection2"> </a>

You can use the Test-CsUcwaConference cmdlet to verify that a pair of test users can participate in a conference using the Unified Communications Web API (UCWA). For details about this cmdlet, see [Test-CsUcwaConference](test-csucwaconference.md) in the Lync Server Management Shell documentation. 
  
## Troubleshooting Plug-in Installation on Windows Server 2008 R2
<a name="sectionSection3"> </a>

If installation of the plug-in fails on a computer running Windows Server 2008 R2, you may need to modify the Internet Explorer security setting or the DisableMSI registry key setting.
  
### To modify the security setting in Internet Explorer

1. Open Internet Explorer.
    
2. Click **Tools**, click **Internet Options**, and then click **Advanced**.
    
3. Scroll down to the **Security** section. 
    
4. Clear **Do not save encrypted pages to disk**, and then click **OK**.
    
    > [!NOTE]
    > If selected, this setting will also cause an error when trying to download an attachment from Lync Web App. 
  
5. Rejoin the meeting. The plug-in should download without errors.
    
### To modify the DisableMSI Registry setting

1. Click **Start**, and then click **Run**.
    
2. To access the Registry Editor, type **regedit**.
    
3. Navigate to HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Installer.
    
4. Edit or add the DisableMSI registry key of type REG_DWORD and set it to 0.
    
5. Rejoin the meeting.
    
## See also
<a name="sectionSection3"> </a>

#### 

[Configuring the meeting join page in Lync Server 2013](configuring-the-meeting-join-page.md)
  
[Lync Web App supported platforms for Lync Server 2013](lync-web-app-supported-platforms.md)

