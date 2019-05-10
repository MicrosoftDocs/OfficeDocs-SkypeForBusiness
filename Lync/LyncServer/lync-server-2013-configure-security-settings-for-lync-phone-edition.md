---
title: 'Lync Server 2013: Configure security settings for Lync Phone Edition'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configure security settings for Lync Phone Edition
ms:assetid: 6e7cec17-8a79-4428-9300-8821256c46cf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg521014(v=OCS.15)
ms:contentKeyID: 48184464
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure security settings for Lync Phone Edition in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Help improve the security of devices running Lync Phone Edition via your SIP security setting and phone lock settings.

<div>

## To configure security settings for Lync Phone Edition

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Clients**, and then click **Device Configuration**.

4.  On the **Device Configuration** page, in the list of device configurations, double-click the configuration for which you want to change security settings.

5.  In **Edit Device Configuration**, in **SIP security**, specify the SIP security level. The default level is **High**, which we recommend using.

6.  In **Edit Device Configuration**, under **Phone Lock**, select or clear the **Enforce device locking** check box (selected by default) and specify the minimum PIN length (6 characters by default) and timeout period (10 minutes by default). We recommend using these defaults or increasing the PIN length and/or decreasing the timeout period.
    
    <div>
    

    > [!NOTE]  
    > For details, see <A href="lync-server-2013-enforce-phone-locking.md">Enforce phone locking in Lync Server 2013</A>.

    
    </div>

</div>

<div>

## Configuring Security Settings for Lync Phone Edition Phones by Using Windows PowerShell Cmdlets

Security settings can be managed by using Lync Server Management Shell and the **Get-CsUCPhoneConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To modify the SIP security mode

  - This command sets the SIPSecurityMode for the global collection of UC phone settings to Medium. SIP security could also be set to Low or High (the default value).
    
        Set-CsUCPhoneConfiguration -Identity global -SIPSecurityMode "Medium"

</div>

<div>

## To modify the minimum PIN length

  - In this example, all the UC phone settings are modified to require a minimum PIN length of 7 digits.
    
        Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration -MinPhonePinLength 7

</div>

For details, see [Get-CsUCPhoneConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsUCPhoneConfiguration).

</div>

<div>

## See Also


[Managing Lync Server 2013 authentication](lync-server-2013-managing-lync-server-authentication.md)  


[Managing devices, phones, and client applications in Lync Server 2013](lync-server-2013-managing-devices-phones-and-client-applications.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

