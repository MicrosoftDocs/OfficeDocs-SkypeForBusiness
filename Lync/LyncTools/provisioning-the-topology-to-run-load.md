---
title: Provisioning the Topology to Run Load
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Provisioning the Topology to Run Load
ms:assetid: 6fba03df-3914-4d2a-8208-e252ad993aff
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945598(v=OCS.15)
ms:contentKeyID: 51541424
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Provisioning the Topology to Run Load

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-04_

<div>

## Provisioning the Topology to Run Load

Depending on your existing settings and configuration of Lync Server 2013, you may need to make the following changes in your environment:

1.  Set the Windows PowerShell execution policy to Unrestricted. To check your execution policy settings, open the Lync Server Management Shell and run the following command:

    ``` powershell
        Get-ExecutionPolicy
    ```        

    If this command does not return the value Unrestricted, run this command:

    ``` powershell
        Set-ExecutionPolicy -Unrestricted
    ```

2.  To effectively configure Lync Server 2013, you will need to:
    
      - Be familiar with Lync Server 2013 topology (for example, computer names, service instances, site names, and policies).
    
      - Assign some of the users that were created to groups, such as Response Group hunt groups (for example, SIP URIs).

3.  To run the script from the command line, you may use:

    ``` powershell
        Powershell.exe -file <path to the file>
    ```
    
4.  Typically, after one of the scripts in this package runs, the resulting traces from the script will be stored in a file in the same path from which the script was invoked, named \<scriptname\>$h$m$s.txt. For example, running ArchivingPolicy.ps1 at 12:15 P.M. will generate a log file such as ArchivingPolicy121500.txt.

5.  Finally, note that although we have provided examples to configure the server, you are responsible for modifying or deleting the configuration after you have finished running the load.

</div>

</div>

<span> </span>

</div>

</div>

</div>

