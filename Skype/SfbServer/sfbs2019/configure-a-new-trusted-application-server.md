---
title: "Configure a new trusted application server in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a7233db7-fac3-43ff-972e-3bc29a56adb3
description: "A trusted application is an application based on Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK that is trusted by Microsoft Lync Server 2013. For details about UCMA applications, seeUnified Communications Managed API 3.0 Core SDK Documentationat https://go.microsoft.com/fwlink/p/?linkId=210320."
---

# Configure a new trusted application server in Lync Server 2013
[]
A trusted application is an application based on Microsoft Unified Communications Managed API (UCMA) 3.0 Core SDK that is trusted by Microsoft Lync Server 2013. For details about UCMA applications, see "Unified Communications Managed API 3.0 Core SDK Documentation" at [https://go.microsoft.com/fwlink/p/?linkId=210320](https://go.microsoft.com/fwlink/p/?linkId=210320).
  
For information about configuring Microsoft Outlook Web Access (OWA) and Lync Server 2013, see "Configure Outlook Web App and Lync Server 2010 Integration" at the Microsoft Exchange Server 2013 documentation.
  
To successfully publish, enable, or disable a topology when adding or removing a server role, you should be logged on as a user who is a member of the RTCUniversalServerAdmins and Domain Admins groups. It is also possible to delegate the proper administrator permissions and rights for adding server roles. For details, see [Delegate setup permissions in Lync Server 2013](delegate-setup-permissions.md) in the Deployment documentation. For other configuration changes, only membership in the RTCUniversalServerAdmins group is required. 
  
### To configure a trusted application server

1. Log on to the computer where Topology Builder is installed as a member of the Domain Admins group and the RTCUniversalServerAdmins group.
    
2. Start Topology Builder: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Topology Builder**.
    
3. Select **Download topology from existing deployment**, and then click **OK**.
    
4. In the **Save Topology As** dialog box, click the Topology Builder file you want to use, and then click **Save**.
    
5. In the left pane, right-click **Trusted application servers**, and then click **New Trusted Application Pool**.
    
6. Enter the **Pool FQDN** of the trusted application pool, select whether it will be a single-server or multiple-server, and then click **Next**.
    
7. On the **Select the next hop** page, from the list, select the Lync Server 2013 Front End pool. 
    
8. Click **Finish**.
    
9. Select the top node **Lync Server 2013**, and then, from the **Actions** menu, click **Publish Topology**.
    
    The **Trusted Application Pool** should have been created successfully and associated with the correct Front End pool. 
    

