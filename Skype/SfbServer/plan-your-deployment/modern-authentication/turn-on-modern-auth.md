---
title: "Planning to turn off Legacy authentication methods internally and externally to your network"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.custom: tracyp
ms.assetid: 

description: "This article outlines cmdlets that give admins more control of authentication methods used inside, and outside, of a business. Administrators can turn authentication methods on or off internally, or externally to their network."
---

# Planning to turn off Legacy authentication methods internally and externally to your network.

> [!NOTE]
> If you're about to read this article, you should already know about supported Modern Authentication topologies, ADAL, and about Modern Authentication config, but, in case you don't, here are the articles you need to start out: 
>  + [https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported](https://docs.microsoft.com/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
>  + [https://docs.microsoft.com/skypeforbusiness/manage/authentication/use-adal](https://docs.microsoft.com/skypeforbusiness/manage/authentication/use-adal)
  
Modern Authentication doesn't just enable more secure methods of authentication, like Two-Factor Auth, or Certificate-based Auth, it can carry out authorization of your user without needing a username or password too. It's pretty handy.

This article will help you plug holes that have been exploited for Denial Of Service (DOS) attacks on Skype for Business Servers, by turning off older methods used for authentication, externally, internally, or both, to your network. For example, one good method to help stop DOS attacks would be to turn off Windows Integrated Authentication (which includes NTLM and Kerberos). Turning off NTLM externally and relying on certificate-based authentication helps to protect passwords from exposure. This is because NTLM uses password credentials to authenticate users, but certificate-based authentication -- enabled by Modern Auth -- doesn't. That means one ideal option to reduce DOS attacks is to block NTLM externally, and use only certificate-based authentication there, instead.

All right, let's get started.

## What would you be changing? 

These cmdlets work for both SIP and Web Services points of access. Though these two channels use different access methods, running the gamut from NTLM and Kerberos to Anonymous access, all standard methods used by Skype for Business have been taken into consideration.

## How to get the Get- and Set-CsAuthConfig cmdlets

These cmdlets will only be installed post July 2018 cumulative update (6.0.9319.534) for Microsoft Skype for Business Server 2015, and then you have a variety of topologies that can be rolled out for your Skype for Business server.

## Topologies

It's important to keep in mind that these are the Supported Topologies involved in this scenario! If you need to go to Support for help with blocking a method, for example, you will need to have a configuration among the types below. 

> [!IMPORTANT]
> In the table and descriptions below, *Modern Authentication* is abbreviated as __MA__ and *Windows Integrated Authentication* is abbreviated as __Win__. As a reminder, Windows Integrated Authentication is made up of two methods: NTLM and Kerberos authentication. You'll need to know this to read the table properly!


|       |Externally  |Internally  |Parameter  |
|---------|:---------|:---------|---------|
|__Type 1__   |  MA + Win       | MA + Win         |  AllowAllExternallyAndInternally       |
|__Type 2__   |  MA       | MA + Win         | BlockWindowsAuthExternally        |
|__Type 3__   |  MA       | MA        | BlockWindowsAuthExternallyAndInternally        |
|__Type 4__   |  MA       | Win        | BlockWindowsAuthExternallyAndModernAuthInternally    |
|__Type 5__   |  MA + Win       | Win        | BlockModernAuthInternally         |

__Type 1 Description:__ This is the default scenario when MA is turned __on__ for Skype for Business Server. In other words, this is the *starting point* when MA is configured.

__Type 2 Description:__ This topology blocks NTLM *externally*, but allows NTLM or Kerberos (for clients that don't support ADAL) to work *internally*. If your clients  do support ADAL they will use MA internally.

__Type 3 Description:__ This topology requires MA for all users. All your ADAL-capable clients will work in this topology, and passwords will not be leveraged if, for example, you turn off the use of passwords with Certificate-based Auth.

__Type 4 Description:__ This topology blocks NTLM *externally* and MA internally. It allows *all clients* to use legacy authentication methods *internally* (even ADAL-capable clients).

__Type 5 Description:__ *Externally*, your modern ADAL clients will use MA and any clients that don't support ADAL will use legacy authentication methods. But, *internally* *all clients* will use legacy authentication (including all ADAL-capable clients).

It's pretty easy to lose track of the goal of protecting your passwords in the options available. Keep in mind the ideal situation is to use MA externally (for example, by configuring certificate-based auth), to avoid DOS attacks. If you leverage it internally for your modern clients, you'll also future-proof your network regarding Skype for Business Server DOS attacks.

## Why to use Set-CsAuthConfig at the Global level

The `Set-CsAuthConfig` cmdlet effects configuration on both the Registrar and the Web Services roles.

This cmdlet is meant to be run at the Global level of your Skype for Business server. It *can* be run at the Pool level but that is *not recommended* because it will add complexity to your installation. By running these commands at the Pool level, if your Pool doesn't have all of the roles included (for example, it doesn't have Web Services), the settings will only be set for the Registrar role. In that case, Web Services will carry on with settings from the Global level, which can be confusing behaviour (particularly when this is done unintentionally).

If a client uses the Registrar settings from one pool and the Web Services settings from another pool and the authentication settings are in an inconsistent state, yous clients may be unable to log on.

Also, if there's only one role present for a pool: 
* Set- will only set the settings that correspond to the role that exists. No special warning will be given because some settings were *not* set. 
* Get- will return the setting that corresponds to the role that exists, and the Global settings for the role that doesn't exist.
* If neither role is present for a pool, both Set- and Get- will return an error message.
* If both roles are present for a pool but policies aren't defined at the pool level, Get- will return an error message.

It may be wisest to do a Get- for these values, and to screenshot or record their starting state before making any changes. You might also consider keeping a log of changes in a OneNote.

> [!NOTE]
> 
> Note: After configuring the CsAuthConfig, you must run Enable-CsComputer on each computer in order for the settings to take effect.

> [!IMPORTANT]
> If you're using Lync Web Access (LWA) and must use Forms-based Access (FBA) for external access, reconfigure LWA so that clients can access it with Anonymous Access to support these scenarios. Likewise, if you use Dial-in Pin, FBA will be blocked for external users only. If they need to change their pin, they will need to login to their corporation to do so, internally. Skype meeting app (SMA) can only be used using guest access internally or externally

## Links 
- For more PowerShell information:
    -  [Get-CsAuthConfig](https://docs.microsoft.com/powershell/module/skype/get-csauthconfig?view=skype-ps)
    -  [Set-CsAuthConfig](https://docs.microsoft.com/en-us/powershell/module/skype/set-csauthconfig?view=skype-ps)

- For more direction on how to use the commands or on the CU needed to install them:
    - [Cmdlets briefing](https://support.microsoft.com/en-us/help/4346673/new-cmdlets-to-manage-skype-for-business-server-2015-authentication)
    - [Updates for Skype for Business Server 2015](https://support.microsoft.com/en-us/help/3061064/updates-for-skype-for-business-server-2015) (General)
    - The [July 2018 Skype for Business Server 2015, Core Components CU](https://support.microsoft.com/en-us/help/4340903/july-2018-cumulative-update-6-0-9319-534-for-skype-for-business-server) (6.0.9319.534)


 
