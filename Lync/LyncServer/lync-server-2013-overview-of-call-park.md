---
title: 'Lync Server 2013: Overview of Call Park'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Overview of Call Park
ms:assetid: 985dc326-0aef-4308-b98b-c1d0069311e7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205124(v=OCS.15)
ms:contentKeyID: 48184939
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Overview of Call Park in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-29_

The Lync Server 2013 Call Park application lets Enterprise Voice users do any of the following:

  - Put a call on hold and then retrieve the call from the same phone or another phone.

  - Put a call on hold to transfer it to a department or general area (for example, to a sales department or a warehouse where there is a common area phone).

  - Put a call on hold and keep the original answering phone free for other calls.

When a user parks a call, Lync Server transfers the call to a temporary number, called an *orbit*, where the call is held until it is retrieved or it times out. Lync Server sends the orbit to the user who parked the call. To retrieve the parked call, the user can dial the orbit number or click the orbit link or button in the Conversation window.

The user who parked a call can notify someone to retrieve the call by using an external mechanism, such as instant messaging (IM) or a paging system, to communicate the orbit number to someone else. The user who parked the call can leave the Conversation window open to receive notification when the call is retrieved.

Because orbit ranges are globally unique, it is possible to retrieve calls from any Lync Server site or PBX phone if routing is configured appropriately. If no one retrieves the call within a configurable amount of time, the call rings back to the person who parked it. If that person does not answer the ringback, the call is transferred to a fallback destination, such as to an operator, if so configured. You can configure the number of times the call rings back before being transferred from one to ten times. If no one answers a transferred call, the call is disconnected. The orbit is freed when the call is retrieved or disconnected.

When you deploy Call Park, you need to reserve ranges of extension numbers for parking calls. These extensions need to be virtual extensions: extensions that have no user or phone assigned to them. You then configure the call park orbit table with the ranges of extension numbers and specify which Application service hosts the Call Park application that handles each range. Each Front End pool has a Call Park table on the corresponding Back End Server that is used to manage calls that are parked on the pool. The list of orbit ranges is stored in Central Management store and is used to route orbits to the destination pool. Each Lync Server pool where the Call Park application is deployed and configured can have one or more orbit ranges. Orbit ranges must be globally unique across the Lync Server deployment.

You also configure other Call Park settings, such as where calls are redirected if they time out and whether the person on the phone hears music while parked. You can also specify the music file to play while the call is on hold.

<div>


> [!NOTE]  
> Customized music-on-hold files for Call Park are not backed up as part of the Lync Server 2013 disaster recovery process and will be lost if the files uploaded to the pool are damaged, corrupted, or erased. Always keep a separate backup copy of the customized music-on-hold files that you have uploaded for Call Park.



</div>

The Call Park application is a component of Enterprise Voice. When you deploy Enterprise Voice, the Call Park application is installed and activated automatically. Before you can use Call Park, however, the Enterprise Voice administrator must configure it and enable it for users through voice policy.

</div>

<span> </span>

</div>

</div>

</div>

