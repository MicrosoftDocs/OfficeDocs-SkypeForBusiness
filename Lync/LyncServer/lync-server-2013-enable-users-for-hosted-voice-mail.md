---
title: 'Lync Server 2013: Enable users for hosted voice mail'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Enable users for hosted voice mail
ms:assetid: fa559f8f-ef99-43a1-b580-9e998b95efb8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413062(v=OCS.15)
ms:contentKeyID: 48185919
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable users for hosted voice mail in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-24_

Follow the procedure to enable Lync Server 2013 users for voice mail on a hosted Exchange Unified Messaging (UM) service.

For details, see [Hosted Exchange user management in Lync Server 2013](lync-server-2013-hosted-exchange-user-management.md) in the Planning documentation.

For details about the [Set-CsUser](https://docs.microsoft.com/powershell/module/skype/Set-CsUser) cmdlet, see the Lync Server Management Shell documentation.

<div>


> [!IMPORTANT]  
> Before a Lync Server 2013 user can be enabled for hosted voice mail, a hosted voice mail policy that applies to their user account must be deployed. For details, see <A href="lync-server-2013-hosted-voice-mail-policies.md">Hosted voice mail policies in Lync Server 2013</A>.



</div>

<div>

## To enable users for hosted voice mail

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Run the Set-CsUser cmdlet to configure the user account for hosted voice mail. For example, run:
    
        Set-CsUser -HostedVoiceMail $True -Identity "contoso\kenmyer"
    
    The preceding example sets the following parameters:
    
      - **HostedVoiceMail** enables a user’s voice mail calls to be routed to hosted Exchange UM. It also signals Microsoft Lync 2013 to light up the “call voice mail” indicator.
    
      - **Identity** specifies the user account to be modified. The Identity value can be specified using any of the following formats:
        
          - The user's SIP address
        
          - The user's Active Directory User-Principal-Name
        
          - The user's domain\\logon name (for example, contoso\\kenmyer)
        
          - The user's Active Directory Domain Services Display-Name (for example, Ken Myer). If using the Display-Name as the Identity value, you can use the asterisk (\*) wildcard character. For example, the Identity "\* Smith" returns all the users who have a Display-Name that ends with the string value "Smith".
        
        <div>
        

        > [!NOTE]  
        > The user’s Active Directory SAM-Account-Name cannot be used as the Identity value because the SAM-Account-Name is not necessarily unique in the forest.

        
        </div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

