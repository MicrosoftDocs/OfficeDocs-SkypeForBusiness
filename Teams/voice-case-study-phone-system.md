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


# Contoso case study: Phone System

Depending on geographic location and other factors, Contoso had offices using the following telephony solutions:

- [Site Type A: Skype for Business Enterprise Voice](#site-type-a:-skype-for-business-enterprise-voice)
- [Site Type B: Traditional legacy telephony systems](#site-type-b:-traditional-legacy-telephony-systems)
- [Site Type C: A combination of Skype for Business Enterprise Voice and traditional legacy telephony systems](#site-type-c:-combination-of-skype-for-business-enterprise-voice-and-traditional-legacy-telephony-systems)


To implement a Microsoft Phone System solution for their entire organization, Contoso had to determine--for each site type--which of the following options would be used with Phone System to connect to the Public Switched Telephone Network (PSTN):

- Phone System with Calling Plan 

- Phone System with own PSTN carrier through Direct Routing 

- Combination of Phone System with Calling Plan and Phone System with own PSTN carrier through Direct Routing
 
To determine the right solution for their organization, Contoso leveraged [Microsoft telephony solutions](https://docs.microsoft.com/SkypeForBusiness/hybrid/msft-telephony-solutions) and the Ignite 2019 session [Calling in Microsoft Teams](https://myignite.techcommunity.microsoft.com/sessions/83170?source=sessions).  

## Site Type A: Skype for Business Enterprise Voice 

Contoso Skype for Business Enterprise Voice was set up as a hub and spoke. There was a central location that maintained the PSTN gateway in the region that provided the connection to the PSTN for the Skype for Business Enterprise Voice users in country. Often these satellite offices did not have their own Internet egress. The numbers for these users resided on the SIP trunk connecting to an existing SBC. 

To determine if the SBC already deployed is certified for Direct Routing and Media Bypass, Contoso checked the [List of Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).  

The users' dialing habits were to dial a user on the legacy telephony system using an extension, even when the user has a Skype for Business client available for peer-to-peer audio. 

Contoso based their decision on the following questions:

- Q. Do we need to retain functionality provided by our on-premises deployment?
  A. No 

- Q. Do we need to interoperate with third-party PBX systems and other telephony equipment? 
  A. No 

- Q. Do we need to retain our current third-party carrier? 
  A. Yes (regulated countries) and No 

- Q. Do we need to get the ROI on SBCs deployed? 
  A. Yes and No  

- Q. Is Microsoft PSTN Calling Plans available in this region? 
  A. Yes and No 

Based on the answers to their questions, Contoso decided to:

- Move the users that are located in a region where PSTN calling plans is available to Phone System with Calling Plans. 

- Move the users that are not located in a region where PSTN calling plans is available, users located in a site where the ROI on the SBCs have yet to be met, and users that resided in a country that has telephony regulations to Phone System with Direct Routing. 

## Site Type B: Traditional legacy telephony systems

Contoso had many offices that leveraged legacy telephony systems. There were a subset of users that had an E1.64 phone number while others only had an extension.  These numbers resided on the TDM trunk to the PSTN gateway.  Intra-site dialing was configured by leveraging a site code in front of the extension to determine where to route the call.  The users dialing habits was to dial by extension.   

Contoso based their decision on the following questions:

- Q. Do we require to retain functionality provided our r on-premises deployment?
  A. No 

- Q. Do we need to interoperate with 3rd party PBXs and other telephony equipment? 
  A. No 

- Q. Do we need to retain your current third-party carrier? 
  A. No 

- Q. Is Microsoft PSTN's calling available in your region? 
  A. Yes and No 

Based on the answers to their questions, Contoso decided to: 

- Move the users that are located in a region where PSTN calling plans is available to Phone System with Calling Plans. 

- Move the users that are not located in a region where PSTN calling plans is available to Phone System with Direct Routing 

 
## Site Type C: Combination of Skype for Business Enterprise Voice and traditional legacy telephony systems

Contoso Skype for Business Enterprise Voice users numbers reside on the SIP trunk to the SBC from the carrier. The numbers for the traditional telephony systems resided on the TDM trunk to the PSTN gateway.   

Contoso based their decision on the following questions:

- Q. Do we need to retain functionality provided by our on-premises deployment?
  A. No 

- Q. Do we need to interoperate with third-party PBX systems and other telephony equipment? 
  A. No 

- Q. Do we need to retain our current third-party carrier? 
  A. No 

- Q. Do we need to get the ROI on SBCs deployed? 
  A. Yes and No  

- Q. Is Microsoft's PSTN Calling Plan available in this region? 
  A. No 

Based on the answers to their questions, Contoso decided on the following: 

- For the legacy telephony users that will be enabled for Direct Routing, Contoso ported the numbers from the TDM trunk to the SIP Trunk for the SBC, since the SBC is certified for Direct Routing. 

- To support a subset of users moving to Phone System and to allow continued routing through the legacy system, the legacy telephony system was set up as the next hop to the SBC.   

- In addition, to encourage user behavior change and remove the dependency on inter- and intra-site extension dialing, Contoso provided guidance to leverage Teams for all internal calls.  

**NOTE:**
-----Insert articles that can assist with the decision on where to place the SBC ------ 

## Calling Plans

Contoso reviewed the Core deployment decisions to determine the additional questions that should be addressed to determine the configuration requirements for calling plan.  The resulting decisions were made: 

- Q. Do my users need international calling? 
  A. Yes 

- Q. Do my users each have a direct inward DID phone number? 
  A. Not today. All users enabled will receive a DID. 

- Q. Do I want to mask or disable caller ID? 
  A. The caller ID for a user will be masked to the local number for Contoso. 


## Direct Routing

Contoso attended Ignite to stay current on Office 365 features including those available with Phone system and Direct Routing. Technical leadership and architects leverage the guidance provided during the Ignite 2019 to determine their direction.  Key sessions that were leveraged: 

Plan for success with Microsoft Teams Direct Routing 

Updates for Direct Routing 


## Configuration






