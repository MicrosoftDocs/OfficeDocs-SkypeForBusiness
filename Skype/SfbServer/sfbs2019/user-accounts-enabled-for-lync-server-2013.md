---
title: "User accounts enabled for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8021087e-5084-4a39-9fef-ab9376c6d371
description: "Topics in this section provide step-by-step procedures for configuring user settings that you can perform using the Lync Server 2013 Control Panel."
---

# User accounts enabled for Lync Server 2013
[]
Topics in this section provide step-by-step procedures for configuring user settings that you can perform using the Lync Server 2013 Control Panel.
  
> [!IMPORTANT]
> You cannot use Lync Server Control Panel to manage users who are members of the Active Directory Domain Admins group. For Domain Admins users, you can use Lync Server Control Panel only to perform read-only search operations. To perform write operations on Domain Admins users (for example, enable or disable for Lync Server Control Panel, change pool or policy assignments, telephony settings, SIP address), you must use Windows PowerShell cmdlets while logged on as a Domain Admins user. For details about using Windows PowerShell cmdlets to manage users, see [Lync Server 2013 Management Shell](lync-server-management-shell.md). 
  
When you perform any Lync Server 2013 administrative task that involves searching for a user or filtering user search results, there are some user properties that exist as attributes in Active Directory Domain Services but are not replicated to the global catalog until Microsoft Exchange Server is deployed. Microsoft Exchange, not Lync Server, marks the following attributes for replication to the global catalog when it is installed:
  
|**User Information**|**Address and Phone**|**Organization**|
|:-----|:-----|:-----|
|Initials  <br/> |Street address  <br/> Country/region  <br/> Pager  <br/> Fax  <br/> Mobile  <br/> |Title  <br/> Company  <br/> Department  <br/> Office  <br/> |
   
## In this section

- [Viewing information about user accounts enabled for Lync Server 2013](viewing-information-about-user-accounts-enabled-for-lync-server-2013.md)
    
- [Enabling and disabling users for Lync Server 2013](enabling-and-disabling-users-for-lync-server-2013.md)
    
- [Managing Enterprise Voice for users in Lync Server 2013](managing-enterprise-voice-for-users.md)
    
- [Modifying user account properties in Lync Server 2013](modifying-user-account-properties.md)
    
- [Manage external access policy in Lync Server 2013](manage-external-access-policy-for-your-organization.md)
    
- [Assigning per-user policies in Lync Server 2013](assigning-per-user-policies.md)
    
## See also

#### 

[User management cmdlets in Lync Server 2013](user-management-cmdlets.md)
#### 

[Managing users in Lync Server 2013](managing-users-in-lync-server-2013.md)

