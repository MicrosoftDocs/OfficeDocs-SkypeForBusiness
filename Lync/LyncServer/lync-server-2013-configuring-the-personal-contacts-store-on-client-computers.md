---
title: 'Lync Server 2013: Configuring the personal contacts store on client computers'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring the personal contacts store on client computers
ms:assetid: ec69a6cb-07f2-4057-9544-55035f83eeae
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ721922(v=OCS.15)
ms:contentKeyID: 49733857
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring the personal contacts store on client computers for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

If you are integrating Microsoft Lync Server 2013 and Microsoft Exchange Server 2013 then it is recommended that you configure the personal contact store on any client computers running Microsoft Lync 2010. In particular, you should configure Lync to use Exchange as the personal contact store, and, at the same time, ensure that users are not able to override that decision. This can be done by creating and configuring a Registry value on each client computer.

Note that this is not required on computers running Lync 2013.

To configure this value on a single computer, complete the following procedure:

1.  On the client computer, click **Start** and then click **Run**.

2.  In the **Run** dialog box, type regedit and then press ENTER.

3.  In Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **Software**, expand **Policies**, expand **Microsoft**, and then expand **Communicator**.

4.  Right-click **Communicator**, point to **New**, and then click **DWORD (32-bit) Value**.

5.  After the new value is created, type **PersonalContactStoreOverride** and then press ENTER to rename the value.

6.  Verify that the value of PersonalContactStoreOverride is set to 0 and then close Registry Editor.

If you need to make this same change on multiple computers you can do so by creating a custom Group Policy object. For details, see the Group Policy documentation at [http://go.microsoft.com/fwlink/p/?LinkId=268543](http://go.microsoft.com/fwlink/p/?linkid=268543).

</div>

<span> </span>

</div>

</div>

</div>

