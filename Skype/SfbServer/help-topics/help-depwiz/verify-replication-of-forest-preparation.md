---
title: "Verify Replication of Forest Preparation"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 2/8/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployMainVerifyForestPrep
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 94e87632-7c28-43df-9238-f5a47c1c43c0
description: "To confirm that the replication of the Global Catalog and the creation of objects during Forest Preparation have been successful, do the following:"
---

# Verify Replication of Forest Preparation
 
To confirm that the replication of the Global Catalog and the creation of objects during Forest Preparation have been successful, do the following:
  
1. On a domain controller (preferably in a remote site from the other domain controllers), in the forest where the Forest Preparation was run, open **Active Directory Users and Computers**.
    
2. In **Active Directory Users and Computers**, expand the domain name of your forest or a child domain.
    
3. Click the **Users** container on the left side pane and look for the Universal group CsAdministrator in the right side pane. If CsAdministrator (among eight other new Universal groups that begin with Cs) is present, replication of the Forest Preparation has been successful.
    
4. If the group(s) is not yet present, you can force the replication or wait 15 minutes and refresh the right side pane. When the groups are present, replication is complete.
    
> [!TIP]
> If you want to review the log files that are created by the Skype for Business Server Deployment Wizard, you can find them on the computer where the Deployment Wizard was run, in the Users directory of the Active Directory Domain Services user who ran the step. For example, if the user logged in as the domain administrator in the domain Contoso.net, the log files are located in: C:\Users\Administrator.Contoso\AppData\Local\Temp 
  

