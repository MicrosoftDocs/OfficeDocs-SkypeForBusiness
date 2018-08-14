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

> [!NOTE]
> If you're about to read this article, you should already know about supported Modern Authentication topologies, ADAL, and about Modern Authentication config, but, in case you don't, here is the article you need start out: 
 + [https://docs.microsoft.com/en-us/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported](https://docs.microsoft.com/en-us/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
 + [https://docs.microsoft.com/en-us/skypeforbusiness/manage/authentication/use-adal](https://docs.microsoft.com/en-us/skypeforbusiness/manage/authentication/use-adal)
  
Modern Authentication doesn't just enable more secure methods of access, like Two-Factor Auth, or Client Certificate Auth, it carries out authorization of your user without needing a username or password. It's pretty handy.

This article will help you plug holes that have been exploited for Denial Of Service (DOS) attacks on Skype for Business Servers, by turning off older methods used for authentication, externally, inernally, or both, to your network. For example, one good method to help stop DOS attacks would be to turn off NTLM externally and rely on certificate-based authentication, disabling any password auth. 

All right, let's get started.

## What would you be changing? 

These cmdlets work for both SIP and Web Services points of access. Though these two channels use different access methods, running the gammut from NTLM and Kerberos to Anonymous access, all standard methods used by Skype for Business have been taken into consideration.

## How to get the Get- and Set-CsAuthConfig cmdlets

These cmdlets will only be installed post July 2018 cumulative update (6.0.9319.534) for Microsoft Skype for Business Server 2015, but then you have a variety of topologies that can be rolled out for your Skype for Business server.

## Topologies

It's important to keep in mind that these are the Supported Topologies involved in this scenario! If you need to go to Support for help with blocking a method, for example, you will need to have a configuration among the types below. 

> [!IMPORTANT]
> In this table and descriptions below, *Modern Authentication* is abbreviated as __MA__ and *Windows Integrated Authentication* is abbreviated at __Win__. You'll need to know this to read the table properly!


|       |Externally  |Internally  |Parameter  |
|---------|:---------|---------:|---------|
|Type 1   |  MA + Win       | MA + Win         |  AllowAllExternallyAndInternally       |
|Type 2   |  MA       | MA + Win         | BlockWindowsAuthExternally        |
|Type 3   |  MA       | MA        | BlockWindowsAuthExternallyAndInternally        |
|Type 4   |  MA       | Win        | BlockWindowsAuthExternallyAndModernAuthInternally    |
|Type 5   |  MA + Win       | Win        | BlockModernAuthInternally         |

__Type 1 Description:__ This is the default scenario when MA is turned __on__ for Skype for Business Server. In other words, this is the *starting point* when MA is configured.

__Type 2 Description:__ This topology blocks password attacks *externally*, but allows for older clients (that don't support ADAL) to work *internally*. If your clients  do support ADAL they will use MA internally.

__Type 3 Description:__ This topology uses MA for all users. All your ADAL-capable clients will work in this topology, and passwords will not be leveraged.

__Type 4 Description:__ This topology blocks password attacks *externally* and allows all clients to use legacy authentication methods *internally*.

__Type 5 Description:__ *Externally*, your modern ADAL clients will use MA and any clients that don't support ADAL will use legacy authentication methods. But, *internally* all clients will use legacy authentication.

It's pretty easy to lose track of the goal of protecting your passwords in the options available. Keep in mind the ideal situation is to use MA externally, to avoid DOS attacks. If you also leverage it internally for your modern clients, you'll also future-proof your network, regarding Skype for Business Server DOS attacks.

## How these changes apply to your Roles



> [!IMPORTANT]
> If you're using Lync Web Access (LWA) and must use Forms-based Access (FBA) for external access, reconfigure LWA so that clients can access it with Anonymous Access to support these scenarios. Likewise, if you use Dial-in Pin, FBA will be blocked for external users only. If they need to change thir pin, they will need to login to their corporation to do so, internally.




 