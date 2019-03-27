---
title: Move Lync Server 2010 Conference Directories to Lync Server 2013
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Move Conference Directories
ms:assetid: 659867e0-ce91-4a95-9787-b1c1566460a8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn727126(v=OCS.15)
ms:contentKeyID: 62387565
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Move Conference Directories

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-28_

Before decommissioning a pool you must perform the following procedure for each conference directory in your Lync Server 2010 pool.

<div>

## To Move a Conference Directory to Lync Server 2013

1.  Open the Lync Server Management Shell.

2.  To obtain the identity of the conference directories in your organization, run the following command:
    
        Get-CsConferenceDirectory
    
    The preceding command returns all the conference directories in your organization. Because of that, you might want to limit the results to the pool being decommissioned. For example, if you are decommissioning the pool with the fully qualified domain name (FQDN) pool01.contoso.net, use this command to limit the returned data to conference directories from that pool:
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"}
    
    That command returns only the conference directories where the ServiceID property contains the FQDN pool01.contoso.net.

3.  To move conference directories, run the following command for each conference directory in the pool:
    
        Move-CsConferenceDirectory -Identity <Numeric identity of conference directory> -TargetPool <FQDN of pool where ownership is to be transitioned>
    
    For example, to move conference directory 3 use this command, specifying a Lync Server 2013 pool as the TargetPool:
    
        Move-CsConferenceDirectory -Identity 3 -TargetPool "pool02.contoso.net"
    
    If you want to move all the conference directories on a pool then use a command similar to the following:
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"} | Move-CsConferenceDirectory -TargetPool "pool02.contoso.net"

Please see the document "Uninstalling Microsoft Lync Server 2010 and Removing Server Roles" (which can be downloaded from [http://go.microsoft.com/fwlink/p/?linkId=246227](http://go.microsoft.com/fwlink/p/?linkid=246227)) for comprehensive, step-by-step instructions on decommissioning Lync 2010 pools.

When moving conference directories you might encounter the following error:

    WARNING: Move operation failed for conference directory with ID "5". Cannot perform a rollback because data migration might have already started. Retry the operation.
    WARNING: Before using the -Force parameter, ensure that you have exported the conference directory data using DBImpExp.exe and imported the data on the target pool. Refer to the DBImpExp-Readme.htm file for more information.
    Move-CsConferenceDirectory : Unable to cast COM object of type 'System._ComObject' to interface type 'Microsoft.Rtc.Interop.User.IRtcConfDirManagement'. 
    This operation failed because the QueryInterface call on the COM component for the interface with SID '{4262B886-503F-4BEA-868C-04E8DF562CEB}' failed due to the following error: The specified module could not be found.

This error typically occurs when the Lync Server Management Shell requires an updated set of Active Directory permissions in order to complete a task. To resolve the problem, close the current instance of the Management Shell, then open a new instance of the shell and re-run the command in order to move the conference directory.

</div>

</div>

<span> </span>

</div>

</div>

</div>

