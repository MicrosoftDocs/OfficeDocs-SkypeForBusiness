---
title: 'Lync Server 2013: Using Config.xml to perform installation tasks'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Using Config.xml to perform installation tasks
ms:assetid: 0813184a-ab40-417c-b3a3-c2090766b831
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204651(v=OCS.15)
ms:contentKeyID: 48183332
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using Config.xml to perform installation tasks in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-02_

Although the Office Customization Tool (OCT) is the primary tool for customization installation, administrators can use the Config.xml file to specify additional installation instructions that are not available in the OCT. The following customizations can only be made by using the Config.xml file:

  - Specify the path of the network installation point.

  - Select the products to install.

  - Configure logging and the location of the Setup customization file and software updates.

  - Specify installation options, such as user name.

  - Copy the local installation source (LIS) to the user's computer without installing Office.

  - Add or remove languages from the installation.

We recommend that you use the Config.xml file to configure Lync 2013 silent installation.

By default, the Config.xml file that is stored in the core product folder (for example, \\product.WW) directs Setup to install that product. For example, the Config.xml file in the following folder installs Lync 2013:

  - \\\\server\\share\\Lync15\\Lync.WW \\Config.xml

The Config.xml elements most commonly used for Lync 2013 installation are listed in the following table.

### Config.xml elements

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuration</p></td>
<td><p>Top-level element (required). Contains the Product attribute, for example: Product=Lync</p></td>
</tr>
<tr class="even">
<td><p>OptionState</p></td>
<td><p>Specifies how specific product features are handled during installation. Use the following attributes to prevent installation of Business Connectivity Services, which includes shared components that interfere with Outlook 2010:</p>
<ul>
<li><p>Id=&quot;LOBiMain&quot;</p></li>
<li><p>State=&quot;Absent&quot;</p></li>
<li><p>Children=&quot;Force&quot;</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Display</p></td>
<td><p>The level of UI that Setup displays to the user. Typical attributes include the following:</p>
<ul>
<li><p>CompletionNotice=&quot;Yes&quot; | &quot;No&quot;(default)</p></li>
<li><p>AcceptEula=&quot;Yes&quot; | &quot;No&quot;(default)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Logging</p></td>
<td><p>Options for the kind of logging that Setup performs. Typical attributes include the following:</p>
<ul>
<li><p>Type =&quot;Off&quot; | &quot;Standard&quot;(default) | &quot;Verbose&quot;</p></li>
<li><p>Template=”filename.txt” (the name of the log file)</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Setting</p></td>
<td><p>Specifies values for Windows Installer properties. Typical attributes include the following:</p>
<ul>
<li><p>Setting Id=&quot;name&quot; (the name of the Windows Installer property)</p></li>
<li><p>Value=&quot;value&quot; (the value to assign to the property)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>DistributionPoint</p></td>
<td><p>The fully qualified path of the network installation point from which the installation is to run. Includes the Location attribute:</p>
<ul>
<li><p>Location=”path”</p></li>
</ul></td>
</tr>
</tbody>
</table>


The following example shows a Config.xml file for a typical silent installation of Lync 2013.

    <Configuration Product="Lync">
      <OptionState Id="LOBiMain" State="Absent" Children="Force" />
      <Display Level="None" CompletionNotice="No" AcceptEula="Yes" />
      <Logging Type="verbose" Path="%temp%" Template="LyncSetupVerbose(*).log" />
      <Setting Id="SETUP_REBOOT" Value="Never" />
      <DistributionPoint Location="\\server\share\Lync15" />
    </Configuration>

Detailed information about using the Config.xml file to perform Office installation and maintenance tasks is available at <http://go.microsoft.com/fwlink/p/?linkid=267514>.

<div>

## To customize the Config.xml file

1.  Open the Config.xml file by using a text editor tool, such as Notepad.

2.  Locate the lines that contain the elements you want to change.

3.  Modify the element entry with the silent options that you want to use. Make sure that you remove the comment delimiters, "\<\!--" and "--\>". For example, use the following syntax:
    
        < DistributionPoint Location="\\server\share\Lync15" />

4.  Save the Config.xml file.

</div>

</div>

<span> </span>

</div>

</div>

</div>

