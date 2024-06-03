---
title: "Prepare Single Standard Edition Server (Intro)"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/23/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.dep.DeployAIOIntro
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: fe11d380-54c9-47e7-a676-02b9a59dc93f
description: "To begin the installation of a Skype for Business Server 2015 Standard Edition server that holds the Central Management store and other collocated services that you select, you must be logged in as a member of the local Administrators group on the server that will become the Standard Edition server. The Prepare single Standard Edition Server page details the requirements for the initial install. The computer must be a member of the domain in which you deploy it, and you must successfully complete the Schema, Forest, and Domain prep for your forest."
---

# Prepare Single Standard Edition Server (Intro)
 
To begin the installation of a Skype for Business Server 2015 Standard Edition server that holds the Central Management store and other collocated services that you select, you must be logged in as a member of the local Administrators group on the server that becomes the Standard Edition server. The **Prepare single Standard Edition Server** page details the requirements for the initial install. The computer must be a member of the domain in which you deploy it, and you must successfully complete the Schema, Forest, and Domain prep for your forest.
  
This particular task is designed to set up a Standard Edition server as the first server in your infrastructure. This task installs the Central Management store, which is SQL Server Express, onto the Standard Edition server. If you already have another Standard Edition server or Front End pool deployed, you should select **Cancel**.
  
> [!NOTE]
> After completing this task, you will install Topology Builder (if you have not already installed it) and configure your topology document. You cannot publish your topology document until you have a Central Management store available—which is deployed by completing the task described in this topic. 
  

