---
title: 'Lync Server 2013: Testing database configuration'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Testing database configuration
ms:assetid: 60f7fcd2-5efe-4791-b159-b0f9bf39a41b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn727307(v=OCS.15)
ms:contentKeyID: 63969606
ms.date: 07/07/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Testing database configuration in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-07-07_


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Verification schedule</p></td>
<td><p>Daily</p></td>
</tr>
<tr class="even">
<td><p>Testing tool</p></td>
<td><p>Windows PowerShell</p></td>
</tr>
<tr class="odd">
<td><p>Permissions required</p></td>
<td><p>When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group, and need to have Administrator privileges on the SQL server.</p>
<p>When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the <strong>Test-CsDatabase</strong> cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:</p>
<pre><code>Get-CsAdminRole | Where-Object {$_.Cmdlets -match &quot;Test-CsDatabase&quot;}</code></pre></td>
</tr>
</tbody>
</table>


<div>

## Description

The **Test-CsDatabase** cmdlet verifies connectivity to one or more Lync Server 2013 databases. When run, the **Test-CsDatabase** cmdlet reads the Lync Server topology, attempts to connect to relevant databases, and then reports back the success or failure of each try. If a connection can be made, the cmdlet will also report back such information as the database name, SQL Server version information, and the location of any installed mirror databases.

</div>

<div>

## Running the test

The command shown in Example 1 verifies the configuration of the Central Management database.

    Test-CsDatabase -CentralManagementDatabase

Example 2 verifies all the Lync Server databases installed on the computer atl-sql-001.litwareinc.com.

    Test-CsDatabase -ConfiguredDatabases -SqlServerFqdn "atl-sql-001.litwareinc.com"

In Example 3, verification is performed only for the Archiving database installed on the computer atl-sql-001.litwareinc.com. Note that the SqlInstanceName parameter is included to specify the SQL Server instance (Archinst) where the Archiving database is located.

    Test-CsDatabase -DatabaseType "Archiving" -SqlServerFqdn "atl-sql-001.litwareinc.com" -SqlInstanceName "archinst"

The command shown in Example 4 verifies the databases installed on the local computer.

    Test-CsDatabase -LocalService

</div>

<div>

## Determining success or failure

If database connectivity is configured correctly, you'll receive output similar to this, with the Succeed property marked as **True**:

SqlServerFqdn : atl-sql-001.litwareinc.com

SqlInstanceName : rtc

MirrorSqlServerFqdn :

MirrorSqlInstanceName :

DatabaseName : xds

DataSource :

SQLServerVersion :

ExpectedVersion : 10.13.2

InstalledVersion :

Succeed : True

SqlServerFqdn : atl-sql-001.litwareinc.com

SqlInstanceName : rtc

MirrorSqlServerFqdn :

MirrorSqlInstanceName :

DatabaseName : lis

DataSource :

SQLServerVersion :

ExpectedVersion : 3.1.1

InstalledVersion :

Succeed : True

If the database is configured correctly but still available, the Succeed field will be shown as **False**, and additional warnings and information will be provided:

SqlServerFqdn : atl-sql-001.litwareinc.com

SqlInstanceName : rtc

MirrorSqlServerFqdn :

MirrorSqlInstanceName :

DatabaseName : xds

DataSource :

SQLServerVersion :

ExpectedVersion : 10.13.2

InstalledVersion :

Succeed : False

SqlServerFqdn : atl-cs-001.litwareinc.com

SqlInstanceName : rtc

MirrorSqlServerFqdn :

MirrorSqlInstanceName :

DatabaseName : lis

DataSource :

SQLServerVersion :

ExpectedVersion : 3.1.1

InstalledVersion :

Succeed : False

WARNING: Test-CsDatabase encountered errors. Consult the log file for a

detailed analysis, and to make sure that all errors (2) and warnings (0) are addressed

before continuing.

WARNING: Detailed results can be found at

"C:\\Users\\Testing\\AppData\\Local\\Temp\\2\\Test-CsDatabase-b18d488a-8044-4679-bbf2-

04d593cce8e6.html".

</div>

<div>

## Reasons why the test might have failed

Here are some common reasons why **Test-CsDatabase** might fail:

  - An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds.

  - This command will fail if the database is misconfigured or not yet deployed.

</div>

<div>

## See Also


[Get-CsDatabaseMirrorState](https://docs.microsoft.com/powershell/module/skype/Get-CsDatabaseMirrorState)  
[Get-CsService](https://docs.microsoft.com/powershell/module/skype/Get-CsService)  
[Get-CsUserDatabaseState](https://docs.microsoft.com/powershell/module/skype/Get-CsUserDatabaseState)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

