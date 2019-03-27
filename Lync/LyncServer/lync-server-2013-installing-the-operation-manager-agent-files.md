---
title: 'Lync Server 2013: Installing the Operation Manager agent files'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Installing the Operation Manager agent files
ms:assetid: e2246c44-0c75-43fc-8b04-26e53c5dd572
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205345(v=OCS.15)
ms:contentKeyID: 48185692
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Installing the Operation Manager agent files in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-20_

To install the Operations Manager agent files on the computer, complete the following steps.

1.  On your System Center setup media, double-click **SetupOM.exe**.

2.  In System Center Operation Manager setup, click **Install Operations Manager Agent**.

3.  In System Center Setup wizard, on the **Welcome to the System Center Operations Manager Setup** wizard page, click **Next**.

4.  On the **Destination Folder** page, select the folder where the Operations Manager Agent files will be installed, and then click **Next**.

5.  On the **Management Group Configuration** page, select **Specify Management Group information**, and then click **Next**.

6.  On the **Management Group Configuration** page, type the name of your Operations Manager Management Group in the **Management Group Name** box, and then type the host name of your Operations Manager server (for example, atl-scom-001) in the **Management Server** box. If you have changed the port number used by Operations Manager, then type the new port number in the Management Server Port box. Otherwise, leave the port at the default value of 5723 and click **Next**.

7.  On the **Agent Action Account** page, select **Local System**, and then click **Next**.

8.  On the **Microsoft Update** page, select **I don't want to use Microsoft Update**, and then click **Next**.

9.  On the **Ready to Install** page, click **Install**.

10. On the **Completing the System Center Operations Manager Setup wizard** page, click **Finish**.

11. Click **Exit**.

If you are using System Center 2007 R2, you can verify that the agent has been created by clicking **Start**, clicking **All Programs**, clicking **System Center Operations Manager 2007 R2**, and then clicking **Operations Manager Shell**. In the Operations Manager Shell, type the following Windows PowerShell command, and then press ENTER:

    Get-Agent 

A list of all your Operations Manager agents will appear onscreen.

If you are using System Center 2012, run this command from the Operations 2012 Manager Shell:

    Get-SCOMAgent

</div>

<span> </span>

</div>

</div>

</div>

