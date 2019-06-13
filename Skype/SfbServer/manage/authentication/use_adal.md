---
title: "How to use Modern Authentication (ADAL) with Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 5ca71746-ead6-4e8c-90b1-461e846d1f4a
description: "This article explains how to use Modern Authentication (which is based on the Active Directory Authentication Library (ADAL) and OAuth 2.0) that can be found in the March 2016 Cumulative Update for Skype for Business for Skype for Business Server 2015."
---

# How to use Modern Authentication (ADAL) with Skype for Business
 
This article explains how to use Modern Authentication (which is based on the Active Directory Authentication Library (ADAL) and OAuth 2.0) that can be found in the March 2016 Cumulative Update for Skype for Business for Skype for Business Server 2015, or from initial release for Skype for Business Server 2019.
  
## What's in this article?

[Configure ADAL in your pool and set AD FS as security token server](use-adal.md#BKMK_Config)
  
[Other Options for Enabling ADAL sign-in (like Office client apps)](use-adal.md#BKMK_Options)
  
[Clients where Modern Authentication / ADAL isn't Supported](use-adal.md#BKMK_Support)
  
### Configure ADAL in your pool and set AD FS as security token server
<a name="BKMK_Config"> </a>

In this process, you connect your installation of AD FS to a Skype for Business Server pool that is configured for ADAL.
  
1. Install the March 2016 Cumulative Update (or newer) for Skype for Business Server 2015 to your Skype for Business Server pool or Standard Edition server. (Schedule maintenance windows, as needed, to run Windows Update for the automatic installation.)
    
2. On your on-premises AD FS server(s), [download](https://aka.ms/sfbadalscripts) the Setup-AdfsOAuthTrustForSfB script. (This needs to be done per AD FS farm or independent AD FS server(s). It does not need to be done on AD FS Proxies or Web Application Proxies.)
    
3. Make a note of the internal and external Web Service fully qualified domain names (FQDNs) for your Skype for Business Server pool or Standard Edition server. This needs to be done for all the Skype for Business Pools.
    
4. From PowerShell on the AD FS Server(s), run `Setup-AdfsOAuthTrustForSfB.ps1` (for Windows Server 2012 R2) or `Setup-Adfs2016OAuthTrustForSfB.ps1` (for Windows Server 2016 or later.) You will need to enter the proper URLs for the internal and external Web Service fully-qualified domain names (FQDNs). Here's an example:
    
     `Setup-AdfsOAuthTrustForSfB.ps1 -poolIDs https://contosoSkype.contoso.com,https://contoso01Skype.contosoIn.com`
    
    For any additional pools, you will need to add the Pool Web Services URLs manually to the Skype for Business Server Relying Party Trust in AD FS.
    
    > [!IMPORTANT]
    > It isn't possible to use Passive Authentication for a Pool and also use ADAL. You must disable Passive Authentication in order to use ADAL. For PowerShell cmdlets on how to set authentication for a Pool see [this](https://technet.microsoft.com/en-us/library/gg398396.aspx) article.
  
    > [!TIP]
    > If you have additional pools you need to add them as [Identifiers](https://technet.microsoft.com/en-us/library/gg557759%28v=ws.10%29.aspx) to the Relying Party Trust in AD FS.> Go to your AD FS server and open AD FS Management. Expand Trust Relationships \> Relying Party Trusts. Right-click the Relying Party Trust that's listed and right-click for Properties \> Identifiers \> type the additional Pool URL(s) \> click Add. 
  
5. Return to your Skype for Business Server Front End or Standard Edition server server. From here you must run cmdlets that create an OAuth server and modify that OAuth configuration to work with Skype for Business. You only need to do this step once per Skype for Business Server deployment. Here is an example:
    
     `New-CsOAuthServer -Identity sts.contosoIn.com -Type ADFS -MetadataURL https://sts.contosoIn.com/FederationMetadata/2007-06/FederationMetadata.xml`
    
    > [!TIP]
    > The 'Identity' URL you see in this command is actually the AD FS Federation Service Name you can see in AD FS Management when you right-click Service \> Properties. The 'Type' is always 'ADFS', and the 'MetadataURL' is always \<Your AD FS service name\> + "/FederationMetadata/2007-06/FederationMetadata.xml". 
  
     `Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity sts.contosoIn.com`
    
6. Still on your Skype for Business Server Front End or Standard Edition server, test the new configuration by entering the SIP address of a user and the pool FQDN. You only need to do this step once per Skype for Business Server deployment. This is an example:
    
     `Test-CsRegistration -UserSipAddress AyakaY@contosoIns.com -TargetFqdn Pool1.contoso.com -Authentication OAuthInteractive`
    
7. When prompted, be sure to enter the credentials of the test user. Verify that the test completes successfully.
    
    > [!NOTE]
    > When your STS URL resolves to AD FS  *internally*  , the prompt you will see will be a **Windows Security** prompt. If the URL resolves externally, you'll see a prompt named **Sign in**. Typically, we would want a **Windows Security** prompt here. Note that this behaviour varies, particularly if you implemented Forms-Based Authentication (or FBA).
  
Also be aware, when the STS URL resolves to an internal AD FS server and Windows Integrated authentication is enabled in browsers, computers where many different users sign in to client applications may have failures to authenticate unless the browser is explicitly configured to prompt users for their credentials in a given browser Security Zone. Think of a kiosk as an example. The account that is logged in to the Operating System may be different than the user account logging into the Skype for Business client. If this is the case, you may see the failures described here.
    
You can see and change this browser setting in Internet Explorer by clicking \> Tools (or the Gear) \> Internet Options \> Security tab \> and the Security Zone (such as Local Intranet). From this dialog, click the Custom level button and scroll to the end of the list in the Settings dialog. Under User Authentication \> Login \> you'll see an option to 'Prompt for user name and password'. If you have kiosks where the user who starts the Skype for Business client is different (has a different account) from the user logged into the computer, you may want to test setting this option to 'ON' for these machines in a Group Policy.
    
Finally, and importantly, you may experience more than one prompt as the security system collects the information it needs to authenticate or authorize your account.
    
### Other Options for Enabling ADAL sign-in (like Office client apps)
<a name="BKMK_Options"> </a>

Now that ADAL is configured for your Skype for Business and (automatically) for Office 2016 client apps across platforms, you may want to leverage it for Exchange Online (where it is not 'On' by default), or in Office 2013 clients.
  
> [!IMPORTANT]
> Need to know what to expect from Modern Authentication sign-ins from your client apps? Take a look at [How modern authentication works for Office 2013 and Office 2016 client apps](https://support.office.com/en-us/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517?ui=en-US&amp;rs=en-US&amp;ad=US). 
  
To turn Modern Authentication on for Exchange Online, you'll need to run some PowerShell cmdlets. In the case of Office 2013 client apps, you will need to change some registry keys on client machines.
  
- Connect to Exchange Online and run the following cmdlets:
    
     `Set-OrganizationConfig -OAuth2ClientProfileEnabled:$true`
    
     `Get-OrganizationConfig | ft name, *OAuth*`
    
- Set these registry keys for every device or computer on which you want to enable Modern Authentication. You will need a GPO in larger organizations. For information on how to make a GPO, see the 'Create a Group Policy Object to modify the registry on a domain joined computer' of [this ](https://support.office.com/en-us/article/Switching-between-the-Skype-for-Business-and-the-Lync-client-user-interfaces-a2394a4c-7522-484c-a047-7b3289742be0)article.
    
|Registry Key  <br/> |Type  <br/> |Value  <br/> |
|:-----|:-----|:-----|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  <br/> |REG_DWORD  <br/> |1  <br/> |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version  <br/> |REG_DWORD  <br/> |1  <br/> |
   
Once these keys are set, set your Office apps to [use Multifactor Authentication (MFA) with Office 365](https://support.office.com/en-us/article/Set-up-multi-factor-authentication-for-Office-365-8f0454b2-f51a-4d9c-bcde-2c48e41621c6?ui=en-US&amp;rs=en-US&amp;ad=US).
  
> [!TIP]
> To disable Modern Authentication on devices for Office 2013, set the HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL registry key to a value of zero. Be aware that a similar Registry key (HKCU\SOFTWARE\Microsoft\Office\ **16.0** \Common\Identity\EnableADAL) can also be used to disable Modern Authentication on devices for Office 2016.
  
### Clients where Modern Authentication / ADAL isn't Supported
<a name="BKMK_Support"> </a>

Some client versions don't support OAuth. You can check your version of Office client in Control Panel where you Add and Remove programs in order to compare your version number to the versions (or ranges of versions) listed here:
  
- Office Client 15.0.[0000-4766].\*
    
- Office Client 16.0.[0000-4293].\*
    
- Office Client 16.0.6001.[0000-1032]
    
- Office Client 16.0.[6000-6224].\*
    
> [!NOTE]
> Hybrid Modern Authentication is also available with Skype For Business on-premises, if you want to know more, please visit [How to configure Skype for Business on-premises to use Hybrid Modern Authentication](https://docs.microsoft.com/en-us/office365/enterprise/configure-skype-for-business-for-hybrid-modern-authentication)
