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

In Office 365, calling plan user is automatically enabled for emergency calling. Contoso reviewed the Emergency Calling Overview to get an understanding of the availability of emergency calling and terminology related to emergency calling: Emergency Address, Place, Emergency Location, and Registered address. 

 The Contoso calling plan users In the United States, can leverage dynamic locations for routing emergency calls as outlined in Emergency Calling Overview. Contoso has offices outside of the United States with calling plan users and sites that are connected to Phone System via direct routing. Contoso needed a way to provide emergency calling to their Calling plan users in the United States, Calling plan users outside of the United states, and users at sites enabled for Direct Routing.  

Once the decision was made on how Contoso will connect to the Office 365 Phone system, Contoso identified the following Emergency calling use cases: 

- Calling Plan user in the United States 

- Calling Plan user outside of the United States 

- User who connects to Phone System through Direct Routing 


## Calling plan user in the United States  

There are requirements for when the phone number needs to be associated with an emergency location.  Contoso reviewed the Considerations for Calling plans that discusses the requirements.  Based on the requirements the below decisions were made.  

Decision: Contoso will associate the location with the telephone number when a number is assigned to a user in the United States  - - 

## Calling plan user outside of the United States 

There are requirements for when the phone number needs to be associated with an emergency location.  Contoso reviewed the Considerations for Calling plans that discusses the requirements.  Based on the requirements the below decisions were made.  

Decision: Contoso will associate the location with the telephone number when a number is assigned to a user in Canada 

Decision: Contoso will assign an emergency location when the phone number is acquired from Office 365 or when a number is transferred from another service provider or carrier 

## User that connect to the phone system with direct routing 

Contoso reviewed the Considerations for Direct Routing to plan for emergency routing for this use case. Since Direct Routing users do not receive emergency calling in the same manner as calling plan users, decisions need to be made on how to provide emergency calling.  There is the ability to have Direct Routing connected to an Emergency Routing Service Provider (ERSP) and also the ability to have a SBC that includes an Emergency Location Identification Number.   

### Emergency Routing Service Provider (ERSP) considerations

The Emergency Routing Service Providers (ERSPs) can automatically route emergency calls based upon the location of the caller.  

- If an Emergency Routing Service Provider is integrated into a Direct Routing deployment, emergency calls with a dynamically acquired location will be automatically routed to the Public Safety Answering Point (PSAP) serving that location. 

- Emergency calls without a dynamically acquired location are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center based upon the updated location. 
- 
- 
- From <https://docs.microsoft.com/en-us/MicrosoftTeams/what-are-emergency-locations-addresses-and-call-routing#considerations-for-direct-routing>  

### ELIN 

If an SBC ELIN application is integrated into a Direct Routing deployment, additional configuration steps need to occur to associate the emergency addresses with telephone numbers.  


Decision: Contoso will leverage Session Border Controllers that include Emergency Location Identification Number (ELIN) applications.  

### Security desk notification: 

The ability to notify the security desk when an emergency call is placed is available for both Microsoft Calling Plans and Phone System Direct Routing. Contoso reviewed the details in the Security desk notification to determine if this should be configured at their offices  

Decision: Contoso will use security desk notification 



## Configuration of ememrgency calling

Contoso followed the steps in Configure dynamic emergency calling to: 

- Assign emergency addresses 

- Configure network settings 

- Configure Location Information Service 

- Configure emergency policies 

- Enable users and sites 

- Test emergency calling 

Once the dynamic emergency calling is configured, it is necessary to assign the location to the appropriate user.  

Contoso followed the steps in Add, change, or remove and emergency location for your organization to create places for buildings, floors, and offices. 

Contoso followed the steps in Assign or change an emergency location for a user to assign an emergency location. 

 