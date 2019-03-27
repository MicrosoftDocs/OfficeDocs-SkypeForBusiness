---
title: 'Lync Server 2013: Create contact objects for hosted Exchange UM'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create contact objects for hosted Exchange UM
ms:assetid: a39be52f-488a-4523-ad5f-ce1f0d681959
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412765(v=OCS.15)
ms:contentKeyID: 48185045
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create contact objects for hosted Exchange UM in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-24_

The following procedure explains how to create Auto Attendant (AA) or Subscriber Access (SA) contact objects for hosted Exchange Unified Messaging (UM).

For details, see [Hosted Exchange Contact object management in Lync Server 2013](lync-server-2013-hosted-exchange-contact-object-management.md) in the Planning documentation.

For details about configuring contact objects, see the Lync Server Management Shell documentation for the following cmdlets:

  - [New-CsExUmContact](https://docs.microsoft.com/powershell/module/skype/New-CsExUmContact)

  - [Set-CsExUmContact](https://docs.microsoft.com/powershell/module/skype/Set-CsExUmContact)

<div class=" ">


> [!IMPORTANT]  
> Before Lync Server 2013 contact objects can be enabled for hosted Exchange UM, a hosted voice mail policy that applies to them must be deployed. For details, see <A href="lync-server-2013-hosted-voice-mail-policies.md">Hosted voice mail policies in Lync Server 2013</A>.



</div>

<div>

## To create AA or SA contact objects for hosted Exchange UM

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the New-CsExUmContact cmdlet to create any contact objects required for your deployment. For example, run the following to create an AA and an SA contact object:
    
       ```
        New-CsExUmContact -SipAddress "sip:exumaa1@fabrikam.com" -RegistrarPool "RedmondPool.litwareinc.com" -OU "HostedExUM Integration" -DisplayNumber "+14255550101" -AutoAttendant $True
       ```
    
       ```
        New-CsExUmContact -SipAddress "sip:exumsa1@fabrikam.com" -RegistrarPool "RedmondPool.litwareinc.com" -OU "HostedExUM Integration" -DisplayNumber "+14255550101"
       ```
    
    These examples set the following parameters:
    
      - **SipAddress** specifies the SIP address of the contact object. This must be an address that has not already been used to configure a user or contact object in Active Directory Domain Services. This value must be in the format “sip:\<*SIP address*\>“ as shown in the previous examples.
    
      - **RegistrarPool** specifies the fully qualified domain name (FQDN) of the pool on which the Registrar service is running.
        
        <div class=" ">
        

        > [!NOTE]  
        > Exchange UM contact objects cannot be moved to pools that are part of Lync Server 2013 deployments prior to Lync Server 2013.

        
        </div>
    
      - **OU** specifies the Active Directory organizational unit where this contact object will be located.
    
      - **DisplayNumber** specifies the telephone number of the contact object. The phone number for each contact object must be unique.
    
      - **AutoAttendant** specifies whether the Contact object is an Auto Attendant. Auto Attendant provides a set of voice prompts that allow callers to navigate the phone system and reach the party that they want to contact. A value of **False** (the default) for this parameter indicates a Subscriber Access contact object.

</div>

</div>

<span> </span>

</div>

</div>

</div>

