---
title: "Planning for two-factor authentication in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 16f08710-8961-4659-acbf-ebb95a198fb4
description: "In this articleClient SupportTopology RequirementsLync Service DiscoveryExchange AuthenticationLync ContactsSkill SearchLync CredentialsAD FS 2.0 Token ReplayExternal User Access"
---

# Planning for two-factor authentication in Lync Server 2013
[]
 **In this article**
  
[Client Support](#sectionSection0)
  
[Topology Requirements](#sectionSection1)
  
[Lync Service Discovery](#sectionSection2)
  
[Exchange Authentication](#sectionSection3)
  
[Lync Contacts](#sectionSection4)
  
[Skill Search](#sectionSection5)
  
[Lync Credentials](#sectionSection6)
  
[AD FS 2.0 Token Replay](#sectionSection7)
  
[External User Access](#sectionSection8)
  
The following is a list of deployment considerations when configuring a Microsoft Lync Server 2013 environment to support two-factor authentication.
  
## Client Support
<a name="sectionSection0"> </a>

The Lync 2013 Cumulative Updates for Lync Server 2013: July 2013 desktop client and all mobile clients currently support two-factor authentication.
  
## Topology Requirements
<a name="sectionSection1"> </a>

Customers are strongly encouraged to deploy two-factor authentication using dedicated Lync Server 2013 with Cumulative Updates for Lync Server 2013: July 2013 Edge, Director, and User Pools. To enable passive authentication for Lync users, other authentication methods must be disabled for other roles and services, including the following:
  
|**Configuration Type**|**Service Type**|**Server Role**|**Authentication Type to Disable**|
|:-----|:-----|:-----|:-----|
|Web Service  <br/> |WebServer  <br/> |Director  <br/> |Kerberos, NTLM, and Certificate  <br/> |
|Web Service  <br/> |WebServer  <br/> |Front End  <br/> |Kerberos, NTLM, and Certificate  <br/> |
|Proxy  <br/> |EdgeServer  <br/> |Edge  <br/> |Kerberos and NTLM  <br/> |
|Proxy  <br/> |Registrar  <br/> |Front End  <br/> |Kerberos and NTLM  <br/> |
   
Unless these authentication types are disabled at the service level, all other versions of the Lync client will be unable to sign in successfully once two-factor authentication is enabled within in your deployment.
  
## Lync Service Discovery
<a name="sectionSection2"> </a>

DNS records used by internal and/or external clients to discover Lync services should be configured to resolve to a Lync server that is not enabled for two-factor authentication. With this configuration, users from Lync Pools that are not enabled for two-factor authentication will not be required to enter a PIN to authenticate, while users from Lync Pools that are enabled for two-factor authentication will be required to enter their PIN to authenticate.
  
## Exchange Authentication
<a name="sectionSection3"> </a>

Customers who have deployed two-factor authentication for Microsoft Exchange may find that certain features in the Lync client are unavailable. This is currently by design, as the Lync client does not support two-factor authentication for features that are dependent on Exchange integration.
  
## Lync Contacts
<a name="sectionSection4"> </a>

Lync users who are configured to leverage the Unified Contact Store feature will find that their contacts are no longer available after signing in with two-factor authentication.
  
You should use the **Invoke-CsUcsRollback** cmdlet to remove existing user contacts from the Unified Contact Store and store them in Lync Server 2013 before enabling two-factor authentication. 
  
## Skill Search
<a name="sectionSection5"> </a>

Customers who have configured the Skill Search feature in their Lync environment will find that this feature does not work when Lync is enabled for two-factor authentication. This is by design, as Microsoft SharePoint does not currently support two-factor authentication.
  
## Lync Credentials
<a name="sectionSection6"> </a>

There are a number of deployment considerations involving saved Lync credentials which may impact users who are configured to use two-factor authentication.
  
### Deleting Saved Credentials

Desktop client users should use the **Delete my sign-in info** option in the Lync client and delete their SIP profile folder from %localappdata%\Microsoft\Office\15.0\Lync before attempting to sign for the first time using two-factor authentication. 
  
### DisableNTCredentials

With the Kerberos or NTLM authentication method, the user's Windows credentials are used automatically for authentication. In a typical Lync Server 2013 deployment where Kerberos and/or NTLM is enabled for authentication, users should not have to enter their credentials every time that they sign in.
  
If users are unintentionally prompted for credentials before they are prompted to enter their PIN, the **DisableNTCredentials** registry key may be unintentionally configured on client computers, possibly through Group Policy. 
  
To prevent the additional prompt for credentials, create the following registry entry on the local workstation or use the Lync administrative template to apply to all users for a given pool using Group Policy:
  
HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Office\15.0\Lync
  
REG_DWORD: DisableNTCredentials
  
Value: 0x0
  
### SavePassword

When a user signs in to Lync for the first time, the user is prompted to save his or her password. If selected, this option allows the user's client certificate to be stored in the personal certificate store and the user's Windows credentials to be stored in the Credential Manager of the local computer.
  
The **SavePassword** registry setting should be disabled when Lync is configured to support two-factor authentication. To prevent users from saving their passwords, change the following registry entry on the local workstation or use the Lync administrative template to apply to all users for a given pool using Group Policy: 
  
HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync
  
REG_DWORD: SavePassword
  
Value: 0x0
  
## AD FS 2.0 Token Replay
<a name="sectionSection7"> </a>

AD FS 2.0 provides a feature referred to as token replay detection, by which multiple token requests using the same token can be detected and then discarded. When this feature is enabled, token replay detection protects the integrity of authentication requests in both the WS-Federation passive profile and the SAML WebSSO profile by making sure that the same token is never used more than once.
  
This feature should be enabled in situations where security is a very high concern such as when using kiosks. For more information about token replay detection, see Best Practices for Secure Planning and Deployment of AD FS 2.0 at [https://go.microsoft.com/fwlink/p/?LinkId=309215](https://go.microsoft.com/fwlink/p/?LinkId=309215).
  
## External User Access
<a name="sectionSection8"> </a>

Configuring an AD FS Proxy or Reverse Proxy to support Lync two-factor authentication from external networks is not covered in these topics.
  

