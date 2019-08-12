---
title: 'Lync Server 2013: Enforce phone locking'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enforce phone locking
ms:assetid: 1f89298b-aea9-4952-93ca-0270b565792b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520963(v=OCS.15)
ms:contentKeyID: 48183594
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enforce phone locking in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-23_

Lync Phone Edition devices can be locked for security purposes. If you enforce phone lock, the device running Lync Phone Edition locks after a period of time that you configure. When a phone is locked, a user can make calls but cannot access calendar and contact information, voice mail, or call logs or use search. To unlock the phone, the user enters a PIN.

To enforce phone lock, enable and configure it by using Lync Server Control Panel or Lync Server PowerShell cmdlets. You can enforce phone lock globally or only within the site for which it is configured.

<div>

## To configure and enforce the phone lock

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Click **Clients**, and then click **Device Configuration**.

4.  On the **Device Configuration** tab, in the list of device configurations, double-click the configuration for which you want to change the phone lock settings.

5.  In the **Edit Device Configuration** dialog box, verify that the **Enforce device locking** check box is selected.

6.  In **Minimum PIN length**, accept the default value for the minimum number of digits that the unlock PIN must contain or specify a new value. The range for the PIN length is four to 15 digits, and the default is six.

7.  In **Phone lock time-out**, accept the default value for the minimum length of time before the phone locks itself or specify a new value. The range for the timeout is 0 to 60 minutes, and the default is 10. Enter the value in the format HH:MM:SS.

8.  Click **Commit**.

</div>

<div>

## Enforcing Phone Locking by Using Windows PowerShell Cmdlets

Phone locking can be enforced by using the Set-CsUCPhoneConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

<div>

## To enable phone locking

  - The following command enables phone locking for the Redmond site. To disable phone locking, set the EnforcePhoneLock property to False ($False).
    
        Set-CsUCPhoneConfiguration -Identity" site:Redmond" -EnforcePhoneLock $True

</div>

<div>

## To enable phone locking and modify the phone lock timeout

  - This command enables phone locking and also sets the phone lock timeout to 30 minutes.
    
        Set-CsUCPhoneConfiguration -Identity" site:Redmond" -EnforcePhoneLock $True -PhoneLockTimeout "00:30:00"

</div>

<div>

## To enable phone locking throughout the organization

  - In this example, phone locking is enabled on all the UC phone configuration settings in use in the organization.
    
        Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration  -EnforcePhoneLock $True

</div>

For more information, see the help topic for the [Set-CsUCPhoneConfiguration](https://docs.microsoft.com/powershell/module/skype/Set-CsUCPhoneConfiguration) cmdlet.

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

