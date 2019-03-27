---
title: 'Preventing new connections'
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: ""
---

# Preventing new connections to Skype for Business Server for server maintenance


Skype for Business Server enables you to take a server offline (for example, to apply software or hardware upgrades) without any loss of service to users.

When you specify the option to prevent new connections or calls to a server in a pool, it stops taking any new connections and calls as soon as you implement this option. These new connections and calls are routed through other servers in the pool. A server that is preventing new connections allows its sessions on existing connections to continue until they naturally end. When all existing sessions have ended, the server is ready to be taken offline.

When you prevent new connections to a Front End Server, some Skype for Business Server features and services rely on DNS load balancing to ensure that it functions properly. If you are not using DNS load balancing on the pool, connections through these services may not be re-routed to other servers during the period that the server is preventing new connections, and thus when the server is taken offline some sessions and calls may be interrupted. The features that rely on DNS load balancing to ensure that this option operates properly are as follows:

  - Attendant

  - Conferencing Announcement application

  - Response Group application

  - Announcement application

  - Call Park application

For details about DNS load balancing, see [Load balancing requirements](../../plan-your-deployment/network-requirements/load-balancing.md).

In addition to preventing new connections for all services on a server running Skype for Business Server, you can also prevent new connections for individual Skype for Business Server services. For example, this method is useful in a situation where you need to apply a Skype for Business Server update that does not require the whole server to be shut down. Note that when you prevent connections for one service, you must select a service as it is grouped and displayed in the Windows list of services. For example, the Skype for Business Server Front-End service and the data collection agent for Monitoring are separate Skype for Business Server services, but in the Windows services list they are consolidated and shown as the Skype for Business Server Front End service. You can prevent new connections for the Skype for Business Server Front End service, but you cannot prevent new connections for these two individual underlying Skype for Business Server services separately.

> [!IMPORTANT]
> When you set a server to prevent new connections, and then restart the server, by default the server will immediately begin accepting new connections after it starts. To prevent this, set the server to only pause and resume manually, before you restart the server.

## To prevent new connections to Skype for Business Server

1.  Log on to the local computer as a member of the Administrators group.

2.  Open the Services snap-in console: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**.

3.  In the list, double-click the Skype for Business Server Windows service to which you want to prevent new connections.

4.  In the Properties dialog box, under **Service status: Started**, click **Pause**.

5.  Optionally, but recommended, next to **Startup type**, click **Manual**.
    
    > [!IMPORTANT]
    > When you set a server to prevent new connections, and then restart the server, by default the server will immediately begin accepting new connections after it starts. To prevent this, set the server to only pause and resume manually, before you restart the server.
