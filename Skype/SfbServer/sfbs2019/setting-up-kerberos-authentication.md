---
title: "Setting up Kerberos authentication in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dd8009ef-6265-4cc0-b2c7-e474cd1f4b09
description: "Lync Server 2013 supports NTLM and Kerberos authentication for Web Services. Office Communications Server 2007 and Office Communications Server 2007 R2 used the default RTCComponentService and RTCService as the user accounts to run the Web Services application pools, allowing for a service principal name (SPN) to be assigned to the user accounts and to act as the authentication principal. Lync Server uses NetworkService to run Web Services and NetworkService cannot have SPNs assigned to it."
---

# Setting up Kerberos authentication in Lync Server 2013
[]
Lync Server 2013 supports NTLM and Kerberos authentication for Web Services. Office Communications Server 2007 and Office Communications Server 2007 R2 used the default RTCComponentService and RTCService as the user accounts to run the Web Services application pools, allowing for a service principal name (SPN) to be assigned to the user accounts and to act as the authentication principal. Lync Server uses NetworkService to run Web Services and NetworkService cannot have SPNs assigned to it.
  
To solve the issue of not having Active Directory objects to hold the SPNs, Lync Server Control Panel can use computer account objects for this purpose. The computer account objects can hold the SPNs and are not subject to password expiration, which was an issue with using user accounts in previous versions. 
  
You use Windows PowerShell cmdlets to configure the computer objects to provide Kerberos authentication.
  
## In this section

- [Prerequisites for enabling Kerberos authentication in Lync Server 2013](prerequisites-for-enabling-kerberos-authentication.md)
    
- [Create a Kerberos authentication account in Lync Server 2013](create-a-kerberos-authentication-account.md)
    
- [Assign a Kerberos authentication account to a site in Lync Server 2013](assign-a-kerberos-authentication-account-to-a-site.md)
    
- [Setting up Kerberos authentication account passwords in Lync Server 2013](setting-up-kerberos-authentication-account-passwords.md)
    
- [In Lync Server 2013 add Kerberos authentication to other sites](add-kerberos-authentication-to-other-sites.md)
    
- [In Lync Server 2013 remove Kerberos authentication from a site](remove-kerberos-authentication-from-a-site.md)
    
- [Testing and reporting the status and assignment of Kerberos authentication in Lync Server 2013](testing-and-reporting-the-status-and-assignment-of-kerberos-authentication.md)
    

