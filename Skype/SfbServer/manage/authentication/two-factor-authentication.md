---
title: "Manage two-factor authentication in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 16f08710-8961-4659-acbf-ebb95a198fb4
description: "Summary: Manage two-factor authentication in Skype for Business Server."
---

# Manage two-factor authentication in Skype for Business Server
 
**Summary:** Manage two-factor authentication in Skype for Business Server.
  
Two-factor authentication provides improved security by requiring users to provide two forms of authentication or identification, namely a user name/password combination and a token or certificate. This is also known as "something you have, something you know." 
  
A typical example of two-factor authentication with a certificate is the use of smart cards. A smart card contains a certificate associated with the user account, and can be validated against user and certificate information stored on a server. By comparing the user information (user name and password) to the certificate provided, the server validates the credentials and authenticates the user.
  
Consider the following subjects when configuring a Skype for Business Server environment to support two-factor authentication.
  
## Client Support

The Cumulative Updates for Lync Server 2013: July 2013 desktop client and the Skype for Business client are the only clients that currently support two-factor authentication.
  
## Topology Requirements

Customers are strongly encouraged to deploy two-factor authentication using dedicated Skype for Business Server with Edge, Director, and User Pools. To enable passive authentication for users, other authentication methods must be disabled for other roles and services, including the following:
  
|**Configuration Type**|**Service Type**|**Server Role**|**Authentication Type to Disable**|
|:-----|:-----|:-----|:-----|
|Web Service  <br/> |WebServer  <br/> |Director  <br/> |Kerberos, NTLM, and Certificate  <br/> |
|Web Service  <br/> |WebServer  <br/> |Front End  <br/> |Kerberos, NTLM, and Certificate  <br/> |
|Proxy  <br/> |EdgeServer  <br/> |Edge  <br/> |Kerberos and NTLM  <br/> |
|Proxy  <br/> |Registrar  <br/> |Front End  <br/> |Kerberos and NTLM  <br/> |
   
Unless these authentication types are disabled at the service level, all other versions of the client will be unable to sign in successfully once two-factor authentication is enabled within in your deployment.
  
## Skype for Business Service Discovery

DNS records used by internal and/or external clients to discover Skype for Business services should be configured to resolve to a Skype for Business server that is not enabled for two-factor authentication. With this configuration, users from Skype for Business Pools that are not enabled for two-factor authentication will not be required to enter a PIN to authenticate, while users from Skype for Business Pools that are enabled for two-factor authentication will be required to enter their PIN to authenticate.
  
## Exchange Authentication

Customers who have deployed two-factor authentication for Microsoft Exchange may find that certain features in the client are unavailable. This is currently by design, as the Skype for Business client does not support two-factor authentication for features that are dependent on Exchange integration.
  
## Contacts

Skype for Business users who are configured to leverage the Unified Contact Store feature will find that their contacts are no longer available after signing in with two-factor authentication.
  
You should use the **Invoke-CsUcsRollback** cmdlet to remove existing user contacts from the Unified Contact Store and store them in Skype for Business Server before enabling two-factor authentication.
  
## Skill Search

Customers who have configured the Skill Search feature in their Skype for Business environment will find that this feature does not work when Skype for Business is enabled for two-factor authentication. This is by design, as Microsoft SharePoint does not currently support two-factor authentication.
  
## Credentials

There are a number of deployment considerations involving saved Skype for Business credentials which may impact users who are configured to use two-factor authentication.
  
### Deleting Saved Credentials

Users should use the **Delete my sign-in info** option in the Skype for Business client and delete their SIP profile folder from %localappdata%\Microsoft\Office\15.0\Skype for Business before attempting to sign for the first time using two-factor authentication.
  
### DisableNTCredentials

With the Kerberos or NTLM authentication method, the user's Windows credentials are used automatically for authentication. In a typical Skype for Business Server deployment where Kerberos and/or NTLM is enabled for authentication, users should not have to enter their credentials every time that they sign in.
  
If users are unintentionally prompted for credentials before they are prompted to enter their PIN, the **DisableNTCredentials** registry key may be unintentionally configured on client computers, possibly through Group Policy.
  
To prevent the additional prompt for credentials, create the following registry entry on the local workstation or use the Skype for Business administrative template to apply to all users for a given pool using Group Policy:
  
    HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Office\15.0\Lync
  
    REG_DWORD: DisableNTCredentials
  
    Value: 0x0
  
### SavePassword

When a user signs in to Skype for Business for the first time, the user is prompted to save his or her password. If selected, this option allows the user's client certificate to be stored in the personal certificate store and the user's Windows credentials to be stored in the Credential Manager of the local computer.
  
The **SavePassword** registry setting should be disabled when Skype for Business is configured to support two-factor authentication. To prevent users from saving their passwords, change the following registry entry on the local workstation or use the Skype for Business administrative template to apply to all users for a given pool using Group Policy:
  
    HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync
  
    REG_DWORD: SavePassword
  
    Value: 0x0
  
## AD FS 2.0 Token Replay

AD FS 2.0 provides a feature referred to as token replay detection, by which multiple token requests using the same token can be detected and then discarded. When this feature is enabled, token replay detection protects the integrity of authentication requests in both the WS-Federation passive profile and the SAML WebSSO profile by making sure that the same token is never used more than once.
  
This feature should be enabled in situations where security is a very high concern such as when using kiosks. For more information about token replay detection, see [Best Practices for Secure Planning and Deployment of AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=309215).
  
## External User Access

Configuring an ADFS Proxy or Reverse Proxy to support Skype for Business two-factor authentication from external networks is not covered in these topics.
  
## See also

[Configure two-factor authentication in Skype for Business Server](configure-two-factor.md)
  
