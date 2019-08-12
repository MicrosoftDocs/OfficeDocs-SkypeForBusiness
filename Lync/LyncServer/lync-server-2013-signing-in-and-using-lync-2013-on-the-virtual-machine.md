---
title: 'Lync Server 2013: Signing in and using Lync 2013 on the virtual machine'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Signing in and using Lync 2013 on the virtual machine
ms:assetid: 6140fc19-5bef-4b58-9b0f-19112b5ecd00
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204948(v=OCS.15)
ms:contentKeyID: 48184318
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Signing in and using Lync 2013 on the virtual machine

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

After the VDI plug-in is enabled, the following steps occur when the user signs in to Lync 2013.

1.  The user types his or her credentials in to the Lync 2013 client running on the virtual machine.

2.  After Lync detects the availability of the VDI plug-in, Lync prompts the user to re-enter his or her credentials. In this dialog box, we recommend that the user select the **Save my password** check box so that he or she will not be required to enter credentials during subsequent sign in.

3.  Lync begins pairing with the VDI plug-in. Before pairing is complete, the client displays two icons in the Lync status bar. The icon in the lower left indicates that no audio devices are available, and the blinking icon in the lower right indicates that the VDI pairing is in progress, as shown:
    
    ![Lync VDI icon showing successful pairing](images/JJ204948.303d618c-4bc8-41c4-8553-2475de0d395e(OCS.15).png "Lync VDI icon showing successful pairing")  

4.  After VDI pairing is successful, the icons change to indicate the audio device that will be used for calls and the VDI pairing success:
    
    ![Lync VDI pairing icon showing success](images/JJ204948.57be3387-a3e5-4949-831e-f5ff9fcc5598(OCS.15).png "Lync VDI pairing icon showing success")  

5.  After Lync pairs with the VDI plug-in, the user can see his or her presence on Lync compatible devices that are connected to the local computer. The user can now place and answer calls as usual.

</div>

<span> </span>

</div>

</div>

</div>

