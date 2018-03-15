---
title: "Cmdlets in Skype for Business Online that use a user identity"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: be87409f-6372-4c70-91ac-6ef13dfbe65a
description: "In Skype for Business Online, there are a number of different ways to reference an individual user Identity:"
---

# Cmdlets in Skype for Business Online that use a user identity
[]
In Skype for Business Online, there are a number of different ways to reference an individual user Identity:
  
- Use the user's Active Directory Domain Services display name. For example:
    
  ```
  -Identity "Ken Myer"
  ```

- Use the user's SIP address. For example:
    
  ```
  -Identity "sip:kenmyer@litwareinc.com"
  ```

- Use the user's UPN. For example:
    
  ```
  -Identity " kenmyer@litwareinc.com"
  ```

- Use the user's Active Directory Domain Services distinguished name. For example:
    
  ```
  -Identity "CN=48ebd1ba-95d4-460c-b751-811ebf0c4611,OU=fa8226f5-14fa-46da-8 236-039b25bc7a27,OU=Lync Online Tenants,DC=litwareinc,DC=com"
  ```

The following cmdlets accept a user Identity:
  
- [Disable-CsMeetingRoom](disable-csmeetingroom.md)
    
- [Enable-CsMeetingRoom](enable-csmeetingroom.md)
    
- [Get-CsExUmContact](get-csexumcontact.md)
    
- [Get-CsMeetingRoom](get-csmeetingroom.md)
    
- [Get-CsOnlineUser](get-csonlineuser.md)
    
- [Get-CsUserAcp](get-csuseracp.md)
    
- [New-CsExUmContact](new-csexumcontact.md)
    
- [Remove-CsExUmContact](remove-csexumcontact.md)
    
- [Remove-CsUserAcp](remove-csuseracp.md)
    
- [Set-CsExUmContact](set-csexumcontact.md)
    
- [Set-CsMeetingRoom](set-csmeetingroom.md)
    
- [Set-CsUserAcp](set-csuseracp.md)
    
Note that you do not need to specify a user Identity when calling one of the **Get-Cs** cmdlets. In this case, the cmdlets return all the instances of the specified item. For example, this command returns information about all the users who have been enabled for Skype for Business Online: 
  
```
Get-CsOnlineUser
```

The Identity parameter is required only if you want to return information for a specific user:
  
```
Get-CsOnlineUser -Identity "Ken Myer"
```

## See also

#### 

[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants.md)
  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)

