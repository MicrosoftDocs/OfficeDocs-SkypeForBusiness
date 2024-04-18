---
ms.date: 03/17/2018
title: "SQL Server Reporting Services (Prerequisites Not Satisfied)"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.dep.DeploySSRSPrereqNotSatisfied
ms.service: skype-for-business-server
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: b6be29df-b882-4ba8-ba40-8062eb3bb14d
ROBOTS: NOINDEX, NOFOLLOW
description: "You see this page if there's no Monitoring Server deployed in your infrastructure. This indicates that the minimum requirements for deploying Monitoring Server reports haven't met."
---

# SQL Server Reporting Services (Prerequisites Not Satisfied)

You see this page if there's no Monitoring Server deployed in your infrastructure. This indicates that the minimum requirements for deploying Monitoring Server reports haven't met.

To resolve the issue, ensure that you have a Monitoring Server joined to the domain that's defined in Topology Builder. The topology must be published. SQL Server Reporting Services must also be available on the SQL Server, and installed as a feature into the Monitoring Server database on the SQL Server.

For details, see [Install Monitoring Reports in Skype for Business Server](../../../deploy/deploy-monitoring/install-monitoring-reports.md) and [Deploying Monitoring](/previous-versions/office/lync-server-2013/lync-server-2013-deploying-monitoring).
