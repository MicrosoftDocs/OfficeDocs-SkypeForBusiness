---
title: "Configure client bootstrapping policies"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 45042eca-b845-4207-b12f-b8b7f5d44bdf

description: "Summary: How to manage Group Policies."
---

# Configure client bootstrapping policies
 
**Summary:** How to manage Group Policies.
  
The Group Policy Management Console (GPMC) and the Group Policy Object Editor are tools that you use to manage Group Policy. Included with the Office Group Policy Administrative Template are lync16.admx (ADMX) and .adml (ADML) Administrative Templates, which contain the registry-based policy settings for Skype for Business that you configure for Group Policy objects in the domain. ADML files are language-specific complements to ADMX files. Each ADMX and ADML file contains the policy settings for a single Office application. You can [download the Office 2016 Administrative Template files (ADMX/ADML)](https://www.microsoft.com/en-us/download/details.aspx?id=49030) for free from the Microsoft Download Center.
  
For Skype for Business clients, there are several client bootstrapping policies that you should consider configuring before users sign in to the server for the first time. For example, the default servers and security mode that the client should use until sign-in is complete. You can use Group Policy to establish these settings in users' computer registries before they sign in and begin receiving in-band provisioning settings from the server. The following table lists the Group Policy settings that are available for Skype for Business.
  
**Group Policy Settings for Skype for Business**

|Group Policy setting|Description|
|:-----|:-----|
|Specify Server           (ConfigurationMode)  <br/> | Specifies how Skype for Business identifies the transport and server to use during sign-in. Within this setting, you specify the following: <br/>  ServerAddressExternal: Specifies the server name or IP address used by clients and federated contacts when connecting from outside the external firewall. <br/>  ServerAddressInternal: Specifies the server name or IP address used when clients connect from inside the organization's firewall. <br/>  Transport: Specifies either Transmission Control Protocol (TCP) or Transport Layer Security (TLS). <br/> |
|Additional server versions supported           (ConfiguredServerCheckValues)  <br/> |Specifies a list of server version names separated by semi-colons that Skype for Business Server will log on to, in addition to the server versions that are supported by default.  <br/> |
|Disable automatic upload of sign-in failure logs (DisableAutomaticSendTracing)  <br/> |Automatically uploads sign-in failure logs to Skype for Business Server for analysis. No logs are automatically uploaded if sign-in is successful. If this policy is not configured, the following happens:  <br/> For Skype for Business Online users: Sign-in failure logs are automatically uploaded. For Skype for Business on-premises users: A confirmation dialog box is shown to the user before upload. When this setting is disabled, sign-in logs are automatically uploaded to the Skype for Business Server for both Skype for Business on-premises and Skype for Business Online users. When this setting is enabled, sign-in logs are never uploaded automatically.  <br/> |
|Disable HTTP fallback for SIP connection           (DisableHttpConnect)  <br/> |Prevents Skype for Business Server from trying to connect to the server by using HTTP, if TLS or TCP are unavailable. By default, Skype for Business first attempts to connect to the server by using TLS or TCP and, if neither of these transport methods is successful, Skype for Business tries to connect by using HTTP. Use this policy to disable the fallback HTTP connection attempt.  <br/> |
|Require logon credentials           (DisableNTCredentials)  <br/> |Requires the user to provide logon credentials for Skype for Business rather than automatically using Windows credentials during sign-in to a SIP server.  <br/> |
|Disable server version check           (DisableServerCheck)  <br/> |If you set this policy to 1, prevents Skype for Business from checking the server name and version before signing in. By default, Skype for Business makes these checks before signing in.  <br/> |
|Enable using BITS to download Address Book Service files           (EnableBitsForGalDownload)  <br/> |Enables Skype for Business to use Background Intelligent Transfer Service (BITS) to download the Address Book Services files.  <br/> |
|Configure SIP security mode           (EnableSIPHighSecurityMode)  <br/> |Enables Skype for Business to send and receive instant messages more securely. This policy has no effect on Windows .NET or Microsoft Exchange Server services.  <br/> If you do not configure this policy setting, Skype for Business can use any transport. But if it does not use TLS and if the server authenticates users, Skype for Business must use either NTLM or Kerberos authentication.  <br/> |
|Global Address Book Download Initial Delay           (GalDownloadInitialDelay)  <br/> |Specifies the time period before a download of the global address list (GAL) occurs. The default value is 60 minutes, which means the server delays the download of GAL file for a random period of between 0 and 60 minutes.  <br/> |
|Prevent users from running Skype for Business           (PreventRun)  <br/> |Prevents users from running Skype for Business. You can configure this policy setting under both Computer Configuration and User Configuration, but the policy setting under Computer Configuration takes precedence.  <br/> |
|Allow storage of user passwords           (SavePassword)  <br/> |Enables Skype for Business to store passwords.  <br/> |
|Configure SIP compression mode           (SipCompression)  <br/> |Specifies when to turn on SIP compression. By default, SIP compression is enabled based on the adapter speed. Note that setting this policy might cause an increase in sign-in time.  <br/> |
|Trusted Domain List           (TrustModelData)  <br/> |Lists the trusted domains that do not match the prefix of the customer SIP domain.  <br/> |
   
Policies configured on the server take precedence over Group Policy settings and client options configured by the user. The following table summarizes the order in which settings take precedence when a conflict occurs.
  
**Group Policy Precedence**

|**Precedence**|**Location or Method of Setting**|
|:-----|:-----|
|1  <br/> |Skype for Business Server in-band provisioning  <br/> |
|2  <br/> |HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\16.0\Lync  <br/> |
|3  <br/> |HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Office\16.0\Lync  <br/> |
|4  <br/> |The Options dialog box in Skype for Business  <br/> |
   
### To define Group Policy settings by using the Skype for Business administrative template files

1. Create a root-level folder to contain all language-neutral ADMX files. For example, create the root folder for the central store on your domain controller at this location:
    
     `%systemroot%\sysvol\domain\policies\PolicyDefinitions`
    
    > [!NOTE]
    > This procedure assumes that you want to manage multiple computers in your domain. In this case, you store the templates in a central store in the Sysvol folder on the primary domain controller. This provides a replicated central storage location for domain Administrative Templates. 
  
2. Create a subfolder for each language that you'll use. These subfolders will contain the language-specific ADML resource files. For example, create a subfolder for United States English (EN-US) at this location:
    
     `%systemroot%\sysvol\domain\policies\PolicyDefinitions\EN-US`
    

