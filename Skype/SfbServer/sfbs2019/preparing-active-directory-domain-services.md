---
title: "Preparing Active Directory Domain Services in Lync Server 2013"
ms.author: heidip
author: microsoftheidi
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b0d9aa4-f1ab-4578-b22f-b802b6ed1530
description: "In this articleActive Directory Preparation PrerequisitesAdministrator Rights and RolesActive Directory Preparation CmdletsLocked Down Active Directory RequirementsCustom Container PermissionsUsing Cmdlets and Ldifde.exeIn This Section"
---

# Preparing Active Directory Domain Services in Lync Server 2013
[]
 **In this article**
  
[Active Directory Preparation Prerequisites](#sectionSection0)
  
[Administrator Rights and Roles](#sectionSection1)
  
[Active Directory Preparation Cmdlets](#sectionSection2)
  
[Locked Down Active Directory Requirements](#sectionSection3)
  
[Custom Container Permissions](#sectionSection4)
  
[Using Cmdlets and Ldifde.exe](#sectionSection5)
  
[In This Section](#sectionSection6)
  
In Lync Server 2013, you can use the Lync Server Deployment Wizard to prepare Active Directory Domain Services, or you can use Lync Server Management Shell cmdlets directly. You can also use the ldifde.exe command line tool directly on your domain controllers, as described later in this topic.
  
The Lync Server Deployment Wizard guides you through each Active Directory preparation task. The Deployment Wizard runs Lync Server Management Shell cmdlets. This tool is useful for environments with a single domain and single forest topology, or other similar topology. 
  
> [!IMPORTANT]
> You can deploy Lync Server in a forest or domain where domain controllers run 32-bit versions of some operating systems (for details, see [Active Directory infrastructure requirements for Lync Server 2013](active-directory-infrastructure-requirements.md)). However, you cannot use the Lync Server Deployment Wizard to run schema, forest, and domain preparation in these environments because the Deployment Wizard and supporting files are 64-bit only. Instead, you can use ldifde.exe and the associated .ldf files on a 32-bit domain controller to prepare the schema, forest and domain. See the section "Using Cmdlets and Ldifde.exe" later in this topic. 
  
You can use Lync Server Management Shell cmdlets to run tasks remotely or for more complex environments.
  
## Active Directory Preparation Prerequisites
<a name="sectionSection0"> </a>

You must run Active Directory preparation steps on a computer running Windows Server 2012, Windows Server 2012 R2, or Windows Server 2008 R2 with SP1 (64-bit). Active Directory preparation requires Lync Server Management Shell and OCSCore.
  
The following components are required to run Active Directory preparation tasks:
  
- Lync Server Core components (OCScore.msi)
    
    > [!NOTE]
    > If you plan to use Lync Server Management Shell for Active Directory preparation, you must run the Lync Server Deployment Wizard first to install Core components. 
  
- Microsoft .NET Framework 4.5
    
    > [!NOTE]
    > For Windows Server 2012 and Windows Server 2012 R2, you install and activate .NET Framework 4.5 by using Server Manager. For details, see "Microsoft .NET Framework 4.5" in [Additional software requirements for Lync Server 2013](additional-software-requirements.md). For Windows Server 2008 R2, download and install [.Net Framework 4.5](https://www.microsoft.com/en-us/download/details.aspx?id=30653) from the Microsoft web site. 
  
- Remote Server Administration Tools (RSAT)
    
    > [!NOTE]
    > Some RSAT tools are required if you run Active Directory preparation steps on a member server rather than on a domain controller. Install the AD DS snap-ins and command-line tools and the Active Directory Module for Windows PowerShell from the AD DS and AD LDS Tools node in Server Manager. 
  
- Microsoft Visual C++ 11 Redistributable
    
    > [!NOTE]
    > Setup prompts you to install this prerequisite if it is not already installed on the computer. The package is supplied for you, and you will not have to acquire it separately. 
  
- Windows PowerShell 3.0 (64-bit)
    
    For Windows Server 2012 and Windows Server 2012 R2, Windows PowerShell 3.0 should be included with your Lync Server 2013 installation. For Windows Server 2008 R2, you need to install or upgrade to Windows PowerShell 3.0. For details, see [Installing Windows PowerShell 3.0 for Lync Server 2013](installing-windows-powershell-3-0.md)
    
## Administrator Rights and Roles
<a name="sectionSection1"> </a>

The following table shows the administrative rights and roles required for each Active Directory preparation task.
  
**User Rights Required for Active Directory Preparation**

|**Procedure**|**Rights or roles**|
|:-----|:-----|
|Schema preparation  <br/> |Member of Schema Admins group for the forest root domain and administrator rights on the schema master  <br/> |
|Forest preparation  <br/> |Member of Enterprise Admins group for the forest  <br/> |
|Domain preparation  <br/> |Member of Enterprise Admins or Domain Admins group for the specified domain  <br/> |
   
## Active Directory Preparation Cmdlets
<a name="sectionSection2"> </a>

The following table compares the Lync Server Management Shell cmdlets used to prepare AD DS to the LcsCmd commands used to prepare AD DS in Microsoft Office Communications Server 2007 R2.
  
**Cmdlets Compared to LcsCmd**

|**Cmdlets**|**LcsCmd**|
|:-----|:-----|
|Install-CsAdServerSchema  <br/> |Lcscmd /forest /action:SchemaPrep /SchemaType:Server  <br/> |
|Get-CsAdServerSchema  <br/> |Lcscmd /forest /action:CheckSchemaPrepState  <br/> |
|Enable-CsAdForest  <br/> |Lcscmd /forest /action:ForestPrep  <br/> |
|Disable-CsAdForest  <br/> |Lcscmd /forest /action:ForestUnprep  <br/> |
|Get-CsAdForest  <br/> |Lcscmd /forest /action:CheckForestPrepState  <br/> |
|Enable-CsAdDomain  <br/> |Lcscmd /domain /action:DomainPrep  <br/> |
|Disable-CsAdDomain  <br/> |Lcscmd /domain /action: DomainUnprep  <br/> |
|Get-CsAdDomain  <br/> |Lcscmd /domain /action:CheckDomainPrepState  <br/> |
   
## Locked Down Active Directory Requirements
<a name="sectionSection3"> </a>

If permissions inheritance is disabled or authenticated user permissions must be disabled in your organization, you must perform additional steps during domain preparation. For details, see [Preparing a locked-down Active Directory Domain Services in Lync Server 2013](preparing-a-locked-down-active-directory-domain-services.md).
  
## Custom Container Permissions
<a name="sectionSection4"> </a>

If your organization uses custom containers instead of the three built-in containers (that is, Users, Computers, and Domain Controllers), you must grant read access to the custom containers for the Authenticated Users group. Read access to the containers is required for domain preparation. For details, see [Preparing domains for Lync Server 2013](preparing-domains.md).
  
## Using Cmdlets and Ldifde.exe
<a name="sectionSection5"> </a>

The **Prepare Schema** step in the Lync Server Deployment Wizard and the **Install-CsAdServerSchema** cmdlet extend the Active Directory schema on domain controllers running a 64-bit operating system. If you need to extend the Active Directory schema on a domain controller running a 32-bit operating system, you can run the **Install-CsAdServerSchema** cmdlet remotely from a member server (recommended approach). If you need to run schema preparation directly on the domain controller, however, you can use the Ldifde.exe tool to import the schema files. The Ldifde.exe tool comes with most versions of the Windows operating system. 
  
If you use Ldifde.exe to import the schema files, you must import all four files, regardless of whether you are migrating from a previous version or performing a clean installation. You must import them in the following sequence:
  
1. ExternalSchema.ldf
    
2. ServerSchema.ldf
    
3. BackCompatSchema.ldf
    
4. VersionSchema.ldf
    
> [!NOTE]
> The four .ldf files are located in \Support\Schema directory of your installation media or download. 
  
To use Ldifde.exe to import the four schema files on a domain controller that is the schema master, use the following format:
  
```
ldifde -i -v -k -s <DCName> -f <Schema filename> -c DC=X <defaultNamingContext> -j logFilePath -b <administrator account> <logon domain> <password>
```

For example:
  
```
ldifde -i -v -k -s DC1 -f ServerSchema.ldf -c DC=X "DC=contoso,DC=com" -j C:\BatchImportLogFile -b Administrator contoso password
```

> [!NOTE]
> Use the b parameter only if you are logged in as a different user. For details about the required user rights, see the "Administrator Rights and Roles" section earlier in this topic. 
  
To use Ldifde.exe to import the four schema files on a domain controller that is not the schema master, use the following format:
  
```
ldifde -i -v -k -s <SchemaMasterFQDN> -f <Schema filename> -c DC=X <rootDomainNamingContext> -j logFilePath -b <administrator account> <domain> <password>
```

For details about using Ldifde, see Microsoft Knowledge Base article 237677, "Using LDIFDE to import and export directory objects to Active Directory," at [https://go.microsoft.com/fwlink/p/?linkId=132204](https://go.microsoft.com/fwlink/p/?linkId=132204).
  
## In This Section
<a name="sectionSection6"> </a>

- [Preparing the Active Directory schema in Lync Server 2013](preparing-the-active-directory-schema.md)
    
- [Preparing the forest for Lync Server 2013](preparing-the-forest.md)
    
- [Preparing domains for Lync Server 2013](preparing-domains.md)
    

