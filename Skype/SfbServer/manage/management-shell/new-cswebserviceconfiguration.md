---
title: "New-CsWebServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/4/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6225cf8d-b669-464e-9848-a292953e3a3a
description: "Creates a new collection of Web Services configuration settings. This cmdlet was introduced in Lync Server 2010."
---

# New-CsWebServiceConfiguration
 
Creates a new collection of Web Services configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsWebServiceConfiguration -Identity <XdsIdentity> [-AllowAnonymousAccessToLWAConference <$true | $false>] [-AllowExternalAuthentication <$true | $false>] [-AutoLaunchLyncWebAccess <$true | $false>] [-CASigningKeyLength <UInt64>] [-Confirm [<SwitchParameter>]] [-CorsPreflightResponseMaxAgeInSeconds <Int64>] [-CrossDomainAuthorizationList <PSListModifier>] [-DefaultValidityPeriodHours <UInt64>] [-EnableCertChainDownload <$true | $false>] [-EnableCORS <$true | $false>] [-EnableGroupExpansion <$true | $false>] [-EnableMediaBasicAuth <$true | $false>] [-EnableStatisticsInResponse <$true | $false>] [-Force <SwitchParameter>] [-HstsMaxAgeInSeconds <Int64>] [-InferCertChainFromSSL <$true | $false>] [-InMemory <SwitchParameter>] [-JoinLauncherCdnConfigUri <String>] [-JoinLauncherCdnTimeout <TimeSpan>] [-LWACdnConfigUri <String>] [-MACResolverUrl <String>] [-MaxCSRKeySize <UInt64>] [-MaxGroupSizeToExpand <UInt32>] [-MaxValidityPeriodHours <UInt64>] [-MeetingUxEnableTelemetry <$true | $false>] [-MeetingUxUseCdn <$true | $false>] [-MinCSRKeySize <UInt64>] [-MinValidityPeriodHours <UInt64>] [-MobilePreferredAuthType <None | OAuth | WebTicketServiceAnon | WebTicketServiceWinNegotiate | WebTicketServiceWinNtlm | WebTicketServiceCert | WebTicketServicePin | WsFedPassive | WsFedBearer | WebTicketServiceAuth>] [-OverrideAuthTypeForExternalClients <String>] [-OverrideAuthTypeForInternalClients <String>] [-SecondaryLocationSourceUrl <String>] [-ShowAlternateJoinOptionsExpanded <$true | $false>] [-ShowDownloadCommunicatorAttendeeLink <$true | $false>] [-ShowJoinUsingLegacyClientLink <$true | $false>] [-TrustedCACerts <PSListModifier>] [-UseCertificateAuth <$true | $false>] [-UseDomainAuthInLWA <$true | $false>] [-UsePinAuth <$true | $false>] [-UseWebClientLegacyUI <$true | $false>] [-UseWindowsAuth <None | Negotiate | NTLM>] [-UseWsFedPassiveAuth <$true | $false>] [-WhatIf [<SwitchParameter>]] [-WsFedPassiveMetadataUri <String>]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 creates a new collection of Web Services configuration settings for the Redmond site (-Identity site:Redmond). This example includes two optional parameters: EnableGroupExpansion, which is set to False ($False); and UseCertificateAuth, which is set to True ($True). These two parameters are used to disable group expansion and enable the use of certificates for authentication, respectively.
  
Note that this command will fail if a collection of Web Services configuration settings has already been created for the Redmond site. That's because sites are limited to a single collection of Web Services configuration settings.
  
```
New-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $False -UseCertificateAuth $True
```

### EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the new collection of Web Services configuration settings is initially created in memory only, and is only later applied to the Redmond site. In order to do this, the first command in the example uses the **New-CsWebServiceConfiguration** cmdlet to create a collection of settings for the Redmond site; the InMemory parameter is included to ensure that this collection is created in memory only and is not immediately applied to the Redmond site. (Because the settings exist only in memory, they must be stored in a variable. In this case, that's a variable named $x.)
  
Commands 2 and 3 in the example take these virtual configuration settings and modify the values of the EnableGroupExpansion and UseCertificateAuth properties. After these changes have been made, the final command uses the **Set-CsWebServiceConfiguration** cmdlet to take the virtual settings and apply them to the Redmond site. If you do not call the **Set-CsWebServiceConfiguration** cmdlet, no new settings will be assigned to the site. Instead, your virtual Web Services configuration settings will disappear as soon as you end your Windows PowerShell session or delete the variable $x.
  
```
$x = New-CsWebServiceConfiguration -Identity site:Redmond -InMemory
$x.EnableGroupExpansion = $False 
$x.UseCertificateAuth = $True
Set-CsWebServiceConfiguration -Instance $x
```

### EXAMPLE 3

The commands shown in Example 3 add the domain http://fabrikam.com to the authorized domains list for a new collection of Web service configuration settings being created for the Redmond site. To do this, the first command in the example uses the **New-CsWebOrigin** cmdlet to create a domain object for fabrikam.com. The resulting domain object is stored in a variable named $x.
  
The second command in the example uses the **New-CsWebServiceConfiguration** cmdlet to create the Web service configuration settings for the Redmond site. The syntax - CrossDomainAuthorizationList $x adds http://fabrikam.com to the collection of domains authorized for cross-domain scripting.
  
```
$x = New-CsWebOrigin -Url "http://fabrikam.com"
New-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $x
```

### EXAMPLE 4

Example 4 shows how you can add multiple authorized domains to a new collection of Web service configuration settings. To add multiple domains, you must create multiple domain objects, storing each in a separate variable. In Example 4, the domain object for http://fabrikam.com is stored in a variable named $x, while the domain object for http://contoso.com is stored in a variable named $y.
  
After all the domain objects have been created, all you need to do is include each variable name in the parameter value for the CrossDomainAuthorizationList parameter. For example:
  
-CrossDomainAuthorizationList $x, $y
  
```
$x = New-CsWebOrigin -Url "http://fabrikam.com"
$y = New-CsWebOrigin -Url "http://contoso.com"
New-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $x, $y
```

## Detailed Description

Many Skype for Business Server 2015 components are web-based: these components either use Web Services or webpages to carry out their tasks. For example, users employ a Web service when searching for new contacts in the Address Book or when using group expansion to view the individual members of a distribution group. Likewise, components ranging from dial-in conferencing to Skype for Business Server 2015 use web pages as the interface between Skype for Business Server Control Panel and users. 
  
The **CsWebServiceConfiguration** cmdlets enable administrators to manage Web Services configuration settings throughout the organization. This includes managing group expansion, certificate settings, and allowed authentication methods. Because you can configure different settings at the global, site, and service scope (albeit for only the Web Services service), you can customize Web Services capabilities for different users and different locations.
  
New Web Services configuration settings are created by using the **New-CsWebServiceConfiguration** cmdlet. Note that these settings can only be created at the site or service scope (and only for the Web Services service); your command will fail if you try to create a new collection at the global scope. Likewise, your command will fail if you try to create a new collection at, for instance, the Redmond site, and that site already hosts a collection of Web service settings.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Web Services configuration settings to be created. To create settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To create settings configured at the service scope, use syntax similar to this:  <br/>  `-Identity "service:WebServer:atl-cs-001.litwareinc.com"` <br/> Note that any settings created at the service scope must be assigned to the Web Server service.  <br/> |
| _AllowAnonymousAccessToLWAConference_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), anonymous users will be allowed to attend Skype for Business web App conferences.  <br/> |
| _AllowExternalAuthentication_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), OAuth authentication can be used to authenticate external users.  <br/> |
| _AutoLaunchLyncWebAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> When set to True, Skype for Business Web App will automatically be used as the default web popup for joining an online conference, provided that the prerequisites for using Skype for Business Web App (for example, Silverlight have been installed, and Internet Explorer is not blocking pop-up windows) have been met.  <br/> The default value is True.  <br/> |
| _CASigningKeyLength_ <br/> |Optional  <br/> |System.UInt64  <br/> |Sets the size of the certification authority (CA) signing key, the private key used by a CA to sign digital certificates. The signing key length can be set to any integer value between 2048 and 16384 bytes; the default value is 2048.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CorsPreflightResponseMaxAgeInSeconds_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _CrossDomainAuthorizationList_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of domains allowed to host web applications that send cross-domain scripting requests to the Skype for Business Server 2015 deployment.  <br/> Domains to be added to the list must be created using the New-CsWebOrigin cmdlet and then added to the new collection of Web service configuration settings. Domain names must be prefaced using the http: or the https: prefix. See Example 3 of this help topic for more information.  <br/> This parameter was introduced in the February, 2013 release of Lync Server 2013.  <br/> |
| _DefaultValidityPeriodHours_ <br/> |Optional  <br/> |System.UInt64  <br/> |When using certificate authentication, clients can request the period of time (in hours) that the certificate remains valid. DefaultValidityPeriodHours represents the amount of time a certificate will remain valid if the client does not request a custom validity period.  <br/> DefaultValidityPeriodHours can be any integer value between 8 hours and 8760 hours (365 days). The default value is 4320 (180 days).  <br/> |
| _EnableCertChainDownload_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, servers presented with an authentication certificate will download the certificate chain for that certificate. The certificate chain traces an individual certificate back to the issuing CA. Certificates will not be accepted for authentication unless the certificate's CA is trusted.  <br/> |
| _EnableCORS_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableGroupExpansion_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, group expansion will be enabled in Skype for Business. With group expansion, users can configure a distribution group as a contact, and then "expand" that group. When a group has been expanded, users can see all the individual members of a group and their current presence information.  <br/> |
| _EnableMediaBasicAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableStatisticsInResponse_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) the X-MS-WebInfraStats header is included in all HTTP responses. The default value is False ($False).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _HstsMaxAgeInSeconds_ <br/> |Optional  <br/> |System.Int64  <br/> |Specifies the time in seconds of the  _max-age_ setting in the Strict-Transport-Security (STS) header of an HTTPS response. A negative value will suppress the STS header in the HTTPS response. The default is 315,360,000 (one year.) <br/> |
| _InferCertChainFromSSL_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, servers will use the certificate information included in the Secure Sockets Layer (SSL) protocol to determine the issuing CA. Certificates will not be accepted for authentication unless the certificate's CA is trusted.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _JoinLauncherCdnConfigUri_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _JoinLauncherCdnTimeout_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |PARAMVALUE: TimeSpan  <br/> |
| _LWACdnConfigUri_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _MACResolverUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for a Web service capable of performing Media Access Control (MAC) resolution. MAC resolution involves taking the MAC address of a connected client and returning the chassis and port IDs of the network switch that client is connected to. MAC resolution is used by the Enhanced 9-1-1 service.  <br/> |
| _MaxCSRKeySize_ <br/> |Optional  <br/> |System.UInt64  <br/> |Sets the maximum size of the certificate signing request (CSR) key. (A CSR is a message sent from an applicant to a CA in order to apply for a digital certificate.) The maximum size can be set to any integer value between 1024 and 16384 bytes. The default value is 16384.  <br/> |
| _MaxGroupSizeToExpand_ <br/> |Optional  <br/> |System.UInt32  <br/> |Represents the maximum number of people that will be displayed when a group is expanded. For example, if MaxGroupSizeToExpand is set to 75, only the first 75 members of the group will be displayed any time the group is expanded.  <br/> MaxGroupSizeToExpand can be set to any integer value between 1 and 1000, inclusive. The default value is 100.  <br/> |
| _MaxValidityPeriodHours_ <br/> |Optional  <br/> |System.UInt64  <br/> |When using certificate authentication, clients can request the period of time (in hours) that the certificate remains valid. MaxValidityPeriodHours represents the maximum amount of time a client can request.  <br/> MaxValidityPeriodHours can be any integer value between 8 hours and 8760 hours (365 days). The default value is 8760.  <br/> |
| _MeetingUxEnableTelemetry_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _MeetingUxUseCdn_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _MinCSRKeySize_ <br/> |Optional  <br/> |System.UInt64  <br/> |Sets the minimum size of the CSR key. The minimum size can be set to any integer value between 1024 and 16384 bytes. The default value is 16384.  <br/> |
| _MinValidityPeriodHours_ <br/> |Optional  <br/> |System.UInt64  <br/> |When using certificate authentication, clients can request the period of time (in hours) that the certificate remains valid. MinValidityPeriodHours represents the minimum amount of time a client can request.  <br/> MinValidityPeriodHours can be any integer value between 8 hours and 4320 hours (180 days). The default value is 8.  <br/> |
| _MobilePreferredAuthType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Web.MobilePreferredAuthType  <br/> | Specifies the preferred authentication type to be used by mobile applications. If an unsupported method is specified, the web ticket service will not start and an event will be logged by the Skype for Business Server. Accepted values for the _MobilePreferredAuthType_ parameter are: <br/>  None <br/>  OAuth <br/>  WebTicketServiceAnon <br/>  WebTicketServiceWinNegotiate <br/>  WebTicketServiceWinNtlm <br/>  WebTicketServiceCert <br/>  WebTicketServicePin <br/>  WsFedPassive <br/>  WsFedBearer <br/>  WebTicketServiceAuth <br/> |
| _OverrideAuthTypeForExternalClients_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _OverrideAuthTypeForInternalClients_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _SecondaryLocationSourceUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for a Web service that can process a location request. This service is typically used only when location requests cannot be resolved locally.  <br/> |
| _ShowAlternateJoinOptionsExpanded_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> When set to True then alternate options for joining an online conference will automatically be expanded and shown to users. When set to False (the default value) these options will be available, but the user will have to display the list of options for themselves.  <br/> |
| _ShowDownloadCommunicatorAttendeeLink_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> If set to True (the default value), users joining a meeting by using a client application other than Skype for Business will see a link that points them toward a download for Skype for Business Web App.  <br/> |
| _ShowJoinUsingLegacyClientLink_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> If set to True, users joining a meeting by using a client application other than Skype for Business will be given the opportunity to join the meeting by using their current client application. The default value is False.  <br/> |
| _TrustedCACerts_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of certificates representing certificate chains trusted by the Web server. New certificates added to the collection must be created using the **New-CsWebTrustedCACertificate** cmdlet. <br/> This collection is not used if the InferCertChainFromSSL property is set to True.  <br/> |
| _UseCertificateAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), clients can be authenticated using certificates. Set this value to False ($False) to disable certificate authentication.  <br/> |
| _UseDomainAuthInLWA_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, domain authentication can be employed as a way to authenticate Skype for Business Web App users.  <br/> |
| _UsePinAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), clients can be authenticated using personal identification numbers (PINs). Set this value to False ($False) to disable PIN authentication.  <br/> |
| _UseWebClientLegacyUI_ <br/> |Optional  <br/> |System.Boolean  <br/> |If true ($True), then the legacy web interface is presented to the client. If false ($False), the standard web interface is used. The default is false.  <br/> |
| _UseWindowsAuth_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Web.UseWindowsAuth  <br/> |Determines how (and if) users will be authenticated using Windows authentication; that is, using the same credentials they used when they logged on to Windows. Valid values are:  <br/> Negotiate - The client and server will work together to determine the proper authentication protocol (either Kerberos or NTLM).  <br/> NTLM - Windows authentication will be allowed, but only using the NTLM protocol.  <br/> None - Windows authentication will not be allowed.  <br/> |
| _UseWsFedPassiveAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, allows for passive authentication: authentication of users by using URL redirection or smart linking. The default value is False ($False).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _WsFedPassiveMetadataUri_ <br/> |Optional  <br/> |System.String  <br/> |URI used by the WS-federation Web requestor protocol.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _UseLocalWebClient_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None. The **New-CsWebServiceConfiguration** cmdlet does not accept pipelined input.
  
## Return Types

The **New-CsWebServiceConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings object.
  
## See also

#### 

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)
  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)
  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

