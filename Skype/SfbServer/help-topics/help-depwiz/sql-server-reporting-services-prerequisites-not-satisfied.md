---
title: "SQL Server Reporting Services (Prerequisites Not Satisfied)"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/26/2015
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.dep.DeploySSRSPrereqNotSatisfied
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: b6be29df-b882-4ba8-ba40-8062eb3bb14d
description: "You see this page if there's no Monitoring Server deployed in your infrastructure. This indicates that the minimum requirements for deploying Monitoring Server reports aren't met."
---

# SQL Server Reporting Services (Prerequisites Not Satisfied)

You see this page if there's no Monitoring Server deployed in your infrastructure. This indicates that the minimum requirements for deploying Monitoring Server reports aren't met.

To resolve this issue, make sure that you have a Monitoring Server joined to the domain, that it's defined in Topology Builder, and that the topology is published. SQL Server Reporting Services must also be available on the SQL Server, and installed as a feature into the Monitoring Server database on the SQL Server.

For details, see [Install Monitoring Reports in Skype for Business Server 2015](../../deploy/deploy-monitoring/install-monitoring-reports.md) and [Deploying Monitoring](/previous-versions/office/lync-server-2013/lync-server-2013-deploying-monitoring).