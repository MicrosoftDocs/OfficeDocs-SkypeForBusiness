---
title: 'Lync Server 2013: Windows PowerShell and Lync Server management tools'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Windows PowerShell and Lync Server 2013 management tools
ms:assetid: 6a285f7c-0ef5-4cab-9976-d03be276e35d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn481130(v=OCS.15)
ms:contentKeyID: 59893869
ms.date: 07/20/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Windows PowerShell and Lync Server 2013 management tools

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-07-20_

In Microsoft Lync Server 2013, management tools are implemented using Windows PowerShell. Windows PowerShell includes a command-line environment, product-specific commands, and a full scripting language. Lync Server 2013 tools that are implemented using Windows PowerShell include the following:

  - **Topology Builder**. You use Topology Builder to create, adjust, and publish your planned topology, and it validates your topology before you begin server installations. When you install Lync Server 2013 on individual servers, the servers read the published topology as part of the installation process, and the installation program deploys the server as directed in the topology. After setup, configuration information is automatically replicated to all servers. Components can be added to your deployment only by using Topology Builder.

  - **Lync Server Management Shell**. You can use Lync Server Management Shell for full command-line management of your deployment.

  - **Lync Server Control Panel**. You can use the Microsoft Lync Server 2013 Control Panel user interface to manage the most common tasks in your deployment.

These tools use Windows PowerShell cmdlets for management of your deployment, including close to 550 product-specific cmdlets. The security cmdlets included in Lync Server 2013 are primarily used to manage authentication, and user rights and permissions. A wide variety of cmdlets are available for managing authentication, including cmdlets for certificate and personal identification number (PIN) authentication. In addition, a number of cmdlets enable you to use the new Role-Based Access Control (RBAC) feature to delegate administrative control of Lync Server 2013. For details about the Lync Server cmdlets, see [Lync Server 2013 Management Shell](lync-server-2013-lync-server-management-shell.md).

The script security features for Windows PowerShell are specifically designed to help prevent some of the scripting-related security problems of older technologies, including Microsoft Visual Basic Scripting Edition (VBScript). The Windows PowerShell security features are intended to create an environment in which users cannot easily or unknowingly run scripts. By default, Windows PowerShell security features are enabled. You can modify the state of those features to accommodate your scripting needs and a variety of security goals. This is not to say that the shell makes it impossible for users to run scripts. Rather, the shell makes it difficult—by default—for users to run scripts without realizing they are doing so. For details, see Windows PowerShell Script Security at [http://go.microsoft.com/fwlink/p/?LinkId=213145](http://go.microsoft.com/fwlink/p/?linkid=213145).

</div>

<span> </span>

</div>

</div>

</div>

