---
title: 'Lync Server 2013: Lync VDI plug-in prerequisites'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Lync VDI plug-in prerequisites
ms:assetid: da25a976-7624-4dfc-b332-9c4db4ee78da
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205304(v=OCS.15)
ms:contentKeyID: 48185552
ms.date: 03/07/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Lync VDI plug-in prerequisites in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-03-07_

In a virtual desktop infrastructure (VDI) environment, the virtual machines and the user’s local computer must meet the requirements outlined in this section.

<div>


> [!NOTE]  
> Refer to your virtualization solution provider for details about how to install and deploy the virtualized environment. For information about deploying a virtualized environment based on Hyper-V and Remote Desktop Services, see the following articles in the Microsoft TechNet Library: 
> <UL>
> <LI>
> <P>Hyper-V at <A class=uri href="https://go.microsoft.com/fwlink/p/?linkid=247514">https://go.microsoft.com/fwlink/p/?linkid=247514</A></P>
> <LI>
> <P>Remote Desktop Services in Windows Server&nbsp;2008&nbsp;R2 at <A class=uri href="https://go.microsoft.com/fwlink/p/?linkid=247513">https://go.microsoft.com/fwlink/p/?linkid=247513</A></P></LI></UL>



</div>

The following are requirements for the virtual machines running on the data center computer:

  - Virtual machines must be configured with Windows 10, Windows 8.1, Windows 8, Windows 7, or Windows Server 2008 R2 with the latest service packs.

The following are requirements for the user and the user’s local computer:

  - The user must be homed on Lync Server 2013.

  - The local computer must be running Windows Embedded Standard 7 with SP1, Windows 7 with SP1, Windows 8, Windows 8.1 Embedded, or Windows 8.1 (not embedded).

  - If you are using Remote Desktop Services, the Lync VDI plug-in bitness (that is, whether the application is 32-bit or 64-bit) must match the local computer’s operating system bitness. The bitness of the operating system on the local computer and the operating system on the virtual machine do not need to match. If you are using another virtualization solution or platform, refer to guidance from your virtualization solution provider about bitness requirements.

  - The local computer must be running the latest version of the remote desktop client. Install the latest updates of Remote Desktop Services client from Microsoft or the latest remote desktop client software from your virtualization solution provider. For the latest Remote Desktop Services updates, see [https://go.microsoft.com/fwlink/p/?LinkId=268032](https://go.microsoft.com/fwlink/p/?linkid=268032).

  - On the local computer, the remote desktop client settings must be configured so that audio plays on the local computer and remote recording is disabled. To configure these settings for Remote Desktop Connection in Windows, see the next section, "To configure Remote Desktop Connection settings."

<div>

## To configure Remote Desktop Connection settings

To prepare Remote Desktop Connection in Windows for the Lync VDI plug-in, follow these steps.

1.  If the local computer is running Windows 8, skip this step. If the local computer is running Windows 7 with SP1, install the latest Windows 8 version of the Remote Desktop Services client, available at [https://go.microsoft.com/fwlink/p/?LinkId=268032](https://go.microsoft.com/fwlink/p/?linkid=268032).

2.  Start the Remote Desktop Services client by clicking **Start**, and then clicking **Remote Desktop Connection**.

3.  Click **Options**.

4.  Click the **Local Resources** tab. Under **Remote audio**, click **Settings**, and then do the following:
    
      - Under **Remote audio playback**, select **Play on this computer**.
    
      - Under **Remote audio recording**, select **Do not record**.
    
      - Click **OK**.

5.  Click the **Experience** tab. Under **Performance**, clear the **Persistent bitmap caching** check box.

6.  Click the **General** tab. In **Computer**, type the name of the virtual machine, and then click **Connect**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

