---
ms.date: 03/17/2018
title: "Troubleshoot Statistics Manager for Skype for Business Server"
ms.reviewer:
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
ms.assetid: 946189fa-521f-455c-9762-904e7e41b791
description: "Summary: Read this article to troubleshoot your deployment of Statistics Manager for Skype for Business Server."
---

# Troubleshoot Statistics Manager for Skype for Business Server

**Summary:** Read this article to troubleshoot your deployment of Statistics Manager for Skype for Business Server.

This article describes how to troubleshoot your Statistics Manager deployment by describing events you might see in the Application event log, and appropriate actions you might take to rectify the event. This article contains the following sections:

- [Agent events](troubleshoot.md#BKMK_Agent)

- [Listener events](troubleshoot.md#BKMK_Listener)

- [Website issues](troubleshoot.md#BKMK_Website)

## Agent events
<a name="BKMK_Agent"> </a>

- **1000** — Unable to set up processor limiter (Job Object)—Unknown reason

- **1001**—Process limiting isn't allowed on the process (probably already inside a Job Object)

    The Agent runs inside of a Windows Job Object to automatically limit its memory footprint. If the agent doesn't start and these event entries are present in the event log, the Job Object isn't able to be instantiated on the server. To work around this, the upper memory limit can be removed by changing a value in the config file:

  ```console
  C:\Program Files\Skype for Business Server StatsMan Agent\PerfAgent.exe.config
  ```

    Search for "MaxProcessMemoryMB" and change the value to "0" as shown:

  ```xml
  <setting name="MaxProcessMemoryMB" serializeAs="String"> <value>300</value> </setting>
  ```

    > [!NOTE]
    > If this change is made, the Agent will generally still consume \< 100 MB of memory, however it will not be forcefully limited to 300 MB as is the default. If this change is made, we recommend closely monitoring memory usage to ensure the Agent does not consume a large amount of memory on its host machine.

- **2000**—Client initialization failure

- **2001**—No connection could be made to the service on any source IP

  If the Agent can't connect to the Listener computer, check the following:

  1. Ensure the Listener service is running on the Listener computer. If not, ensure Redis is running on that server, and then restart the Listener service.

     Check the Statistics Manager event sign in the Listener computer to ensure there are no issues with the Statistics Manager Listener service itself.

  2. Use a connectivity tool such as telnet to verify connectivity from the Agent computer to the Listener on the correct port.

     If not, make sure the incoming firewall rule is enabled on the Listener computer for the network type that the Listener computer is connected to (private/public/domain). If the Listener computer isn't joined to a domain, the network might be listed as public and in that case the firewall rules installed with Statistics Manager doesn't apply by default.

- **4000**—Failure to download Server Info from Listener (unknown reason)

  - **4001** — Server Not Found in Listener Topology

    This error occurs if the server is successfully connecting to the Listener, but the server wasn't added to the topology in the Listener's cache. Resolution options:

  - Make sure you followed the instructions for importing the topology. See [Import the topology](deploy.md#BKMK_ImportTopology).

  - If the Agent is on a server that isn't listed in the topology (for example, the nodes in a SQL AlwaysOn cluster), you need to add the Agent manually by following the instructions in [Import the topology](deploy.md#BKMK_ImportTopology).

  - **4002**—Invalid Listener Password

    The encrypted password that the agent is attempting to use doesn't match the service password on the Listener itself. Uninstall the Agent and reinstall it using the correct service password.

  - **4003**—Certificate Thumbprint Mismatch

    The certificate thumbprint given to the Agent at install time doesn't match the thumbprint on the certificate the Listener is currently using and therefore the connection is refused. Uninstall the Agent and reinstall it using the correct certificate thumbprint.

  - **4004**—Invalid Response or HttpStatusCode

    The Listener isn't responding with an expected status.

  - If the connection is proxied, check the proxy configuration.

  - Check the Listener computer's StatsMan log for issues with its configuration.

  - **4005**—Couldn't deserialize the XML

    The server info on the Listener server is corrupt or there might be a version mismatch between the Agent and the Listener computers. Ensure the versions match and check the Listener event log for issues.

## Listener events
<a name="BKMK_Listener"> </a>

- **10000**—Startup failure Unknown reason (these are unrecoverable and the service will stop/crash as a result)

  - **10001**—Configuration problem

    Generally this occurs when the [listener_install_location]\PerfAgentListener.exe.config file is modified by hand and not readable by the application.

  - **10002**—HTTP Listener initialization error

    This event will generally be logged when the URL ACL isn't set properly during installation or the SSL Cert is invalid. Ensure the certificate in your configuration is valid. If it is, reinstall the Listener according to the instructions in [Deploy Statistics Manager](deploy.md#BKMK_Deploy).

  - **10003**—Redis failure

  - **10004**—Caching infrastructure failure

  - **10007**—Settings (stored in redis)

    The Listener couldn't contact Redis or retrieve well-formed data from the cache and couldn't start. Ensure the Redis service is started and configured properly on the server.

  - **10005**—Server info retrieval/parsing

    The topology information in the Redis cache is invalid. First, attempt to restart Redis and the Listener. If the error persists, see [Import the topology](deploy.md#BKMK_ImportTopology) to recreate the topology data.

- **10100**—Redis PING outage

  - **10101**—Redis PING continued outage (every 60 seconds)

  - **30100**—Redis PING outage restored

    These are logged when the Listener can't connect to Redis. Ensure Redis is started and network connectivity between the Listener and Redis is available.

- **10200**—Redis Write outage

  - **10201**—Redis Write outage continued (every 60 seconds)

  - **30100**—Redis Write outage resolved

    These are logged when the Listener can't write to the Redis cache. Ensure Redis is started and network connectivity between the Listener and Redis is available.

- **30000**—Successfully started

    Logged each time the Listener is started.

- **22000**—Initialization of Statistics Manager Agent succeeded.

- **23000**—Initialization of EventLogQueryManager succeeded (first time or after failing)

- **24000**—Initialization of server info succeeded (first time or after failing)

- **25000** Listener is back online after failing to post (or first successful post)

- **5000**—Start of listener offline for posting data

- **5001**—Listener is still offline for an extended period

    These events can be useful for monitoring/alerting/clearing issues.

## Website issues
<a name="BKMK_Website"> </a>

- Repetitive sign in prompts in Chrome - this was a bug that was resolved in version 1.1. Be sure you have upgraded to the latest version of Statistics Manager if you're seeing repeated sign in prompts in the Chrome browser. To verify the version of the website you are running:

  - In File Explorer, open (default directory)

  - Right select on StatsManHubWebSite.dll and view its properties.

  - If a computer can't be found in the KHI Landscape view or the Counter Details view, make sure it's a member of a Site and a Pool. If it isn't, it will not appear in those views. For information about defining a site and pool for a server in the topology, see [Import the topology](deploy.md#BKMK_ImportTopology).

  - The product version is shown in the Description details.

## For more information
<a name="BKMK_Website"> </a>

For more information, see the following:

- [Plan for Statistics Manager for Skype for Business Server](plan.md)

- [Deploy Statistics Manager for Skype for Business Server](deploy.md)

- [Upgrade Statistics Manager for Skype for Business Server](upgrade.md)

