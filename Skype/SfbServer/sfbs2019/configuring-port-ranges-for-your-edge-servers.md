---
title: "Configuring port ranges for your Edge Servers in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 7/24/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6f0ae442-6624-4e3f-849a-5b9e387fb8cf
description: "With Edge servers you do not have to configure separate port ranges for audio, video, and application sharing; likewise, the port ranges used for Edge servers do not have to match the port ranges used with your Conferencing, Application, and Mediation servers. Before we proceed with our example, it's important to stress that while this option exists, we do recommend you not change the port ranges, as this may adversely affect some scenarios if you move out of the 50000 port range."
---

# Configuring port ranges for your Edge Servers in Lync Server 2013
[]
With Edge servers you do not have to configure separate port ranges for audio, video, and application sharing; likewise, the port ranges used for Edge servers do not have to match the port ranges used with your Conferencing, Application, and Mediation servers. Before we proceed with our example, it's important to stress that while this option exists, we do recommend you not change the port ranges, as this may adversely affect some scenarios if you move out of the 50000 port range.
  
For example, suppose you have configured your Conferencing, Application, and Mediation servers to use these port ranges:
  
|**Packet Type**|**Starting Port**|**Number of Ports Reserved**|
|:-----|:-----|:-----|
|Application sharing  <br/> |40803  <br/> |8348  <br/> |
|Audio  <br/> |49152  <br/> |8348  <br/> |
|Video  <br/> |57500  <br/> |8034  <br/> |
|**Totals** <br/> |--  <br/> |24730  <br/> |
   
As you can see, your port ranges for audio, video, and application sharing start at port 40803 and encompass a total of 24732 ports. If you prefer, you can configure a given Edge Server to use these overall port values by running a command similar to this one from within the Lync Server Management Shell:
  
```
Set-CsEdgeServer -Identity EdgeServer:atl-edge-001.litwareinc.com -MediaCommunicationPortStart 40803 -MediaCommunicationPortCount 24730
```

Or, use the following command to simultaneously configure all the Edge Servers in your organization:
  
```
Get-CsService -EdgeServer | ForEach-Object {Set-CsEdgeServer -Identity $_.Identity -MediaCommunicationPortStart 40803 -MediaCommunicationPortCount 24730}
```

You can verify the current port settings for your Edge Servers by using this Lync Server Management Shell command:
  
```
Get-CsService -EdgeServer | Select-Object Identity, MediaCommunicationPortStart, MediaCommunicationPortCount
```

Again, while we do provide these options, we strongly recommend you leave things as they are for the port configuration.
  

