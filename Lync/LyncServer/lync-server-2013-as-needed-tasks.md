---
title: 'Lync Server 2013: As-needed tasks'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: As-needed tasks
ms:assetid: b66bc6fe-f138-4cf4-ba7f-aee9a3e0497e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn722431(v=OCS.15)
ms:contentKeyID: 63969643
ms.date: 01/27/2015
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# As-needed tasks in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-18_

Perform the following tasks as necessary. They are frequently also covered by standard procedures:

  - **Full Security Auditing   **You can perform this audit regularly, in response to an upgrade or redesign of the messaging system, or in response to an attempted (or successful) security breach. The procedure may involve port scans on servers and firewalls, audits of security fixes, and third-party penetration tests.

  - **Replace Certificates about to Expire**   Checking Lync Server Certificates is one of regular weekly tasks, and as part of the procedure an administrator should have a record of all certificates’ expiry dates. This record enables an administrator to create a notification when a particular certificate is about to be expired and replaced as needed.

  - **Updating Performance Baselines**   Update performance baselines after an upgrade or configuration change. Your organization can use baselines to measure performance changes and to detect issues that affect system performance.

  - **Managing Enterprise Pool**   Initial configuration of Enterprise pools, Standard Edition servers, and any other servers in your organization's environment were done during deployment of the individual servers. Post-deployment management of servers and pools for Standard Edition servers and Enterprise pools includes the following tasks:
    
      - Managing Front End Servers
    
      - Managing Web Conferencing
    
      - Managing Conferencing
    
      - Changing Service Account Credentials
    
      - Managing Databases
    
      - Starting and Stopping Services and Deactivating Server Roles
    
      - Removing Servers and Server Roles, Removing Pools, and Decommissioning Servers and Pools

  - **Managing Usage**   You can configure Lync Server 2013 to provide the features and functionality that are most appropriate for your organization. This includes the following:
    
      - Managing Support for On-Premise Web Conferencing Meetings
    
      - Managing the Use of Distribution Groups to Send Instant Messages
    
      - Managing Contacts, Presence, and Queries
    
      - Configuring Client Version Filtering
    
      - Configuring Intelligent IM Filtering
    
      - Configuring Archiving, Call Detail Recording, and Meeting Compliance

  - **Managing Edge Server Connectivity**   Ongoing management of the servers and settings required to provide external connectivity includes the following:
    
      - Managing Connectivity between Internal Servers and Edge Servers
    
      - Configuring Internal and External Interfaces and Certificates for Edge Servers
    
      - Managing Federated Partner Access

  - **Administering the Address Book**   Administering Address Book Servers includes the following:
    
      - Configuring Address Book Server phone normalization
    
      - Managing the Address Book Server from the command line

  - **Managing User Accounts**   Management of user accounts includes the following:
    
      - Enabling User Accounts for Lync Server
    
      - Configuring Lync Server Users using the Wizard
    
      - Configuring Individual Lync Server User Account Properties
    
      - Searching for Lync Server Users
    
      - Moving Lync Server Users
    
      - Deleting Lync Server Users

  - **Analyzing Lync Server 2013 Log Files**   One very helpful tool, generally used for troubleshooting, is the Lync Server 2013 Logging Tool described in detail in [Using Lync Server 2013 Logging Tool](http://technet.microsoft.com/en-us/library/gg558599.aspx).

Because the Logging Tool generates log files (on a per-server basis), these log files can be viewed and analyzed by using the Snooper tool, if the Microsoft Office Server 12 Resource Kit Tools are installed on the computer. Otherwise, logs can also be analyzed by using a text editor, which is much less transparent and more complex than using the Snooper utility.

To View and Analyze Protocol Messages

In the Logging Tool, when you have ended the debug session, click Analyze Log Files to view the log files by using the Snooper tool. You can analyze protocol logs for the following components:

  - Lync Server SipStack (SIP)

  - Lync Server S4 (SIP)

  - Lync Server Conferencing signaling traffic (C3P), including MCU Infra C3P and Focus C3P

  - Lync Server Web conferencing traffic (PSOM)

  - Lync Server Unified Communications Client Platform client (UCCP)

  - Error reports from the archiving database

To help organize the performance of as-needed tasks, see As-Needed Operations Checklist.

<div>


> [!IMPORTANT]  
> For detailed administration and management procedures, see the Microsoft Lync Server 2013 Administration Guide.



</div>

<div>

## Backup (and restore) policies or configuration settings

Lync Server 2013 lets you back up and restore the whole system. Iif you want to back up (and then maybe someday restore) a single policy or a single collection of configuration settings, retrieve the appropriate policy, and then pipe that object to the Export-Clixml cmdlet, which saves the policy information as an XML file:

`Get-CsClientPolicy -Identity "RedmondClientPolicy" | Export-Clixml -Path C:\Backup\RedmondClientPolicy.xml`

You may now experiment with RedmondClientPolicy and change lots of the settings. If you decide instead to restore the old policy, enter:

`$x = Import-Clixml -Path C:\Backup\RedmondClientPolicy.xml`

`Set-CsClientPolicy -Instance $x`

Note that this approach will work for most policies and settings but it won't work with some of the more complex items—items that contain multiple sub-objects (like routing configuration settings, which contain many separate voice routes).

</div>

</div>

<span> </span>

</div>

</div>

</div>

