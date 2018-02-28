---
title: "Set-CsWebServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 4/4/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 5aa0316d-afd8-4cc2-b606-0e720e6ab021
description: "Modifies an existing collection of Web Services configuration settings. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsWebServiceConfiguration
[]
Modifies an existing collection of Web Services configuration settings. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsWebServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

Example 1 enables group expansion for the Web Services configuration settings applied to the Redmond site (-Identity site:Redmond). This is done by including the EnableGroupExpansion property and setting the parameter value to True.
  
```
Set-CsWebServiceConfiguration -Identity site:Redmond -EnableGroupExpansion $True
```

### EXAMPLE 2

In Example 2, the maximum validity period for all the Web Services configuration settings applied at the site scope is changed to 16 hours. To carry out this task, the **Get-CsWebServiceConfiguration** cmdlet is called along with the Filter parameter; the filter value "site:*" limits the returned data to settings where the Identity begins with the characters "site:". This collection is then piped to the **Set-CsWebServiceConfiguration** cmdlet, which takes each item in the collection and changes the MaxValidityPeriodHours property to 16.
  
```
Get-CsWebServiceConfiguration -Filter "site:*" | Set-CsWebServiceConfiguration -MaxValidityPeriodHours 16
```

### EXAMPLE 3

In Example 3, the group expansion size is set to 400 for each collection of Web Services configuration settings that allow group expansion. To do this, the **Get-CsWebServiceConfiguration** cmdlet is called without any parameters; this returns a collection of all the Web Services configuration settings used in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnableGroupExpansion property is equal to True. In turn, this filtered collection is piped to the **Set-CsWebServiceConfiguration** cmdlet, which takes each item in the collection and sets the value of the MaxGroupSizeToExpand property to 400.
  
```
Get-CsWebServiceConfiguration | Where-Object {$_.EnableGroupExpansion -eq $True} | Set-CsWebServiceConfiguration -MaxGroupSizeToExpand 400
```

### EXAMPLE 4

The command shown in Example 4 shows how the global Web Services settings can be configured so that any person joining a meeting using a client application other than Skype for Business Server 2015 will first be shown a link to a site where he or she can download Skype for Business Web App. This is done by including the ShowDownloadCommunicatorAttendeeLink parameter and setting the parameter value to $True.
  
```
Set-CsWebServiceConfiguration -Identity global -ShowDownloadCommunicatorAttendeeLink $True 
```

### EXAMPLE 5

The commands shown in Example 5 add the domain http://fabrikam.com to an existing collection of Web service configuration settings. To carry out this task, the first command in the example uses the **New-CsWebOrigin** cmdlet to create a domain object for fabrikam.com. The resulting domain object is stored in a variable named $x.
  
The second command in the example uses the **Set-CsWebServiceConfiguration** cmdlet to add http://fabrikam.com to the Web service configuration settings applied to the Redmond site. The syntax @{Add=$x} adds the domain to any domains already in the collection of domains authorized for cross-domain scripting. To replace the existing collection with just http://fabrikam.com use the syntax @{Replace=$x}.
  
```
$x = New-CsWebOrigin -Url "http://fabrikam.com"
Set-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList @{Add=$x}
```

### EXAMPLE 6

In Example 6, the first domain listed in the collection of domains authorized for cross-domain scripting is removed from the web service configuration settings for the Redmond site. To carry out this task, the first command in the example uses the **Get-CsWebServiceConfiguration** cmdlet to return the current settings for the Redmond site. Those values are stored in a variable named $x.
  
In the second command, the RemoveAt method is used to remove the first domain from the CrossDomainAuthorizationList property. Domains are stored in this property as arrays, with the first domain having an index number of 0, the second domain having an index number of 1, and so on. To remove the second domain (index number 1) from the CrossDomainAuthorizationList property you would use this syntax:
  
$x.CrossDomainAuthorizationList.RemoveAt(1)
  
Note that command 2 removes the domain from the copy of the Redmond site stored in the variable $x, and not from the site itself. To actually remove the domain from the Redmond site, the third command in the example uses the **Set-CsWebServiceConfiguration** cmdlet and the Instance parameter to overwrite settings for the Redmond site with the settings stored in $x.
  
```
$x = Get-CsWebServiceConfiguration -Identity "site:Redmond"
$x.CrossDomainAuthorizationList.RemoveAt(0)
Set-CsWebServiceConfguration -Instance $x
```

### EXAMPLE 7

The command shown in Example 7 modifies the web service configuration settings for the Redmond site by removing all the domains that are authorized for cross-domain scripting. This is done by setting the CrossDomainAuthorizationList property to a null value ($Null).
  
```
Set-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $Null
```

## Detailed Description

Many Skype for Business Server 2015 components are web-based: these components either use Web Services or webpages to carry out their tasks. For example, users employ a web service when searching for new contacts in the Address Book or when using group expansion to view the individual members of a distribution group. Likewise, components ranging from dial-in conferencing to Skype for Business Server Control Panel use web pages as the interface between Skype for Business Server 2015 and users.
  
The **CsWebServiceConfiguration** cmdlets enable administrators to manage Web Services configuration settings throughout the organization. This includes managing group expansion, certificate settings, and allowed authentication methods. Because you can configure different settings at the global, site, and service scope (albeit for the only the Web Services service), you can customize Web Services capabilities for different users and different locations. The **CsWebServiceConfiguration** cmdlets enable administrators to manage Web Services configuration settings throughout the organization. This includes managing group expansion; certificate settings; and allowed authentication methods. Because you can configure different settings at the global, site, and service scope (Web Services service only) you can customize Web Services capabilities for different users and different locations.
  
Custom settings (for example, custom validity periods for certificates) can be specified at the time you create a new Web Services configuration setting collection. Alternatively, you can modify the property values for an existing collection by using the **Set-CsWebServiceConfiguration** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowAnonymousAccessToLWAConference_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, anonymous users will be allowed to attend Skype for Business Web App conferences.  <br/> |
| _AllowExternalAuthentication_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), OAuth authentication can be used to authenticate external users.  <br/> |
| _AutoLaunchLyncWebAccess_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> When set to True, Skype for Business Web App will automatically be used as the default web popup for joining an online conference, provided that the prerequisites for using Skype for Business Web App (for example, Silverlight have been installed, and Internet Explorer is not blocking pop-up windows) have been met.  <br/> The default value is True.  <br/> |
| _CASigningKeyLength_ <br/> |Optional  <br/> |System.UInt64  <br/> |Sets the size of the CA signing key, the private key used by a certification authority (CA) to sign digital certificates. The signing key length can be set to any integer value between 2048 and 16384 bytes; the default value is 2048.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _CorsPreflightResponseMaxAgeInSeconds_ <br/> |Optional  <br/> |System.Int64  <br/> |PARAMVALUE: Int64  <br/> |
| _CrossDomainAuthorizationList_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of domains allowed to host web applications that send cross-domain scripting requests to the Skype for Business Server 2015 deployment.  <br/> Domains to be added to the list must be created using the New-CsWebOrigin cmdlet and then added to the new collection of Web service configuration settings. Note, too that domain names must be prefaced using the http: or the https: prefix. See Examples 5, 6, and 7 of this help topic for more information.  <br/> This parameter was introduced in the February, 2013 release of Lync Server 2013.  <br/> |
| _DefaultValidityPeriodHours_ <br/> |Optional  <br/> |System.UInt64  <br/> |When using certificate authentication, clients can request the period of time (in hours) that the certificate remains valid. DefaultValidityPeriodHours represents the amount of time a certificate will remain valid if the client does not request a custom validity period.  <br/> DefaultValidityPeriodHours can be any integer value between 8 hours and 8760 hours (365 days). The default value is 4320 (180 days).  <br/> |
| _EnableCertChainDownload_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, servers presented with an authentication certificate will download the certificate chain for that certificate. The certificate chain traces an individual certificate back to the issuing CA. Certificates will not be accepted for authentication unless the certificate's CA is trusted.  <br/> |
| _EnableCORS_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableGroupExpansion_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, group expansion will be enabled in Skype for Business. With group expansion, users can configure a distribution group as a contact, then "expand" that group. When a group has been expanded, users can see the individual members of a group and their current presence information.  <br/> |
| _EnableMediaBasicAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True), enables basic authentication for media.  <br/> |
| _EnableStatisticsInResponse_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True ($True) the X-MS-WebInfraStats header is included in all HTTP responses. The default value is False ($False).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts or non-fatal error messages that might occur when you run the cmdlet.  <br/> |
| _HstsMaxAgeInSeconds_ <br/> |Optional  <br/> |System.Int64  <br/> |Specifies the value of max-age in Strict-Transport-Security header in a HTTPS response. Default value is 315360000. A negative value means Strict-Transport-Security header will not appear in HTTPS responses.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the Web Services configuration settings to be modified. To modify settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To modify settings configured at the service scope, use syntax similar to this:  <br/>  `-Identity "service:WebServer:atl-cs-001.litwareinc.com"` <br/> To modify settings configured at the global scope, you can use this syntax:  <br/>  `-identity global` <br/> If the Identity parameter is not used then the **Set-CsWebServiceConfiguration** cmdlet will automatically modify the global collection. <br/> |
| _InferCertChainFromSSL_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, servers will use the certificate information included in the Secure Sockets Layer (SSL) protocol to determine the issuing CA. Certificates will not be accepted for authentication unless the certificate's CA is trusted.  <br/> |
| _Instance_ <br/> |Optional  <br/> |WebServiceSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _JoinLauncherCdnConfigUri_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _JoinLauncherCdnTimeout_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |PARAMVALUE: TimeSpan  <br/> |
| _LWACdnConfigUri_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _MACResolverUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for a Web service capable of performing Media Access Control (MAC) resolution. MAC resolution involves taking the MAC address of a connected client and returning the chassis and port IDs of the network switch that client is connected to. MAC resolution is used by the Enhanced 9-1-1 service.  <br/> |
| _MaxCSRKeySize_ <br/> |Optional  <br/> |System.UInt64  <br/> |Sets the maximum size of the Certificate Signing Request (CSR) key. (A CSR is a message sent from an applicant to a CA in order to apply for a digital certificate.) The maximum size for a CSR key can be set to any integer value between 1024 and 16384 bytes. The default value is 16384.  <br/> |
| _MaxGroupSizeToExpand_ <br/> |Optional  <br/> |System.UInt32  <br/> |Represents the maximum number of people that will be displayed when a group is expanded. For example, if MaxGroupSizeToExpand is set to 75 only the first 75 members of the group will be displayed any time the group is expanded.  <br/> MaxGroupSizeToExpand can be set to any integer value between 1 and 1000, inclusive. The default value is 100.  <br/> |
| _MaxValidityPeriodHours_ <br/> |Optional  <br/> |System.UInt64  <br/> |When using certificate authentication, clients can request the period of time (in hours) that the certificate remains valid. MaxValidityPeriodHours represents the maximum amount of time a client can request.  <br/> MaxValidityPeriodHours can be any integer value between 8 hours and 8760 hours (365 days). The default value is 8760.  <br/> |
| _MeetingUxEnableTelemetry_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _MeetingUxUseCdn_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _MinCSRKeySize_ <br/> |Optional  <br/> |System.UInt64  <br/> |Sets the minimum size of the Certificate Signing Request (CSR) key. The minimum size can be set to any integer value between 1024 and 16384 bytes. The default value is 16384.  <br/> |
| _MinValidityPeriodHours_ <br/> |Optional  <br/> |System.UInt64  <br/> |When using certificate authentication, clients can request the period of time (in hours) that the certificate remains valid. MinValidityPeriodHours represents the minimum amount of time a client can request.  <br/> MinValidityPeriodHours can be any integer value between 8 hours and 4320 hours (180 days). The default value is 8.  <br/> |
| _MobilePreferredAuthType_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Web.MobilePreferredAuthType  <br/> |Specifies the default authentication method used for mobile client connectivity. Values can include: None | OAuth | WebTicketServiceAnon | WebTicketServiceWinNegotiate | WebTicketServiceWinNtlm | WebTicketServiceCert | WebTicketServicePin | WsFedPassive | WsFedBearer | WebTicketServiceAuth.  <br/> Note that if this value is set to a method that is not supported, the web ticket service may not start and an error will be generated in the Event log.  <br/> |
| _OverrideAuthTypeForExternalClients_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _OverrideAuthTypeForInternalClients_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _SecondaryLocationSourceUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for a web service that can process a location request. This service is only used when location requests cannot be resolved locally.  <br/> |
| _ShowAlternateJoinOptionsExpanded_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> When set to True then alternate options for joining an online conference will automatically be expanded and shown to users. When set to False (the default value) these options will be available, but the user will have to display the list of options for themselves.  <br/> |
| _ShowDownloadCommunicatorAttendeeLink_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> If set to True (the default value), users joining a meeting by using a client application other than Skype for Business will see a link that points them to a download for Skype for Business Web App.  <br/> |
| _ShowJoinUsingLegacyClientLink_ <br/> |Optional  <br/> |System.Boolean  <br/> |This parameter has been deprecated for use with the on-premises version of Skype for Business Server 2015.  <br/> If set to True, users joining a meeting by using a client application other than Skype for Business will be given the opportunity to join the meeting by using their current client application. The default value is False.  <br/> |
| _TrustedCACerts_ <br/> |Optional  <br/> |System.Management.Automation.PSListModifier  <br/> |Collection of certificates representing certificate chains trusted by the Web Server. New certificates added to the collection must be created by using the **New-CsWebTrustedCACertificate** cmdlet. <br/> This collection is not used if the InferCertChainFromSSL property is set to True.  <br/> |
| _UseCertificateAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), clients can be authenticated using certificates. Set this value to False to disable certificate authentication.  <br/> |
| _UseDomainAuthInLWA_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, domain authentication can be employed as a way to authenticate Skype for Business Web App users.  <br/> |
| _UsePinAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), clients can be authenticated using personal identification numbers (PINs). Set this value to False to disable PIN authentication.  <br/> |
| _UseWebClientLegacyUI_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _UseWindowsAuth_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Web.UseWindowsAuth  <br/> |Determines how (and if) users will be authenticated using Windows authentication; that is, using the same credentials they used when they logged on to Windows. Valid values are:  <br/> Negotiate - The client and server will work together to determine the proper authentication protocol (either Kerberos or NTLM).  <br/> NTLM - Windows authentication will be allowed, but only using the NTLM protocol.  <br/> None - Windows authentication will not be allowed.  <br/> |
| _UseWsFedPassiveAuth_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True, allows for passive authentication: authentication of users by using URL redirection or smart linking. The default value is False ($False).  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _WsFedPassiveMetadataUri_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _UseLocalWebClient_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings object. The **Set-CsWebServiceConfiguration** cmdlet accepts pipelined input of the Web Services settings object.
  
## Return Types

The **Set-CsWebServiceConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Web.WebServiceSettings object.
  
## See also

#### 

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)
  
[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)
  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)

