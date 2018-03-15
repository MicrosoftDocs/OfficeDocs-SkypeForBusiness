---
title: "Translation rules in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6e067bd4-4931-4385-81ac-2acae45a16d8
description: "Lync Server 2013 Enterprise Voice requires that all dial strings be normalized to E.164 format for the purpose of performing reverse number lookup (RNL). In Microsoft Lync Server 2010, translation rules are supported only for called numbers. New in Microsoft Lync Server 2013, translation rules are also supported for calling numbers. The trunk peer (that is, the associated gateway, private branch exchange (PBX), or SIP trunk) may require that numbers be in a local dialing format. To translate numbers from E.164 format to a local dialing format, you can define one or more translation rules to manipulate the request URI before you route it to the trunk peer. For example, you could write a translation rule to remove +44 from the beginning of a dial string and replace it with 0144."
---

# Translation rules in Lync Server 2013
[]
Lync Server 2013 Enterprise Voice requires that all dial strings be normalized to E.164 format for the purpose of performing reverse number lookup (RNL). In Microsoft Lync Server 2010, translation rules are supported only for called numbers. New in Microsoft Lync Server 2013, translation rules are also supported for calling numbers. The trunk peer (that is, the associated gateway, private branch exchange (PBX), or SIP trunk) may require that numbers be in a local dialing format. To translate numbers from E.164 format to a local dialing format, you can define one or more translation rules to manipulate the request URI before you route it to the trunk peer. For example, you could write a translation rule to remove +44 from the beginning of a dial string and replace it with 0144. 
  
By performing outbound route translation on the server, you can reduce the configuration requirements on each individual trunk peer in order to translate phone numbers into a local dialing format. When you plan which gateways, and how many gateways, to associate with a specific Mediation Server cluster, it may be useful to group trunk peers with similar local dialing requirements. This can reduce the number of required translation rules and the time it takes to write them.
  
> [!IMPORTANT]
> Associating one or more translation rules with an Enterprise Voice trunk configuration should be used as an alternative to configuring translation rules on the trunk peer. Do not associate translation rules with an Enterprise Voice trunk configuration if you have configured translation rules on the trunk peer, because the two rules might conflict. 
  
## Example Translation Rules

The following examples of translation rules show how you can develop rules on the server to translate numbers from E.164 format to a local format for the trunk peer.
  
For details about how to implement translation rules, see [Defining translation rules in Lync Server 2013](defining-translation-rules.md) in the Deployment documentation. 
  
|**Description**|**Starting Digits**|**Length**|**Digits to Remove**|**Digits to Add**|**Matching Pattern**|**Translation**|**Example**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Conventional long-distance dialing in U.S.  <br/> (strip out the '+')  <br/> |+1  <br/> |Exactly 12  <br/> |1  <br/> |0  <br/> |^\+(1\d{10})$  <br/> |$1  <br/> |+14255551010 becomes 14255551010  <br/> |
|U.S. international long-distance dialing  <br/> (strip out '+' and add 011)  <br/> |+  <br/> |At least 11  <br/> |1  <br/> |011  <br/> |^\+(\d{9}\d+)$  <br/> |011$1  <br/> |+441235551010 becomes 011441235551010  <br/> |
   

