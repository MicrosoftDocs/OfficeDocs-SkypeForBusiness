---
title: "Perimeter network VoIP components for Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 74230008-695d-436a-90b9-9cd060c70f7b
description: "Outside callers who use unified communications clients for individual or conference calls rely on Edge Server for voice communication with coworkers."
---

# Perimeter network VoIP components for Lync Server 2013
[]
Outside callers who use unified communications clients for individual or conference calls rely on Edge Server for voice communication with coworkers. 
  
On an Edge Server, the Access Edge service provides SIP signaling for calls from Lync users who are outside your organization's firewall. The A/V Edge service enables media traversal of NAT and firewalls. A caller who uses a unified communications (UC) client from outside the corporate firewall relies on the A/V Edge service for both individual and conference calls.
  
The A/V Authentication service is collocated with, and provides authentication services for, the A/V Edge service. Outside users who attempt to connect to the A/V Edge service require an authentication token that is provided by the A/V Authentication Service before their calls can go through.
  

