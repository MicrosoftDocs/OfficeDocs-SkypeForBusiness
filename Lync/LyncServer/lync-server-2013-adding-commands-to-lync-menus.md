---
title: 'Lync Server 2013: Adding commands to Lync menus'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Adding commands to Lync menus
ms:assetid: a8443bc2-e234-4022-870a-00700f38b1ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412788(v=OCS.15)
ms:contentKeyID: 48185091
ms.date: 04/11/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Adding commands to Lync menus in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-04-11_

You can add custom commands to Lync 2013 menus and pass the SIP Uniform Resource Identifier (URI) of the current user and selected contacts to the application that the custom command starts.

The custom commands that you add can appear on one or more of the following menus:

  - The Tools menu, on the menu bar in the Lync main window

  - The shortcut menu for contacts in the Contacts list

  - The More Options menu, in the Conversation window

  - The shortcut menu for people listed in the Conversation window participant list

  - The options menu in a contact card

You can define custom commands for two types of applications—applications that do either of the following:

  - Apply only to the current user and are started on the local computer.

  - Involve additional users, such as an online collaboration program, and must be started on each user's computer.

The custom command can be invoked in the following ways:

  - Select one or more users, and then choose the custom command.

  - Start a two-party or multiparty conversation, and then choose the custom command.

<div>

## To add a custom command

Use the registry settings in the following table to add a command to the menus. These entries are placed in the registry at one of the following locations:

  - For 32bit OS: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps

  - For 64bit OS: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps

### Custom Command Registry Entries

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Name</th>
<th>Type</th>
<th>Data</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Name</p></td>
<td><p>REG_SZ</p></td>
<td><p>Name of the application as it appears on the menu.</p></td>
</tr>
<tr class="even">
<td><p>ApplicationType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = Executable (default)</p>
<div>

> [!NOTE]  
> Requires ApplicationInstallPath.


</div>
<p>1 = Protocol</p></td>
</tr>
<tr class="odd">
<td><p>ApplicationInstallPath</p></td>
<td><p>REG_SZ</p></td>
<td><p>Full path of the executable.</p>
<div>

> [!NOTE]  
> Must be specified if ApplicationType is 0 (Executable).


</div></td>
</tr>
<tr class="even">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>Full path to be started along with any parameters, including the default parameters <em>%user-id%</em> and <em>%contact-id%</em>.</p></td>
</tr>
<tr class="odd">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = Local session. The application is started on the local computer.</p>
<p>1 = Two-party session (default). Lync 2013 starts the application locally and then sends a desktop notification to the other user. The other user clicks the notification to start the application on their computer.</p>
<p>2 = Multiparty session. Lync 2013 starts the application locally and then sends desktop notifications to the other users. The other user clicks the notification to start the specified application on their computer.</p></td>
</tr>
<tr class="even">
<td><p>ExtensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>A list of the menus where this command will appear, separated by semicolons. Possible values are:</p>
<p>MainWindowActions</p>
<p>MainWindowRightClick</p>
<p>ConversationWindowActions</p>
<p>ConversationWindowRightClick</p>
<p>ContactCardMenu</p>
<p>If ExtensibleMenu is not defined, the default values of MainWindowRightClick and ConversationWindowActions are used.</p></td>
</tr>
</tbody>
</table>


For example, the following Registry Editor (.REG) file shows the results of adding a Contoso Sales Contact Manager menu item to Actions menu in the Conversation window:

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Office\15.0\Lync\SessionManager\Apps\{1F9F07C6-7E0B-462B-AAD7-98C6DBEA8F69}]
    "Name"="Contoso Sales Contact Manager"
    "HelpMessage"="The Contoso Sales Contact Manager is not installed. Contact the Help Desk for more information."
    "ApplicationType"=dword:00000000
    "ApplicationInstallPath"="C:\\cscm.exe"
    "Path"="C:\\cscm.exe %user-id% %contact-id%"
    "SessionType"=dword:00000001
    "ExtensibleMenu"="ConversationWindowActions;MainWindowRightClick"

</div>

<div>

## To access a custom command

To access a custom command after it is added, do one of the following, depending on the ExtensibleMenu values that you define:

  - **MainWindowActions**   In the Lync main window, click **Tools**, and then click your custom command.

  - **MainWindowRightClick**   In the Lync main window, right-click a contact, and then click your custom command.

  - **ConversationWindowActions**   In the Conversation window, click the **More Options** icon, and then click your custom command.

  - **ConversationWindowRightClick**   In the Conversation window, right-click a contact name, and then click your custom command.

</div>

</div>

<span> </span>

</div>

</div>

</div>

