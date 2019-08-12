---
title: 'Lync Server 2013: Hosted Exchange Contact object management'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Hosted Exchange Contact object management
ms:assetid: eead9d76-bc4f-4c1c-9779-683cb7a88410
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412978(v=OCS.15)
ms:contentKeyID: 48185748
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Hosted Exchange Contact object management in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-25_

You need to configure a Contact object for each auto-attendant number and subscriber access number in your cross-premises deployment.

For integration with hosted Exchange UM, ocsumutil.exe cannot be used to manage Contact objects, because it depends on Active Directory Exchange UM settings. In a cross-premises deployment, Lync Server 2013 and hosted Exchange UM are installed in separate forests with no trust between them. For security reasons, Lync Server 2013 administrators have no direct access to Exchange UM Active Directory settings. As a result, Lync Server 2013 provides a different model for managing Contact objects in a *shared SIP address space* that is accessible to both Lync Server 2013 and the hosted Exchange UM service.

<div>

## Hosted Contact Object Workflow

The following are the general steps for working with your hosted Exchange tenant administrator to manage contact objects:

1.  The Exchange administrator requests phone numbers for the Exchange UM subscriber access and auto-attendant Contact objects.

2.  The Lync Server 2013 administrator creates a Contact object for each phone number and assigns a hosted voice mail policy to each Contact object.

3.  The Lync Server 2013 administrator provides the phone numbers to the Exchange administrator.

4.  The Exchange administrator assigns the phone numbers to appropriate Exchange UM dial plans for auto attendants and subscriber access.

<div>


> [!NOTE]  
> There is no need to configure any Lync Server 2013 dial plan settings on the Contact objects as there is with on-premises deployments.



</div>

</div>

<div>

## Configuring Hosted Contact Objects

<div>


> [!NOTE]  
> Before Lync Server 2013 Contact objects can be enabled for hosted Exchange UM, a hosted voice mail policy that applies to them must be deployed. The policy can be of global, site-level, or per-user scope, as long as it applies to the contact object you want to enable. For details, see <A href="lync-server-2013-hosted-voice-mail-policies.md">Hosted voice mail policies in Lync Server 2013</A>.



</div>

To configure hosted auto-attendant and subscriber access Contact objects in a cross-premises deployment, you must use the following cmdlets:

  - **New-CsExUmContact** creates a new Contact object for hosted UM.

  - **Set-CsExUmContact** modifies an existing Contact object for hosted Exchange UM.

The following example creates an auto-attendant Contact object:

    New-CsExUmContact -SipAddress sip:exumaa1@fabrikam.com -RegistrarPool RedmondPool.litwareinc.com -OU "OU=ExUmContacts,DC=litwareinc,DC=com" -DisplayNumber 2065559876 -AutoAttendant $True

This example creates a new Exchange UM Contact object with the SIP address sip:exumaa1@fabrikam.com. The name of the pool where the Lync Server 2013 Registrar service is running is RedmondPool.litwareinc.com. The Active Directory organizational unit where this information will be stored is OU=ExUmContacts,DC=litwareinc,DC=com. The phone number of the Contact object is 2065554567. The optional -AutoAttendant $True parameter specifies that this object is an auto-attendant Contact object. Setting the -AutoAttendant parameter to False (the default) specifies a subscriber access Contact object.

For details about the New-CsExUmContact and Set-CsExUmContact cmdlets, see the Lync Server Management Shell documentation.

</div>

</div>

<span> </span>

</div>

</div>

</div>

