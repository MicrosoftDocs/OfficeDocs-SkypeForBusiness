---
title: 'Lync Server 2013: Replacing the XmlAdapter with a customized Persistent Chat Server Compliance adapter'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Replacing the XmlAdapter with a customized Persistent Chat Server Compliance adapter
ms:assetid: 2cb70db2-663f-40a6-abcf-89ea7d4a8b65
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ680106(v=OCS.15)
ms:contentKeyID: 49558152
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Replacing the XmlAdapter with a customized Persistent Chat Server Compliance adapter in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

You can write a custom adapter instead of using the XmlAdapter that is installed with Persistent Chat Server. To accomplish this, you must provide a .NET Framework assembly that contains a public class that implements the **IComplianceAdapter** interface. You must place this assembly in the Persistent Chat Server installation folder of each server in your Persistent Chat Server pool. Any one of the Compliance servers can provide compliance data to your adapter, but the compliance servers will not provide duplicate compliance data to multiple instances of your adapter.

<div>

## Implementing the IComplianceAdapter interface

The interface is defined in the Compliance.dll assembly in the namespace `Microsoft.Rtc.Internal.Chat.Server.Compliance`. The interface defines two methods that your custom adapter must implement.

    void SetConfig(AdapterConfig config)

The Persistent Chat Compliance server will call this method when the adapter first loads. The `AdapterConfig` contains the Persistent Chat compliance configuration that is relevant to the compliance adapter.

    void Translate(ConversationCollection conversations)

The Persistent Chat Compliance server calls this method at periodic intervals as long as there is new data to translate. This time interval is equal to the `RunInterval` as set in the Persistent Chat Compliance configuration.

The `ConversationCollection` contains the conversation information that was collected from the last time this method was called.

</div>

</div>

<span> </span>

</div>

</div>

</div>

