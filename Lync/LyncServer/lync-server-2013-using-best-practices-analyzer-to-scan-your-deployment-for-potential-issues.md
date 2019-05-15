---
title: 'Using Best Practices Analyzer to scan your deployment for potential issues'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using Best Practices Analyzer to scan your deployment for potential issues
ms:assetid: 09c84509-dc91-4e7b-882b-3c467b6b026d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg591343(v=OCS.15)
ms:contentKeyID: 48183359
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Best Practices Analyzer to scan your Lync Server 2013 deployment for potential issues

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-21_

To run a Best Practices Analyzer scan, you must specify the following:

  - **Credentials**   To run a scan, you must log on to a computer on which Best Practices Analyzer is installed by using an account that is a member of the local Administrators group. Additionally, you need to log on by using a user account that has the user rights and permissions required to run the appropriate scans, or you must specify credentials that have the appropriate user rights and permissions when you run Best Practices Analyzer. For details, see [Group memberships and user rights requirements for Best Practices Analyzer in Lync Server 2013](lync-server-2013-group-memberships-and-user-rights-requirements-for-best-practices-analyzer.md).

  - **Scope of scan**   To specify the scope of the scan, select the categories and servers that you want to scan. You can select all categories, one or more categories, or one or more servers within a specific category in your Lync Server environment.

  - **Type of scan**   Currently, the Health Check scan is the only type of scan available (selected by default). The Health Check scan generates a report that includes errors, warnings, and other information for all servers specified in the scope.

  - **Network speed**   Network speed options include Fast LAN (100 Mbps or more), LAN (10 Mbps), Fast WAN (1.5 Mbps), or WAN (64 kbps). The estimated time to complete the scan is based on this setting. This setting is also used to set the time-out period. During the scan, the Best Practices Analyzer waits for a response from a server for a specified time. If it does not receive a response within the specified time-out period, it moves to the next server in the scan. On slower networks, this specified time-out period is longer to account for longer network latencies. We recommend that you select the slowest link in your topology for this parameter so that the tool does not time out too quickly.

<div>

## To scan your Lync Server 2013 deployment

1.  Log on to a computer on which Best Practices Analyzer is installed by using an account that is a member of the local Administrators group, and has other required user rights and permissions.

2.  Click **Start**, point to **All Programs**, click **Microsoft Lync Server 2013**, and then click **Best Practices Analyzer**.

3.  On the **Welcome** screen, click **Select options for a new scan**.

4.  On the **Connect to Active Directory** page, verify the name specified in **Active Directory Server**, and then do one of the following:
    
      - To run a scan using the credentials that you used to log on to the computer, click **Connect to the Active Directory server**.
    
      - To specify different credentials that you want to use for Active Directory Domain Services, Edge Server, or Exchange Server, click **Show advanced logon options**, select each check box for which separate credentials are required, specify the credentials for each selected check box, and then click **Connect to the Active Directory server**.
    
    <div>
    

    > [!NOTE]
    > Before beginning the scan, Best Practices Analyzer performs a network and permissions check to ensure that the specified account credentials are valid and that Best Practices Analyzer can connect to Active Directory Domain Services. If the tool is running on a workgroup server, the tool also verifies that it can connect to Edge Servers in the perimeter network (that is, if they are included in the scan).

    
    </div>

5.  On the **Start a new Best Practices scan** page, select the options that you want to include in the scan, specify the network speed, and then click **Start scanning**.

6.  On the **Scanning Completed** page, click **View a report of this Best Practices scan**.

7.  On the **View Best Practices Report** page, do one of the following:
    
      - To view reports in a list organized by server component, click **List Reports**, and then click either the **All Issues** tab or the **Informational Items** tab.
    
      - To view reports as a hierarchical list organized by types of results, click **Tree Reports**, and then click either the **Detailed View** tab or the **Summary View** tab.
    
      - To view other reports, click **Other Reports**.
    
    <div>
    

    > [!NOTE]
    > For details about the Best Practices Analyzer reports and the issues they identify, see <A href="lync-server-2013-viewing-and-working-with-reports-created-by-best-practices-analyzer.md">Viewing and working with reports created by Best Practices Analyzer in Lync Server 2013</A> and <A href="lync-server-2013-analyzing-and-resolving-issues-identified-by-best-practices-analyzer.md">Analyzing and resolving issues identified by Best Practices Analyzer in Lync Server 2013</A>.

    
    </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

