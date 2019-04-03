---
title: 'Lync Server 2013: Configuring Windows 8 for Virtual Smart Cards'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring Windows 8 for Virtual Smart Cards
ms:assetid: 4916c167-4ee3-4f3e-b65c-33e588595112
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn308564(v=OCS.15)
ms:contentKeyID: 54973684
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Windows 8 for using Virtual Smart Cards with Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-03_

One factor to consider when deploying two-factor authentication and smart card technology is the cost of implementation. Windows 8 provides a number of new security capabilities, and one of the most interesting new features is support for virtual smart cards.

For computers equipped with a Trusted Platform Module (TPM) chip that meets specification version 1.2, organizations can now get the benefits of smart card logon without making any additional investments in hardware. For more information, see Using Virtual Smart Cards with Windows 8 at [http://go.microsoft.com/fwlink/p/?LinkId=313365](http://go.microsoft.com/fwlink/p/?linkid=313365).

<div>

## To Configure Windows 8 for Virtual Smart Cards

1.  Log in to the Windows 8 computer using the credentials of a Lync-enabled user.

2.  At the Windows 8 Start screen, move your cursor to the bottom right corner of the screen.

3.  Select the **Search** option, and then search for **Command Prompt**.

4.  Right click on **Command Prompt**, and then select **Run as Administrator**.

5.  Open the Trusted Platform Module (TPM) Management console by running the following command:
    
        Tpm.msc

6.  From the TPM management console, verify that your TPM specification version is at least 1.2
    
    <div>
    

    > [!NOTE]  
    > If you receive a dialog stating that a Compatible Trust Platform Module (TPM) cannot be found, verify that the computer has a compatible TPM module and that it is enabled in the system BIOS.

    
    </div>

7.  Close the TPM management console

8.  From the command prompt, create a new virtual smart card using the following command:
    
        TpmVscMgr create /name MyVSC /pin default /adminkey random /generate
    
    <div>
    

    > [!NOTE]  
    > To provide a custom PIN value when creating the virtual smart card, use /pin prompt instead.

    
    </div>

9.  From the command prompt, open the Computer Management console by running the following command:
    
        CompMgmt.msc

10. In the Computer Management console, select **Device Management**.

11. Expand **Smart card readers**.

12. Verify that the new virtual smart card reader has been created successfully.

</div>

</div>

<span> </span>

</div>

</div>

</div>

