---
title: 'Lync Server 2013: Preparing the Active Directory schema'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Preparing the Active Directory schema
ms:assetid: 067726ae-fd3f-4133-a32f-26d2603ac674
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398119(v=OCS.15)
ms:contentKeyID: 48183300
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Preparing the Active Directory schema in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-27_

Before you begin preparing Active Directory Domain Services, you can open the schema files by using a text editor, such as Windows Notepad, or see [Active Directory schema extensions, classes, and attributes used by Lync Server 2013](lync-server-2013-active-directory-schema-extensions-classes-and-attributes-used-by-lync-server.md) to review all the Active Directory Domain Services schema extensions that will be modified for Lync Server 2013. Lync Server uses four schema files:

  - ExternalSchema.ldf, which is used for interoperability with Microsoft Exchange Server

  - ServerSchema.ldf, which is the primary Lync Server 2013 schema file

  - BackCompatSchema.ldf, which is used for interoperability with any components from prior releases

  - VersionSchema.ldf, which is used for version information of the prepared schema

All .ldf files are installed during schema preparation, regardless of whether you are migrating from a previous release or performing a clean installation. These schema files are installed in the sequence shown in the preceding list and are located in the \\Support\\schema folder on the installation media.

The Lync Server schema extensions are replicated across all domains, which impacts network traffic. Run schema preparation at a time when network usage is low.

<div>


> [!NOTE]  
> If you need to add support for Microsoft® Office Communicator Mobile 2007 R2 for Java and Microsoft® Office Communicator Mobile for Nokia 1.0 mobile clients to your Lync Server 2013 deployment, you need to prepare the Active Directory schema for Microsoft Office Communications Server 2007 R2 during installation of Lync Server 2013. For the necessary software and documentation, see <A href="http://go.microsoft.com/fwlink/p/?linkid=207172">http://go.microsoft.com/fwlink/p/?linkId=207172</A>.



</div>

<div>

## ADSI Edit

Active Directory Service Interfaces Editor (ADSI Edit) is an AD DS administration tool that you can use to verify schema preparation and replication.

ADSI Edit is installed by default when you install the AD DS role to make a server a domain controller. For Windows Server 2008 and Windows Server 2008 R2, ADSI Edit (adsiedit.msc) is included with the Remote Server Administration Tools (RSAT). You can also install RSAT on domain member servers or stand-alone servers. The RSAT package is copied to these servers by default when you install Windows, but it is not installed by default. You install individual tools by using Server Manager. ADSI Edit is included under **Role Administration Tools**, **Active Directory Domain Services Tools**, **Active Directory Domain Controller Tools**.

For Windows Server 2003, ADSI Edit is included with the Support Tools. The Support Tools are available from the Windows Server 2003 CD in the \\SUPPORT\\TOOLS folder, or you can download them from “Windows Server 2003 Service Pack 2 32-bit Support Tools” at [http://go.microsoft.com/fwlink/p/?linkId=125770](http://go.microsoft.com/fwlink/p/?linkid=125770). Instructions for installing the Support Tools from the product CD are available from “Install Windows Support Tools” at [http://go.microsoft.com/fwlink/p/?linkId=125771](http://go.microsoft.com/fwlink/p/?linkid=125771). Adsiedit.dll is automatically registered when you install the support tools. If, however, you copied the files to your computer, you must run the **regsvr32** command to register the adsiedit.dll file before you can run the tool.

</div>

<div>

## In This Section

  - [Running Active Directory schema preparation in Lync Server 2013](lync-server-2013-running-schema-preparation.md)

  - [Verifying Active Directory schema replication in Lync Server 2013](lync-server-2013-verifying-schema-replication.md)

</div>

<div>

## See Also


[Preparing the forest for Lync Server 2013](lync-server-2013-preparing-the-forest.md)  
[Preparing domains for Lync Server 2013](lync-server-2013-preparing-domains.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

