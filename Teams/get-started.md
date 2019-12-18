---
title: Quick start
author: JuliaDegnan
ms.author: judegn
manager: serdars
ms.date: 01/28/2019
ms.topic: article
audience: admin
ms.service: msteams
ms.reviewer: lolaj
description: Get started with planning your network quickly. 
localization_priority: Priority
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---
# Plan your network
We assume you already know your way around the Teams admin center, and you are familiar with what you need to do to plan your network for Teams. 

To quickly get up and running using Teams, complete the following tasks:

1. Verify all locations have internet access so they can connect to Office 365. At a minimum, verify that the following common ports are open to the internet from all locations:

    - Open TCP ports **80** and **443** for outgoing traffic from clients that will use Teams    
    - Open UDP ports **3478** through **3481** for outgoing traffic from clients that will use Teams

1. Verify your organization has deployed Exchange Online and SharePoint Online, and a verified domain for Office 365 (for example, contoso.com).

## Using Network Planner

If you want help assessing your network, including bandwidth calculations and network requirements across your org's physical locations, check out the [Network Planner](https://docs.microsoft.com/en-us/microsoftteams/network-planner) tool located in the Teams Admin Center. When you provide your network details and Teams usage, the Network Planner calculates your network requirements for deploying Teams and cloud voice across your organization’s physical locations.

For an example scenario, see [Using Network Planner - example scenario](tutorial-network-planner-example).

## Next steps

Go to [Optimize your network](optimize-your-network.md).

Learn more with our interactive [Teams Adoption Guide](https://aka.ms/teamstoolkit).
