---
title: "Test the pool deployment in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ffd80617-155a-4041-bbeb-74503e7938dd
description: "The following procedure describes how to test the deployment of the Front End pool."
---

# Test the pool deployment in Lync Server 2013
[]
The following procedure describes how to test the deployment of the Front End pool.
  
### To test the pool deployment

1. Use Active Directory Computers and Users to add the Active Directory user object of the administrator role for the Lync Server 2013 deployment (on which Lync Server 2013 Control Panel is installed) to the **CSAdministrator** group. 
    
    > [!IMPORTANT]
    > If you do not add the appropriate users and groups to the CsAdministors group, you will receive an error when opening Lync Server Control Panel, which states that "Unauthorized: Access is denied due to a role-based access control (RBAC) authorization failure." 
  
2. If the user object is currently logged on, log off and then log on again to register the new group assignment.
    
    > [!NOTE]
    > The user account cannot be the local administrator of any server running Lync Server 2013. 
  
3. Use the administrative account to log on to the computer where Lync Server Control Panel is installed.
    
4. Start Lync Server Control Panel, and then provide credentials, if prompted. Lync Server Control Panel displays deployment information.
    
5. In the left navigation bar, click **Topology**, and then confirm that the service status shows a computer with a green arrow and that a green check mark for replication status is next to each Lync Server server role that has been deployed and brought online. 
    
6. In the left navigation bar, click **Users**, and then click **Enable users**. 
    
7. On the **New Lync Server User** page, click **Add**.
    
8. To define search parameters for the objects you want to find, on the **Select from Active Directory** page, you can select **Search**, and then optionally click **Add Filter**. You can also select **LDAP search** and enter an LDAP expression to filter or limit the objects that will be returned. After you have decided on your Search options, clink **Find**.
    
9. In the Search results pane, select all the objects for this search session, and then click **OK**.
    
10. On the **New Lync Server User** page, the object or objects you selected are in the **Users** display. In the **Assign users to a pool** list, select the server where the objects should be homed. 
    
    Following are a number of options for configuring the objects.
    
  - **Generate user's SIP URI**
    
  - **Telephony**
    
  - **Line URI**
    
  - **Conferencing policy**
    
  - **Client version policy**
    
  - **PIN policy**
    
  - **External access policy**
    
  - **Archiving policy**
    
  - **Location policy**
    
  - **Client policy**
    
    For the purposes of testing the basic functionality, select the option you prefer for the **Generate user's SIP URI** setting (the other options in the configuration will use default settings), and then click **Enable**.
    
11. A summary page is displayed that shows a check mark in the **Enabled** column to indicate that the objects are now ready for use. The **SIP address** column displays the address you need for the user sign-in configuration. 
    
12. Log one user on to a computer that is joined to the domain, and another user on to another computer in the domain.
    
13. Install Lync 2013 on each of the two client computers, and then verify that both users can sign in to Lync Server 2013 and can send instant messages to each other.
    
## See also

#### 

[Deploying clients and devices in Lync Server 2013](deploying-clients-and-devices.md)

