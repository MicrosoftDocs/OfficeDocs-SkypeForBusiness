---
title: 'Lync Server 2013: Configuring a watcher node to use credential authentication'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring a watcher node to use credential authentication
ms:assetid: 032e33f3-9483-42e6-a33c-347eb6779597
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204632(v=OCS.15)
ms:contentKeyID: 48183255
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring a watcher node to use credential authentication in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-20_

If your watcher node computer lies outside the perimeter network, then you must follow a slightly different procedure in order to configure that watcher node to run synthetic transactions. Specifically, you should not create a trusted application pool and a trusted application, and you must install a certificate that enables the watcher node to send alerts to a computer inside the perimeter network. This means that you will need to complete two separate tasks:

  - Update the membership in the computer's RTC Local Read-only Administrators Group

  - Install the watcher node configuration files

<div>

## Updating Membership in the RTC Local Read-Only Administrators Group

If your watcher node lies outside the perimeter network, you must add the Network Service account to the RTC Local Read-only Administrators group on the watcher node computer. To do this, complete the following procedure on the watcher node:

1.  Click **Start**, right-click **Computer**, and then click **Manage**.

2.  In Server Manager, expand **Configuration**, expand **Local Users and Groups**, and then click **Groups**.

3.  In the Groups pane, double-click **RTC Local Read-only Administrators**.

4.  In the **RTC Local Read-only Administrators Properties** dialog box, click **Add**.

5.  In the **Select Users, Computers, Service Accounts, or Groups** dialog box, click **Locations**.

6.  In the **Locations** dialog box, select the name of the watcher node computer, and then click **OK**.

7.  In the **Enter object names to select** box, type **Network Service**, and then click **OK**.

8.  In the **RTC Local Read-only Administrators Properties** dialog box, click **OK**, and then close **Server Manager**.

Restart the watcher node computer.

</div>

<div>

## Installing the Watcher Node Configuration Files

After the watcher node computer has restarted, your next step is to run the file Watchernode.msi. To run this file, open the Lync Server 2013 Management Shell by clicking **Start**, clicking **All Programs**, clicking **Lync Server 2013**, and then clicking **Lync Server Management Shell**. In the Lync Server Management Shell, type the following command and then press ENTER (be sure and specify the actual path to your copy of Watchernode.msi):

    C:\Tools\Watchernode.msi Authentication=Negotiate

<div>


> [!NOTE]  
> As noted previously, Watchernode.msi can also be run from a command window. To open a command window, click <STRONG>Start</STRONG>, right-click <STRONG>Command Prompt</STRONG>, and then click <STRONG>Run as administrator</STRONG>. When the command window opens, type the same command as shown earlier.



</div>

The Negotiate mode is used any time the watcher node cannot be set up as a trusted application pool. In this mode, administrators will need to manage test user passwords on the watcher node.

</div>

</div>

<span> </span>

</div>

</div>

</div>

