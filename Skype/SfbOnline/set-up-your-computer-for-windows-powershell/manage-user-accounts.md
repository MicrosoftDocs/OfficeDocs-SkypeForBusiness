---
title: "Manage user accounts"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: a226b0d4-6359-42b8-808d-4b8ab3736d3b
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: Normal
f1keywords: None
ms.custom:
- PowerShell
description: "Use the Get-CsOnlineUser cmdlet in Windows PowerShell to get information about your organization's Skype for Business Online users."
---

# Manage user accounts

## Manage user accounts

This topic contains the following sections:

- [Return information about all your Skype for Business Online users](manage-user-accounts.md#BKMKReturnInfoAboutAllUsers)

- [Return information for a specific user in Skype for Business Online](manage-user-accounts.md#BKMKReturnInfoSpecificUser)

- [Return specific information for specific users in Skype for Business Online](manage-user-accounts.md#BKMKReturninfoSpecificUsers)

- [Return a filtered list of users in Skype for Business Online ](manage-user-accounts.md#BKMKReturnFilteredListofUsers)

> [!NOTE]
> The **Set-CsUser** cmdlet is also included in the set of cmdlets available to Skype for Business Online admins. However, **Set-CsUser** cannot currently be used to manage Skype for Business Online, except for setting the _AudioVideoDisabled_ parameter. If you attempt to run the cmdlet with any other parameter, it will fail with an error message similar to this: Unable to set "SipAddress". This parameter is restricted within Remote Tenant PowerShell.

### Return information about all your Skype for Business Online users
<a name="BKMKReturnInfoAboutAllUsers"> </a>

To return information about all your users who have been enabled for Skype for Business Online, call the [Get-CsOnlineUser](https://go.microsoft.com/fwlink/p/?linkid=849603) cmdlet without any additional parameters.

```
Get-CsOnlineUser
```

To return information for a single, randomly selected user (for example, to use this account for test purposes), call the **Get-CsOnlineUser** cmdlet and set the _ResultSize_ parameter to 1.

```
Get-CsOnlineUser -ResultSize 1
```

That causes the **Get-CsOnlineUser** cmdlet to return information for just one user, regardless of how many users you have in your organization. To return information for five users, set the value of the _ResultSize_ parameter to 5.

```
Get-CsOnlineUser -ResultSize 5
```

### Return information for a specific user in Skype for Business Online
<a name="BKMKReturnInfoSpecificUser"> </a>

There are multiple ways of referencing a specific user account when calling the [Get-CsOnlineUser](https://go.microsoft.com/fwlink/p/?linkid=849603) cmdlet. You can use the user's Active Directory Domain Services (AD DS) display name.

```
Get-CsOnlineUser -Identity "Ken Myer"
```

You can use the user's SIP address.

```
Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"
```

You can use the user's user principal name (UPN).

```
Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"
```

### Return specific information for specific users in Skype for Business Online
<a name="BKMKReturninfoSpecificUsers"> </a>

By default, the [Get-CsOnlineUser](https://technet.microsoft.com/library/2bfafd70-a7d9-4308-a353-5ecf44249b53.aspx) cmdlet returns a huge amount of information for each Skype for Business Online user account. If you are interested in only a subset of that information, pipe the returned data to the **Select-Object** cmdlet. For example, this command returns all the data for the user Ken Myer, and then uses the **Select-Object** cmdlet to limit the information displayed onscreen to Ken's AD DS display name and dial plan.

```
Get-CsOnlineUser -Identity "Ken Myer" | Select-Object DisplayName, DialPlan
```

The following command returns the display name and dial plan for all your users.

```
Get-CsOnlineUser | Select-Object DisplayName, DialPlan
```

To find the properties of a Skype for Business Online user account, use the following command.

```
Get-CsOnlineUser | Get-Member
```

### Return a filtered list of users in Skype for Business Online
<a name="BKMKReturnFilteredListofUsers"> </a>

By using the [Get-CsOnlineUser](https://go.microsoft.com/fwlink/p/?linkid=849603) cmdlet and the _LdapFilter_ or _Filter_ parameters, you can easily return information about a targeted set of users. For example, this command returns all the users who work in the Finance department.

```
Get-CsOnlineUser -LdapFilter "department=Finance"
```

## Related topics
[Set up your computer for skype for business online management using Windows PowerShell](set-up-your-computer-for-windows-powershell.md)


