---
title: 'Lync Server 2013: Configuring your environment for the Lync Room System Administrative Web Portal'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring your environment for the Lync Room System Administrative Web Portal
ms:assetid: 1bf3cc55-cfa8-46ee-a8bc-6dab3bff76b2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn436325(v=OCS.15)
ms:contentKeyID: 56737623
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring your Lync Server 2013 environment for the Lync Room System Administrative Web Portal

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-22_

To use the Lync Room System (LRS) Administrative Web Portal, you will need to install or configure the following prerequisites.

<div>


> [!IMPORTANT]  
> If the server is configured with both Kerberos and NTLM authentication, and LRS is running on a computer that is not joined to the domain, Kerberos authentication will fail and the user will not see the status of LRS in the administrative portal. To resolve this issue, configure the server with NTLM authentication or both NTLM and TLS-DSK authentication (without Kerberos), or join the LRS computer to the domain.



</div>

1.  Install Lync Server 2013 Cumulative Updates: July 2013 in the Lync Server topology.
    
    To get the update or see what’s included with it, see [Updates for Lync Server 2013](http://go.microsoft.com/fwlink/p/?linkid=323959).

2.  Create a SIP-enabled Active Directory user.
    
    The LRS Administrative Web Portal uses these credentials to query information from Lync Server. The recommended username is LRSApp.

3.  Create an Active Directory security group with name LRSSupportAdminGroup.
    
    Create the group with Group Scope as Global and Group Type as Security. SIP enabled users who are added to this group will be authorized to see the list of rooms and execute certain commands, such as collecting logs.

4.  Create an Active Directory security group with name LRSFullAccessAdminGroup.
    
    Create the group with Group Scope as Global and Group Type as Security.SIP enabled users who are added to this group are authorized to use all admin portal functionality.
    
     
    
    ![List of Admin Groups with security group role](images/Dn436325.5d432819-a2e2-452c-bc2a-5d4ee79d8c33(OCS.15).png "List of Admin Groups with security group role")  
    
     

5.  Add LRSFullAccessAdminGroup as a member of LRSSupportAdminGroup.
    
    ![LRSSupportAdminGroup Properties Members page](images/Dn436325.91a4a28a-cacf-4ef6-aac1-915ec41c9648(OCS.15).png "LRSSupportAdminGroup Properties Members page")  
    
     

6.  Create a SIP enabled Active Directory user with name LRSSupport. Add this user to LRSSupportAdminGroup.
    
    ![LRSSupportAdminGroup Properties Members page](images/Dn436325.7638055d-22ac-4909-914d-1966f5623909(OCS.15).png "LRSSupportAdminGroup Properties Members page")  
    
     

7.  Install ASP.NET MVC 4 for Visual Studio 2010 SP1 and Visual Web Developer 2010 SP1, available in the Microsoft Download Center at [http://go.microsoft.com/fwlink/p/?LinkId=323967](http://go.microsoft.com/fwlink/p/?linkid=323967).

</div>

<span> </span>

</div>

</div>

</div>

