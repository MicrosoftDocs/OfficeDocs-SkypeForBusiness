---
title: "Configuring your Lync Server 2013 environment for the Lync Room System Administrative Web Portal"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1bf3cc55-cfa8-46ee-a8bc-6dab3bff76b2
description: "To use the Lync Room System (LRS) Administrative Web Portal, you will need to install or configure the following prerequisites."
---

# Configuring your Lync Server 2013 environment for the Lync Room System Administrative Web Portal
[]
To use the Lync Room System (LRS) Administrative Web Portal, you will need to install or configure the following prerequisites.
  
> [!IMPORTANT]
> If the server is configured with both Kerberos and NTLM authentication, and LRS is running on a computer that is not joined to the domain, Kerberos authentication will fail and the user will not see the status of LRS in the administrative portal. To resolve this issue, configure the server with NTLM authentication or both NTLM and TLS-DSK authentication (without Kerberos), or join the LRS computer to the domain. 
  
1. Install Lync Server 2013 Cumulative Updates: July 2013 in the Lync Server topology. 
    
    To get the update or see what's included with it, see [Updates for Lync Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=323959).
    
2. Create a SIP-enabled Active Directory user.
    
    The LRS Administrative Web Portal uses these credentials to query information from Lync Server. The recommended username is LRSApp.
    
3. Create an Active Directory security group with name LRSSupportAdminGroup.
    
    Create the group with Group Scope as Global and Group Type as Security. SIP enabled users who are added to this group will be authorized to see the list of rooms and execute certain commands, such as collecting logs.
    
4. Create an Active Directory security group with name LRSFullAccessAdminGroup. 
    
    Create the group with Group Scope as Global and Group Type as Security.SIP enabled users who are added to this group are authorized to use all admin portal functionality. 
    
     ![List of Admin Groups with security group role](media/LRS_LRSFullAccessAdminGroup.png)
  
5. Add LRSFullAccessAdminGroup as a member of LRSSupportAdminGroup.
    
     ![LRSSupportAdminGroup Properties Members page](media/LRS_Add_LRSSupportAdminGroup.png)
  
6. Create a SIP enabled Active Directory user with name LRSSupport. Add this user to LRSSupportAdminGroup.
    
     ![LRSSupportAdminGroup Properties Members page](media/LRS_Add_LRS_SIP_SupportUser.png)
  
7. Install ASP.NET MVC 4 for Visual Studio 2010 SP1 and Visual Web Developer 2010 SP1, available in the Microsoft Download Center at [https://go.microsoft.com/fwlink/p/?LinkId=323967](https://go.microsoft.com/fwlink/p/?LinkId=323967).
    

