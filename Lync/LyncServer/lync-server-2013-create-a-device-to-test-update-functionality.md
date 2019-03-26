---
title: 'Lync Server 2013: Create a device to test update functionality'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create a device to test update functionality
ms:assetid: ce509fd1-17b3-4b78-b269-fe5d06fe2e1d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg182587(v=OCS.15)
ms:contentKeyID: 48185466
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a device to test update functionality in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

You can add a test device to the **Test Device** page and then use this device to verify the functionality of new updates before deploying the updates to production devices. You can test a device globally (throughout your entire Lync Server environment) or within a single site. You identify a test device by its Media Access Control (MAC) address or serial number. When you add a device, it appears in the list on the **Test Device** page of the Lync Server Control Panel.

<div>

## To add a test device

1.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

2.  In the left navigation bar, click **Clients**, and then click **Test Device**.

3.  Click **New**, and then click either **Global test device** or **Site test device**.

4.  Do one of the following:
    
      - If you clicked **Global test device**, skip to the next step.
    
      - If you clicked **Site test device**, select a site from the list of available sites, and then click **OK**.

5.  In **New Test Device**, type a name for the device in **Device name**.

6.  Under **Identifier type**, click either **MAC address** or **Serial number**.

7.  In the **Unique identifier** box, type the MAC address or serial number of the device.

8.  Click **Commit**.

</div>

<div>

## Creating Test Devices by Using Windows PowerShell Cmdlets

Test devices can be created by using Windows PowerShell and the New-CsTestDevice cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

When creating test devices using this cmdlet, you must do two things:

  - Specify either MACAddress or SerialNumber as the IdentifierType.

  - Include the scope when specifying the device Identity. To create a new device at the global scope use syntax similar to this:
    
        -Identity "global/WindowsPhone"
    
    To create a test device at the site scope use syntax similar to this:
    
        -Identity "site:Redmond/WindowsPhone"

<div>

## To create a test device by using the MAC address

  - This command creates a test device at the global scope, and using the MAC address as the IdentifierType:
    
        New-CsTestDevice -Identity "global/WindowsPhone" -IdentifierType "MACAddress" -Identifier "01:02:03:04:05:06"

</div>

<div>

## To create a test device by using the serial number

  - This command creates a new test device at the site scope (for the Redmond site) and uses the serial number as the IdentifierType:
    
        New-CsTestDevice -Identity "site:Redmond/WindowsPhone" -IdentifierType "SerialNumber" -Identifier "01ABC5419JKR55T"

</div>

For more information, see the help topic for the [New-CsTestDevice](https://docs.microsoft.com/powershell/module/skype/New-CsTestDevice) cmdlet.

</div>

</div>

<span> </span>

</div>

</div>

</div>

