---
title: "Create Skype for Business Server Control Panel Administrators"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployMainCreateCSCPAdmin
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3312926a-4671-4030-bb92-90ac24c778dd
ROBOTS: NOINDEX, NOFOLLOW
description: "To grant access to the Skype for Business Server, do the following:"
---

# Create Skype for Business Server Control Panel Administrators
 
To grant access to the Skype for Business Server, do the following:
  
1. Log on as a member of the Domain Admins group or the RTCUniversalServerAdmins group.
    
2. Open **Active Directory Users and Computers**, expand your domain, right-click the **Users** container, and then click **Properties**.
    
3. In **CSAdministrator Properties**, click the **Members** tab.
    
4. On the Members tab, click **Add**. In **Select Users, Contacts, Computers, Service Accounts, or Groups**, locate the **Enter the object names to select**. Type the user name(s) or group name(s) to add to the group CSAdministrators. Click **OK**.
    
5. On the Members tab, confirm that the users or groups that you selected are present. Click **OK**.
    
> [!TIP]
> The Skype for Business Server Control Panel is a role-based access control tool. Membership in the CsAdministrator group gives a user who is using the Skype for Business Server Control Panel full control for all the configuration functions available. There are other roles available that are designed for specific functions. Users do not have to be enabled for Skype for Business Server in order to be made members of the management groups. 
  
Other roles include:
  
- **CsArchiving:** Members of this group can perform all archiving functions, such as configuring and managing the Archiving Server role.
    
- **CsHelpDesk:** Members of this group can view the configuration and deployment, including user properties and policies. Members can also perform specific troubleshooting tasks.
    
- **CsLocationAdministrator:** Members have the lowest level of user rights associated with Enhanced 9-1-1 (E9-1-1) management. They can create E9-1-1 locations and network identifiers and associate those in the deployment.
    
- **CsResponseGroupAdministrator:** Members can manage and configure the Response Group service.
    
- **CsServerAdministrator:** Members can manage, monitor, and troubleshoot all servers running Skype for Business Server.
    
- **CsUserAdministrator:** Members can manage, enable and disable users, and assign existing policies to users.
    
- **CsViewOnlyAdministrator:** Members can view the deployment and configuration of the server information. This membership enables a member to monitor the health of the servers running Skype for Business Server.
    
- **CsVoiceAdministrator:** Members can create, configure, and manage voice-related settings in Skype for Business Server.
    
To help retain security and role-based access control integrity, add users to the groups that define what role the user performs in management of the Skype for Business Server deployment.
  

