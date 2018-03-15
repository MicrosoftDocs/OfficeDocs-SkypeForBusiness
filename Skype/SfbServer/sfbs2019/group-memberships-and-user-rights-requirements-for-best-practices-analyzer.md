---
title: "Group memberships and user rights requirements for Best Practices Analyzer in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f812e343-8f75-454e-b7a8-1b404e32071a
description: "To successfully run Best Practices Analyzer, the user account that you use to log on must be a member of the Administrators group on the local computer. Additionally, to scan your environment, the user account must be a member of the following groups:"
---

# Group memberships and user rights requirements for Best Practices Analyzer in Lync Server 2013
[]
To successfully run Best Practices Analyzer, the user account that you use to log on must be a member of the Administrators group on the local computer. Additionally, to scan your environment, the user account must be a member of the following groups: 
  
- **Domain Admins** To enumerate Active Directory Domain Services information and to call the Windows Management Instrumentation (WMI) providers on domain controllers and global catalog servers. 
    
- **Administrators** Required on each Lync Server 2013 internal computer and each Edge Server to call the Windows Management Instrumentation (WMI) providers and to access the registry. 
    
- **RTCUniversalReadOnlyAdmins** Full or delegated read only Lync Server 2013 administrative rights. 
    
- **Exchange View Only Administrator** Full or delegated Exchange View Only Administrator on the Microsoft Exchange organization. 
    
If your user account does not have sufficient user rights, you have two options: 
  
- At a command prompt, use the **runas** command to run the tool under an account that does have sufficient user rights. The syntax is as follows: 
    
  ```
  runas /netonly /user:<domain>\<userName> rtcbpa.exe
  ```

- On the **Connect to Active Directory** page, set the credentials for the accounts that you plan to use to run Best Practices Analyzer. Click **Show advanced login options**. You can enter three accounts: one for connecting to Active Directory Domain Services, one for connecting to Lync Server 2013 Edge Servers, and one for connecting to the Exchange Servers. If you do not specify any of these accounts, the user account that you used to log on and run Best Practices Analyzer is used.
    

