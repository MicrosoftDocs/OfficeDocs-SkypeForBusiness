---
title: 'Configuring Quality of Service on Microsoft Lync Phone Edition devices'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Quality of Service on Microsoft Lync Phone Edition devices
ms:assetid: a6eb2620-a512-4ab6-bdfd-eb76be43bbfe
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205137(v=OCS.15)
ms:contentKeyID: 48185004
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Quality of Service on Microsoft Lync Phone Edition devices in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Although Quality of Service (QoS) is not enabled by default for devices such as iPhones, QoS is enabled by default for devices running Lync Phone Edition. (These devices are commonly referred to as UC or Unified Communication phones.) To verify this, run the following Windows PowerShell command from within the Lync Server Management Shell:

    Get-CsUCPhoneConfiguration

If you have not made any changes to your UC phone configuration settings then you will get back information that looks like this:

    Identity             : Global
    CalendarPollInterval : 00:03:00
    EnforcePhoneLock     : True
    PhoneLockTimeout     : 00:10:00
    MinPhonePinLength    : 6
    SIPSecurityMode      : High
    VoiceDiffServTag     : 40
    Voice8021p           : 0
    LoggingLevel         : Off

For Quality of Service purposes, only one of these properties is of interest: VoiceDiffServTag. The VoiceDiffServTag represents the DSCP value assigned to voice traffic emanating from a Lync Phone Edition device.

<div>


> [!NOTE]
> The Voice8021p parameter is no longer supported in Lync Server 2013. The parameter is still valid for backward compatibility with Microsoft Lync Server 2010; however, it has no effect on devices used with Lync Server 2013.



</div>

In most networks, marking Lync Phone Edition packets with a VoiceDiffServTag of 40 should not cause any problems. However, 40 is not the value typically used for audio traffic; instead, audio traffic is almost always marked with the DSCP code 46. In order to maintain consistency throughout your network, you might want to change the VoiceDiffServTag property of your UC phones to 46.

To do that, you can use either Windows PowerShell or the Lync Server Control Panel. To modify the VoiceDiffServTag value by using Windows PowerShell, run the following command from within the Lync Server Management Shell:

    Set-CsUCPhoneConfiguration -VoiceDiffServTag 46

The preceding command modifies the global collection of UC phone configuration settings. Note, however, that UC phone settings can also be assigned to the site scope. To modify UC phone configuration settings at the site scope, you must specify the site Identity. For example:

    Set-CsUCPhoneConfiguration -Identity "site:Redmond" -VoiceDiffServTag 46

You can also use the following command to simultaneously modify all your UC phone configuration settings:

    Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration -VoiceDiffServTag 46

If you prefer to make this change using Lync Server Control Panel, then start the Control Panel and then complete the following procedure:

1.  Click **Clients** and then click **Device Configuration**.

2.  On the **Device Configuration** tab, double-click the collection of settings you want to modify (for example, **Global**).

3.  In the **Edit Device Configuration** dialog box, set the value of the **Voice Quality of Service (QoS)** box to **46** and then click **Commit**.

If you have multiple collections you will need to repeat this process for each collection of UC phone settings. Lync Server Control Panel will not allow you to simultaneously modify multiple setting collections.

If you have devices that are not based on the Windows operating system (such as iPhones) in your organization these devices will not be affected by changing the VoiceDiffServTag setting. If you want to change DSCP values on those devices you will need to refer to the administration manual for each of your device types.

</div>

<span> </span>

</div>

</div>

</div>

