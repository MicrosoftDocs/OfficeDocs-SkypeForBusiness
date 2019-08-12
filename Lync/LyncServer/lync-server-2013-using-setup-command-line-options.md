---
title: 'Lync Server 2013: Using Setup command-line options'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Using Setup command-line options
ms:assetid: 99878c3c-ff31-48e2-8424-580d7b07a7bf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205129(v=OCS.15)
ms:contentKeyID: 48184957
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Setup command-line options in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

The Setup.exe command line is used for very few operations in Office setup. Instead of using the Setup command-line options, you’ll typically use the Office Customization Tool and the Config.xml file for product setup and feature customization.

The Office Setup.exe command line recognizes the command-line options described in the following table.

### Office Setup Command-Line Options

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Setup Command-Line Option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>/admin</p></td>
<td><p>Runs the Office Customization Tool to create a Setup customization file (.msp file).</p></td>
</tr>
<tr class="even">
<td><p>/adminfile [path]</p></td>
<td><p>Applies the specified Setup customization file to the installation. You can specify a path of a specific customization file (.msp file) or to the folder where you store customization files.</p></td>
</tr>
<tr class="odd">
<td><p>/config [path]</p></td>
<td><p>Specifies the Config.xml file that Setup uses during the installation. Use the /config option to specify the Config.xml file you customized for Lync 2013 installations, for example: <code>/config \\server\share\Lync15\Lync.WW\Config.xml</code></p></td>
</tr>
<tr class="even">
<td><p>/modify Lync</p></td>
<td><p>Used with a modified Config.xml file to run Setup in maintenance mode and make changes to an existing Office installation. For example, you can use the /modify option to add or remove Lync features.</p></td>
</tr>
<tr class="odd">
<td><p>/repair Lync</p></td>
<td><p>Runs Setup from the user’s computer to repair Lync.</p></td>
</tr>
<tr class="even">
<td><p>/uninstall Lync</p></td>
<td><p>Runs Setup to remove Lync from the user’s computer.</p></td>
</tr>
</tbody>
</table>


For details about using the setup command-line options, see <http://go.microsoft.com/fwlink/p/?linkid=267515>.

</div>

<span> </span>

</div>

</div>

</div>

