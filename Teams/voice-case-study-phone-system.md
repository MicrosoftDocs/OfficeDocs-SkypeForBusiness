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

In adoption of Microsoft Phone System, Contoso had to decide on which sites would leverage the following solutions:

- Phone System with Calling Plan 

- Phone System with own PSTN carrier with Direct routing 

- Combination of Phone System with Calling Plan and Phone System with own PSTN carrier with Direct Routing 
 
Contoso leveraged Microsoft telephony solutions and Ignite 2019 session Calling in Microsoft Teams to determine the right solution for their organization.  


Contoso had offices that were entirely on Skype for Business Enterprise voice, some offices that were leveraging a traditional legacy telephony system, and other sites that had some users on Skype for Business Enterprise Voice and others on traditional legacy telephony systems. 


## Site Type A: Traditional Legacy Telephony Systems 

Contoso had many offices that leveraged legacy telephony systems. There were a subset of users that had an E1.64 phone number while others only had an extension.  These numbers resided on the TDM trunk to the PSTN gateway.  Intra-site dialing was configured by leveraging a site code in front of the extension to determine where to route the call.  The users dialing habits was to dial by extension.   

 

Contoso leveraged Microsoft telephony solutions  to determine the right solution for their organization.  

 

Questions Contoso asked themselves: 

Q. Do we require to retain functionality provided our r on-premises deployment? A. No 

Q. Do we need to interoperate with 3rd party PBXs and other telephony equipment? A. No 

Q. Do we need to retain your current third-party carrier? A. No 

Q. Is Microsoft PSTN's calling available in your region? Yes and No 

 

Decision: 

Contoso decided to move the users that are located in a region where PSTN calling plans is available to Phone System with Calling Plans. 

Contoso decided to move the users that are not located in a region where PSTN calling plans is available to Phone System with Direct Routing 

 

 
