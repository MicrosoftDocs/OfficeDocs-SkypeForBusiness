---
title: 'Lync Server 2013:  Preparing Active Directory Domain Services'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Preparing Active Directory Domain Services
ms:assetid: 7b0d9aa4-f1ab-4578-b22f-b802b6ed1530
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398607(v=OCS.15)
ms:contentKeyID: 48184583
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Preparing Active Directory Domain Services in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-19_

In Lync Server 2013, you can use the Lync Server Deployment Wizard to prepare Active Directory Domain Services, or you can use Lync Server Management Shell cmdlets directly. You can also use the ldifde.exe command line tool directly on your domain controllers, as described later in this topic.

The Lync Server Deployment Wizard guides you through each Active Directory preparation task. The Deployment Wizard runs Lync Server Management Shell cmdlets. This tool is useful for environments with a single domain and single forest topology, or other similar topology.

<div>


> [!IMPORTANT]  
> You can deploy Lync Server in a forest or domain where domain controllers run 32-bit versions of some operating systems (for details, see <A href="lync-server-2013-active-directory-infrastructure-requirements.md">Active Directory infrastructure requirements for Lync Server 2013</A>). However, you cannot use the Lync Server Deployment Wizard to run schema, forest, and domain preparation in these environments because the Deployment Wizard and supporting files are 64-bit only. Instead, you can use ldifde.exe and the associated .ldf files on a 32-bit domain controller to prepare the schema, forest and domain. See the section “Using Cmdlets and Ldifde.exe” later in this topic.



</div>

You can use Lync Server Management Shell cmdlets to run tasks remotely or for more complex environments.

<div>

## Active Directory Preparation Prerequisites

You must run Active Directory preparation steps on a computer running Windows Server 2012, Windows Server 2012 R2, or Windows Server 2008 R2 with SP1 (64-bit). Active Directory preparation requires Lync Server Management Shell and OCSCore.

The following components are required to run Active Directory preparation tasks:

  - Lync Server Core components (OCScore.msi)
    
    <div>
    

    > [!NOTE]  
    > If you plan to use Lync Server Management Shell for Active Directory preparation, you must run the Lync Server Deployment Wizard first to install Core components.

    
    </div>

  - Microsoft .NET Framework 4.5
    
    <div>
    

    > [!NOTE]  
    > For Windows Server 2012 and Windows Server 2012 R2, you install and activate .NET Framework 4.5 by using Server Manager. For details, see "Microsoft .NET Framework 4.5" in <A href="lync-server-2013-additional-software-requirements.md">Additional software requirements for Lync Server 2013</A>. For Windows Server&nbsp;2008&nbsp;R2, download and install <A href="http://www.microsoft.com/en-us/download/details.aspx?id=30653">.Net Framework 4.5</A> from the Microsoft web site.

    
    </div>

  - Remote Server Administration Tools (RSAT)
    
    <div>
    

    > [!NOTE]  
    > Some RSAT tools are required if you run Active Directory preparation steps on a member server rather than on a domain controller. Install the AD DS snap-ins and command-line tools and the Active Directory Module for Windows PowerShell from the AD DS and AD LDS Tools node in Server Manager.

    
    </div>

  - Microsoft Visual C++ 11 Redistributable
    
    <div>
    

    > [!NOTE]  
    > Setup prompts you to install this prerequisite if it is not already installed on the computer. The package is supplied for you, and you will not have to acquire it separately.

    
    </div>

  - Windows PowerShell 3.0 (64-bit)
    
    For Windows Server 2012 and Windows Server 2012 R2, Windows PowerShell 3.0 should be included with your Lync Server 2013 installation. For Windows Server 2008 R2, you need to install or upgrade to Windows PowerShell 3.0. For details, see [Installing Windows PowerShell 3.0 for Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md)

</div>

<div>

## Administrator Rights and Roles

The following table shows the administrative rights and roles required for each Active Directory preparation task.

### User Rights Required for Active Directory Preparation

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Procedure</th>
<th>Rights or roles</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Schema preparation</p></td>
<td><p>Member of Schema Admins group for the forest root domain and administrator rights on the schema master</p></td>
</tr>
<tr class="even">
<td><p>Forest preparation</p></td>
<td><p>Member of Enterprise Admins group for the forest</p></td>
</tr>
<tr class="odd">
<td><p>Domain preparation</p></td>
<td><p>Member of Enterprise Admins or Domain Admins group for the specified domain</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Active Directory Preparation Cmdlets

The following table compares the Lync Server Management Shell cmdlets used to prepare AD DS to the LcsCmd commands used to prepare AD DS in Microsoft Office Communications Server 2007 R2.

### Cmdlets Compared to LcsCmd

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlets</th>
<th>LcsCmd</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Install-CsAdServerSchema</p></td>
<td><p>Lcscmd /forest /action:SchemaPrep /SchemaType:Server</p></td>
</tr>
<tr class="even">
<td><p>Get-CsAdServerSchema</p></td>
<td><p>Lcscmd /forest /action:CheckSchemaPrepState</p></td>
</tr>
<tr class="odd">
<td><p>Enable-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:ForestPrep</p></td>
</tr>
<tr class="even">
<td><p>Disable-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:ForestUnprep</p></td>
</tr>
<tr class="odd">
<td><p>Get-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:CheckForestPrepState</p></td>
</tr>
<tr class="even">
<td><p>Enable-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action:DomainPrep</p></td>
</tr>
<tr class="odd">
<td><p>Disable-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action: DomainUnprep</p></td>
</tr>
<tr class="even">
<td><p>Get-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action:CheckDomainPrepState</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Locked Down Active Directory Requirements

If permissions inheritance is disabled or authenticated user permissions must be disabled in your organization, you must perform additional steps during domain preparation. For details, see [Preparing a locked-down Active Directory Domain Services in Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md).

</div>

<div>

## Custom Container Permissions

If your organization uses custom containers instead of the three built-in containers (that is, Users, Computers, and Domain Controllers), you must grant read access to the custom containers for the Authenticated Users group. Read access to the containers is required for domain preparation. For details, see [Preparing domains for Lync Server 2013](lync-server-2013-preparing-domains.md).

</div>

<div>

## Using Cmdlets and Ldifde.exe

The **Prepare Schema** step in the Lync Server Deployment Wizard and the **Install-CsAdServerSchema** cmdlet extend the Active Directory schema on domain controllers running a 64-bit operating system. If you need to extend the Active Directory schema on a domain controller running a 32-bit operating system, you can run the **Install-CsAdServerSchema** cmdlet remotely from a member server (recommended approach). If you need to run schema preparation directly on the domain controller, however, you can use the Ldifde.exe tool to import the schema files. The Ldifde.exe tool comes with most versions of the Windows operating system.

If you use Ldifde.exe to import the schema files, you must import all four files, regardless of whether you are migrating from a previous version or performing a clean installation. You must import them in the following sequence:

1.  ExternalSchema.ldf

2.  ServerSchema.ldf

3.  BackCompatSchema.ldf

4.  VersionSchema.ldf

<div>


> [!NOTE]  
> The four .ldf files are located in \Support\Schema directory of your installation media or download.



</div>

To use Ldifde.exe to import the four schema files on a domain controller that is the schema master, use the following format:

    ldifde -i -v -k -s <DCName> -f <Schema filename> -c DC=X <defaultNamingContext> -j logFilePath -b <administrator account> <logon domain> <password>

For example:

    ldifde -i -v -k -s DC1 -f ServerSchema.ldf -c DC=X "DC=contoso,DC=com" -j C:\BatchImportLogFile -b Administrator contoso password

<div>


> [!NOTE]  
> Use the b parameter only if you are logged in as a different user. For details about the required user rights, see the "Administrator Rights and Roles" section earlier in this topic.



</div>

To use Ldifde.exe to import the four schema files on a domain controller that is not the schema master, use the following format:

    ldifde -i -v -k -s <SchemaMasterFQDN> -f <Schema filename> -c DC=X <rootDomainNamingContext> -j logFilePath -b <administrator account> <domain> <password>

For details about using Ldifde, see Microsoft Knowledge Base article 237677, "Using LDIFDE to import and export directory objects to Active Directory," at [http://go.microsoft.com/fwlink/p/?linkId=132204](http://go.microsoft.com/fwlink/p/?linkid=132204).

</div>

<div>

## In This Section

  - [Preparing the Active Directory schema in Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)

  - [Preparing the forest for Lync Server 2013](lync-server-2013-preparing-the-forest.md)

  - [Preparing domains for Lync Server 2013](lync-server-2013-preparing-domains.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

