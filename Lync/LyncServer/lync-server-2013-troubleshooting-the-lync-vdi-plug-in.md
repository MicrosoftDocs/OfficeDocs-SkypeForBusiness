---
title: 'Lync Server 2013: Troubleshooting the Lync VDI plug-in'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Troubleshooting the Lync VDI plug-in
ms:assetid: 183c9449-b907-409c-b5ed-b02af3bd93ee
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204713(v=OCS.15)
ms:contentKeyID: 48183525
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Troubleshooting the Lync VDI plug-in in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-10_

<div>

## Troubleshooting Issues with Installing the Lync VDI Plug-in on a Thin Client

If there are issues with installing the VDI plug-in on a thin client, check the following:

  - Ensure that there is sufficient space in the folder that you specified in the TEMP and TMP system variables.

  - Ensure that write-protect is turned off. Refer to your device manufacturer’s documentation for instructions.

</div>

<div>

## Troubleshooting Issues with Pairing

When VDI plug-in pairing fails, the pairing icon in the lower right displays as a red “X” as shown:

![Lync VDI icon showing successful pairing](images/JJ204948.303d618c-4bc8-41c4-8553-2475de0d395e(OCS.15).png "Lync VDI icon showing successful pairing")

The following are possible reasons for failures and the corrective actions you can take.

  - **The user entered incorrect credentials during sign-in.**
    
    The user should sign out of Lync and sign in again with the correct credentials. The pairing dialog box will reappear and show whether pairing is successful.

  - **Another instance of the remote desktop client is running.**
    
    If they are using Remote Desktop Connection in Windows, users should do the following:
    
    1.  Start Task Manager: Press **Alt+Ctrl+Delete**, and then click **Start Task Manager**.
    
    2.  Click the **Processes** tab and look for all processes named **mstsc.exe** in the list.
    
    3.  Highlight each **mstsc.exe** process and then click **End Process**.
    
    4.  Start a new remote desktop session and try connecting again.

  - **The necessary files did not install correctly.**
    
    After the plug-in is installed on the local computer, the following files should be present under C:\\Program Files\\Microsoft Office\\Office15 (or the appropriate drive letter):
    
      - LyncVdiPlugin.dll
    
      - UcVdi.dll
    
    If there are any issues with VDI pairing, check to make sure that these files are present on the local computer.

  - **The Lync client is running on the local computer.**
    
    To use the Lync VDI plugin, a Lync client must not be running on the local computer, otherwise pairing will fail. As a best practice, the user should not install a Lync client on the local computer.

</div>

</div>

<span> </span>

</div>

</div>

</div>

