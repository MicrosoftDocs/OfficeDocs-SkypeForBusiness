---
title: "Turn off Modern Authentication and other authentication methods internally and externally to your network"
ms.author: tracyp
author: MSFTTracyP
manager: serdars
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: tracyp
ms.assetid: 

description: "This article outlines cmdlets that give admins more control of authentication methods used inside, and outside, of a business. Administrators can turn authentication methods on or off internally, or externally to their network."
---

# Turn off Modern Authentication and other authentication methods internally and externally to your network
 
NOTE If you're about to read this article, you should already know about supported Modern Authentication topologies, and about Modern Authentication config, but, in case you don't, here is the article you need start out:

 [https://docs.microsoft.com/en-us/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported](https://docs.microsoft.com/en-us/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
  
Modern Authentication doesn't just enable more secure methods of access, like Two-Factor Auth, or Client Certificate Auth, it carries out authorization of your user without needing a username or password. It's pretty handy.

This article will help you plug holes that have been exploited for Denial Of Service (DOS) attacks on Skype for Business Servers, by turning off older methods used for authentication, externally, inernally, or both, to your network. So, let's get started.

## What are we plugging? 

These cmdlets work for both SIP and Web Services points of access. Though these two channels use different access methods, running the gammut from NTLM and Kerberos to Anonymous access, all standard methods used by Skype for Business have been taken into consideration.

## SIP

DOS attacks on SIP services use NTLM authentication heavily. NTLM is a username and password 'handshake' between the server and client, and does require credentials to be passed.

This cmdlet will turn off NTLM for authorization inside the SIP service:

`Set-CsProxyConfiguration UseNTLMforClientProxyAuth= false`

Be aware that this cmdlet turns off internal and external connections that use NTLM. There is no method for turning off one without the other.

## Web Services

The story is not the same in Web Services. Here, when methods (like NTLM) are stopped, the administrator has the choice of preventing them  externally, or internally, or both. 

Here are the new parameters added to:

`Set-CsWebServiceConfiguration`

|Parameters  |Required?  |Type  |Description  |
|:---------|:---------:|:---------:|---------|
|OverrideAuthTypeForInternalClients  | Optional         | System.String        | This is a string made up of comma separated option strings where each option overrides a specific authentication for *internal* client. The default is an empty string ($null).        |
|OverrideAuthTypeForExternalClients    | Optional        | System.String        |  A string composed of comma separated option strings where each overrides a specific authentication for *external* clients. The default is empty string ($null).      

Here are the commands valid for the parameters above:


|Parameter  |Valid values |Description  |
|---------|:---------|---------|
|OverrideAuthTypeForInternalClients     |DisableWindowsAuth, DisableOAuth, DisableWsFedPassiveAuth, DisableFormsAuth          |         |DisableWindowsAuth overrides the current setting of *UseWindowsAuth* by disallowing Windows authentication for internal connection. 

DisableOAuth overrides the current setting of *AllowExternalAuthentication* by disallowing OAuth authentication for internal connection. 

DisableWsFedPassiveAuth overrides the current setting of *UseWsFedPassiveAuth* by disallowing LiveID authentication for internal connection. 

DisableFormsAuth overrides the current setting of *UseWindowsAuth* by disallowing Form based authentication for internal connection
|OverrideAuthTypeForExternalClients      |     DisableWindowsAuth, DisableOAuth, DisableWsFedPassiveAuth, DisableFormsAuth    |DisableWindowsAuth overrides the current setting of *UseWindowsAuth* by disallowing Windows authentication for external connection. 

DisableOAuth overrides the current setting of *AllowExternalAuthentication* by disallowing OAuth authentication for external connection. 

DisableWsFedPassiveAuth overrides the current setting of *UseWsFedPassiveAuth* by disallowing LiveID authentication for external connection. 

DisableFormsAuth overrides the current setting of *UseWindowsAuth* by disallowing Form based authentication for external connection.            |

NOTE  You must run `Enable-CsComputer` and an IISReset for these commands to begin doing their job quickly.

The cmdlet, `Set-CsWebServiceConfiguration`, can be used at different security scopes in Skype for Business: globally, at the site level, or on the service level. This means you can run this cmdlet for different scopes, using different parameters. I'd caution you against creating too much complexity in your deployment, unless it's truly called for. If it is, be sure to document the values used for each of the scopes, thoroughly. Avoid the headaches later.

 







 