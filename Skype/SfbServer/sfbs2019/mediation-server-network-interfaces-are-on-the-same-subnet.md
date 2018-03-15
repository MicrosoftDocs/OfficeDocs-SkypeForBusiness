---
title: "Mediation Server network interfaces are on the same subnet"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7e90955c-87bb-4ad8-a907-24e2a07a937c
description: "Issue: Users may encounter an issue in which calls through this Mediation Server are disconnected immediately after they are connected."
---

# Mediation Server network interfaces are on the same subnet
[]
Issue: Users may encounter an issue in which calls through this Mediation Server are disconnected immediately after they are connected.
  
## Description of the Issue

A Lync Server 2013 Mediation Server has two network interfaces that are connected to the same subnet. In this situation, users may encounter an issue in which calls through this Mediation Server are disconnected immediately after they are connected.
  
## Issue Resolution

Configure the network interfaces to use different subnets and gateways.
  
If the IP addresses of the two network interfaces on the Mediation Server are different, but are in the same subnet, you receive the following alert title and alert text:
  
 **Alert title**
  
Checking if calls from a Mediation Server could disconnect immediately after an initial connection is made
  
 **Alert text**
  
A Mediation Server may have X network interfaces for the gateway (public or external) side and for the proxy (private or internal Lync Front End Server) side. These X network interfaces currently have X unique IP addresses, but they're on the same subnet on your network. For network routing to work correctly, the X network interfaces need to be from different subnets. Each network interface must also have its own default IP gateway. There are some situations when the IP gateways and the Lync Front End Servers are all on the internal network and in the same network subnet. If this is the case, it is fine to use one listening network interface for the Lync Mediation Server.
  
> [!NOTE]
> In the displayed message, X is replaced by a numeric value specific to the issue in your environment. 
  

