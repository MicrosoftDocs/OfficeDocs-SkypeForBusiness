---
title: 'Lync Server 2013: Response Group configuration permissions and prerequisites'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Response Group configuration permissions and prerequisites
ms:assetid: 4266f16a-b387-452c-a8ca-d771a3c58f0f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204840(v=OCS.15)
ms:contentKeyID: 48183972
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Response Group configuration permissions and prerequisites in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Response Group is an Enterprise Voice call management feature. This topic describes what you need to have in place before you can configure Response Group and the administrative credentials and permissions you need to perform configuration tasks.

This section assumes that you have read the planning documentation related to Response Group. For details, see [Planning for call management features in Lync Server 2013](lync-server-2013-planning-for-call-management-features.md) in the Planning documentation.

<div>

## Configuration Tools and Administrative Roles

You can use the following administrative tools to configure Response Group:

  - Lync Server Control Panel

  - Response Group Configuration Tool

  - Lync Server Management Shell

To configure response groups, you must be a member of at least one of the following administrative roles:


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Active Directory Security Group (1)</strong></p></td>
<td><p>Create Workflow</p></td>
<td><p>Assign Manager</p></td>
<td><p>Create /assign agents, queues</p></td>
<td><p>Create / manage holiday and business hours</p></td>
<td><p>Activate / deactivate workflow</p></td>
<td><p>Configure workflow (IVR or Hunt Group)</p></td>
</tr>
<tr class="even">
<td><p><strong>CsResponseGroupAdministrator</strong></p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
</tr>
<tr class="odd">
<td><p><strong>CsResponseGroupManager</strong></p></td>
<td> </td>
<td><p>√(2)</p></td>
<td><p>√(3)</p></td>
<td><p>√(3)</p></td>
<td><p>√(3)</p></td>
<td><p>√(3)</p></td>
</tr>
<tr class="even">
<td><p><strong>CsVoiceAdministrator</strong></p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
</tr>
<tr class="odd">
<td><p><strong>CsServerAdministrator</strong></p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
</tr>
<tr class="even">
<td><p><strong>CsAdministrator</strong></p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
<td><p>√</p></td>
</tr>
<tr class="odd">
<td><p><strong>CsViewOnlyAdministrator</strong></p></td>
<td><p>√(4)</p></td>
<td><p>√(4)</p></td>
<td><p>√(4)</p></td>
<td><p>√(4)</p></td>
<td><p>√(4)</p></td>
<td><p>√(4)</p></td>
</tr>
</tbody>
</table>


<div>


> [!NOTE]  
> <STRONG>(1)</STRONG> An Active Directory Domain Services user object must be a member of the specified Active Directory security group listed. An administrator or other delegated Active Directory group member with appropriate permissions to add users to a security group (For example, Administrator, Account Operators) must add a user object to the listed security group or group for the user to be able to perform the functions listed. <STRONG>(2)</STRONG> Only for workflows that the CsResponseGroupAdministrator has assigned to the CsResponseGroupManager. <STRONG>(3)</STRONG> A Response Group Manager can assign another member of CsResponseGroupManager to a workflow that the current manager already manages. <STRONG>(4)</STRONG> CsViewOnlyAdministrator can only run verb "Get" Lync Server Management Shell cmdlets.



</div>

</div>

<div>

## Response Group Configuration Prerequisites

Response Group requires the following components:

  - Application service

  - Response Group application

  - Language packs

  - File store (to hold audio files)

  - Web Services (includes the Response Group Configuration Tool and the agents' sign-in and sign-out console)

All of these components are installed by default when you deploy Enterprise Voice.

You might need to perform the following tasks before configuring Response Group:

  - Enable users for Lync Server 2013 and Enterprise Voice.

  - Modify a configuration file to be compliant with Federal Information Processing Standards (FIPS).

  - Modify the database collation to support Yi, Meng, and Zang characters for queue names and agent group names.

<div>

## Enabling Users

The first step in configuring Response Group is to create agent groups. Before you can create an agent group, you must enable the users who will be agents for Response Group for Lync Server 2013 and Enterprise Voice. Enabling users for Lync Server 2013 is typically a step in the Enterprise Edition server or Standard Edition server deployment. For details about enabling users for Lync Server 2013, see [Disable or re-enable user account for Lync Server 2013](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md). Enabling users for Enterprise Voice is typically a step in the Enterprise Voice deployment. For details, see [Enable users for Enterprise Voice in Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md).

</div>

<div>

## Complying with FIPS requirements

This section applies to you only if your organization needs to comply with Federal Information Processing Standards (FIPS).

To be compliant with FIPS, you need to modify the application-level Web.config file to use a different cryptography algorithm after you install Web Services. You need to specify that ASP.NET use the Triple Data Encryption Standard (3DES) algorithm to process view state data. For the Response Group application, this requirement applies to the Response Group Configuration Tool and the agent sign-in and sign-out console. For details about this requirement, see Microsoft Knowledge Base article 911722, "You may receive an error message when you access ASP.NET webpages that have ViewState enabled after you upgrade from ASP.NET 1.1 to ASP.NET 2.0," at [http://go.microsoft.com/fwlink/p/?linkId=196183](http://go.microsoft.com/fwlink/p/?linkid=196183).

To modify the Web.config file, do the following:

1.  In a text editor such as Notepad, open the application-level Web.config file.

2.  In the Web.config file, locate the `<system.web>` section.

3.  Add the following `<machineKey>` section to in the `<system.web>` section:
    
        <machineKey validationKey="AutoGenerate,IsolateApps" decryptionKey="AutoGenerate,IsolateApps" validation="3DES" decryption="3DES"/>

4.  Save the Web.config file.

5.  Restart the Internet Information Services (IIS) service by running the following command at a command prompt:
    
        iisreset

</div>

<div>

## Supporting Yi, Meng, and Zang Characters

This section applies to you only if your organization needs to support Yi, Meng, or Zang characters.

<div>


> [!NOTE]  
> For information on what the Yi, Meng, and Zang characters are and why they may be important to your deployment, see the information on the GB18030 character sets <A href="http://go.microsoft.com/fwlink/p/?linkid=240223">http://go.microsoft.com/fwlink/p/?linkId=240223</A>.



</div>

To support Yi, Meng, or Zang characters, you need to modify the collation for the Rgsconfig database. Change the collation of the **Name** column in the following tables in each Rgsconfig database:

  - dbo.AgentGroups

  - dbo.BusinessHours

  - dbo.HolidaySets

  - dbo.Queues

  - dbo.Workflows

For SQL Server 2008 R2 and SQL Server 2012, use the Latin\_General\_100 (Accent Sensitive) collation. If you use this collation, all object names are not case-sensitive.

You can change the collation by using Microsoft SQL Server Management Studio. For details about using this tool, see "Using SQL Server Management Studio" at [http://go.microsoft.com/fwlink/p/?linkId=196184](http://go.microsoft.com/fwlink/p/?linkid=196184). Follow these steps to change the collation:

1.  Be sure that SQL Server Management Studio is configured to allow changes that require tables to be recreated. For details, see "Save (Not Permitted) Dialog Box" at [http://go.microsoft.com/fwlink/p/?linkId=196186](http://go.microsoft.com/fwlink/p/?linkid=196186). For details about setting a column collation, see "How to: Set Column Collation (Visual Database Tools)" at [http://go.microsoft.com/fwlink/p/?linkId=196185](http://go.microsoft.com/fwlink/p/?linkid=196185).

2.  Using Microsoft SQL Server Management Studio, connect to the Rgsconfig database.

3.  Find the table you want to change in the Rgsconfig database, right-click the table, and click **Design**.

4.  Change the collation of the **Name** column and save the table.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

