---
title: "Create a Persistent Chat administrator in Skype for Business Server 2015"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5c3892e4-ebae-453e-8107-f42ec0436ea2
description: "Summary: Read this topic to learn how to create a Persistent Chat Server administrator role to enable initial configuration and management of Persistent Chat services in Skype for Business Server 2015."
---

# Create a Persistent Chat administrator in Skype for Business Server 2015
 
**Summary:** Read this topic to learn how to create a Persistent Chat Server administrator role to enable initial configuration and management of Persistent Chat services in Skype for Business Server 2015.
  
In Skype for Business Server, users who perform specific tasks must be assigned as members of one or more specific groups. Role-Based Access Control (RBAC) is used to grant privileges by assigning users to predefined Skype for Business Server administrative roles. These roles correspond to universal security groups in Active Directory Domain Services. Members of the Persistent Chat Administrator security group, CsPersistentChatAdministrator, are granted access to the Persistent Chat Server cmdlets, which can be executed using either the Skype for Business Server Management Shell or the Skype for Business Server Control Panel.
  
Before configuring and administering Persistent Chat Server, be sure that the appropriate user rights and permissions are in place, and that any users who will act as Persistent Chat administrators are added to the Persistent Chat Administrator security group.
  
> [!NOTE] 
> Persistent chat is available in Skype for Business Server 2015 but is no longer supported in Skype for Business Server 2019. The same functionality is available in Teams. For more information, see [Journey from Skype for Business to Microsoft Teams](/microsoftteams/journey-skypeforbusiness-teams). If you need to use Persistent chat, your choices are to either migrate users requiring this functionality to Teams, or to continue using Skype for Business Server 2015.

## Create a Persistent Chat administrator

To add a user to the Persistent Chat Administrator security group, CsPersistentChatAdministrator, perform the following steps:
  
1. Using an account that has permission to modify the membership of an Active Directory group, log on to a computer where Active Directory Users and Computers have been installed.
    
2. Click Start, click All Programs, click Administrative Tools, and then click Active Directory Users and Computers.
    
3. In Active Directory Users and Computers, expand the name of your domain and click the Users container.
    
4. Right-click the security group CsPersistentChatAdministrator, and then click Properties.
    
5. In the Properties dialog box, on the Members tab, click Add.
    
6. In the Select Users, Computers, Contact, or Groups dialog box, type the user name or display name of the user to be added to the group in the Enter the object names to select box and then click OK.
    
7. In the Properties dialog box, click OK.
    

