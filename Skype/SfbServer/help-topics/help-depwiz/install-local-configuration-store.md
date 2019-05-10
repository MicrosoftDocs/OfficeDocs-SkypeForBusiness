---
title: "Install Local Configuration Store"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 4/13/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.dep.DeployMainInstallReplica
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: d9c4bcc2-11a7-4d4d-858d-224db217ad32
description: "To begin the installation of a new Skype for Business Server 2015 role server, you must first install the local SQL Server that will host the local configuration store. The local configuration store will act as a read-only replica of the Skype for Business Server Central Management store (CMS). You must be logged on to the server that you are running the Install Local Configuration Store step as the local administrator on the computer, and have membership in the RTCUniversalServerAdmins or the RTCUniversalGlobalReadOnlyGroup group. If you are performing the setup on an Edge Server, you do not have to be a member of the RTCUniversalServerAdmins or the RTCUniversalGlobalReadOnlyGroup group. The Topology Builder definition document will be read from the exported definition document instead of from the Central Management store. To export the Topology Builder definition document and make it available to the Edge Servers, see the topic Export Your Topology and Copy It to External Media for Edge Installation."
---

# Install Local Configuration Store

To begin the installation of a new Skype for Business Server 2015 role server, you must first install the local SQL Server that will host the local configuration store. The local configuration store will act as a read-only replica of the Skype for Business Server Central Management store (CMS). You must be logged on to the server that you are running the **Install Local Configuration Store** step as the local administrator on the computer, and have membership in the RTCUniversalServerAdmins or the RTCUniversalGlobalReadOnlyGroup group. If you are performing the setup on an Edge Server, you do not have to be a member of the RTCUniversalServerAdmins or the RTCUniversalGlobalReadOnlyGroup group. The Topology Builder definition document will be read from the exported definition document instead of from the Central Management store. To export the Topology Builder definition document and make it available to the Edge Servers, see the topic [Export Your Topology and Copy It to External Media for Edge Installation](https://technet.microsoft.com/library/def9f416-c519-4a72-b242-7d3057d9c1fd.aspx).

To begin the installation:

1. On the Skype for Business Server 2015 page, next to **Step1: Install Local Configuration Store**, click **Run**.

2. On the **Local Server Configuration** page, be sure that the **Retrieve configuration automatically from the Central Management Store** option is selected, and then click **Next**.

3. When the local server configuration installation is complete, click **Finish**.

> [!NOTE]
> The installation of the local SQL Server can take some time. You will not see updates on progress in the installation summary screen while SQL Server is being installed. If you want to monitor the progress of the installation, use Task Manager to watch the SQL Server setup.


