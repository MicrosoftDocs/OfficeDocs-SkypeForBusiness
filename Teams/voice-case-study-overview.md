---
title: Teams voice Contoso case study
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords: ms.teamsadmincenter.directrouting.overview
f1.keywords:
- NOCSH
description: Teams voice case study for multi-national corporation
appliesto: 
  - Microsoft Teams
---


- [Plan Direct Routing](direct-routing-plan.md) 

# Overview

The Contoso Corporation is a fictional but representative global manufacturing conglomerate with its headquarters in Paris, France. Contoso has deployed Microsoft 365 Enterprise and addressed major design decisions and implementation details for networking, identity, Windows 10 Enterprise, Office 365 ProPlus, mobile device management, information protection, security,migration from Skype for Business to teams, phone system, and audio conferencing.  

The overall goal of Contoso for Microsoft 365 Enterprise is to accelerate their digital transformation by using cloud services to bring together its employees, partners, data, and processes to create customer value and maintain its competitive advantage in a digital-first world. 

These articles ...

To migrate from Skype for Business to Teams, Contoso realized it was necessary to consider the end user impacts during the transition time.  Instead of switching everyone to Teams at the same time, they set up Hybrid, moved the Teams enabled users to Skype for Business online which allowed users in Teams and Skype for Business on-premises to share presence and communicate.  

Contoso followed Migration and interoperability guidance for organizations using Teams together with Skype for Business and attended the Ignite 2019 session Designing your path from Skype for Business to Teams: Start Here!  to: 

- Understand fundamental concepts such as interopt, federation, and upgrade behavior 

- Coexistence modes and management based on TeamsUpgradePolicy 

- End user experience for 

  - Chat and Calling 

  - Meeting Scheduling 

  - Availability of collaboration functionality in Teams clients 

 

Contoso decided to: 

- Follow Configure Skype for Business Hybrid to: 

  - Configure on-premises environment service to federate with Office 365 

  - Configure on-premises environment to trust Office 365 and enable on-premises environment to enable shared SIP address space 

  - Enable shared Sip address space in your Office 365 tenant 

  - Leverage islands mode during the technical pilot 

  - Switch users over to Teams Only mode once the user is enabled for Phone System. Teams only mode is required for direct routing and calling plan. 

