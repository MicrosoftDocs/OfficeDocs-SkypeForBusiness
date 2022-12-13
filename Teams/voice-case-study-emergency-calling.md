---
title: 'Teams voice Contoso case study: Emergency calling'
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 06/17/2020
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: jowrig
search.appverid: MET150
f1.keywords:
- NOCSH
description: 'Teams voice case study for multi-national corporation : Emergency calling'
appliesto: 
  - Microsoft Teams
---


# Contoso case study: Emergency calling

To understand the availability of emergency calling and terminology related to emergency calling&mdash;Emergency Address, Place, Emergency Location, and Registered address&mdash;Contoso reviewed [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

In Office 365, a Calling Plan user is automatically enabled for emergency calling. But only Calling Plan users in the United States can use dynamic locations for routing emergency calls. 

For Direct Routing, Contoso learned that additional configuration is required for routing emergency calls and possibly for partner connectivity. The administrator must configure connection to an Emergency Routing Service Provider (ERSP) (United States) OR configure the Session Border Controller (SBC) for an Emergency Location Identification Number (ELIN) application.

Contoso has offices in the United States and outside of the United States:

- In the United States, Contoso Calling Plan users can use dynamic locations for routing emergency calls. 

- Outside of the United States, Contoso has some sites that use Calling Plans and some sites that are connected to Phone System through Direct Routing.

## Emergency calling use cases

After deciding how Contoso will connect to Phone system, Contoso identified the following Emergency calling use cases: 

- [Calling Plan user in the United States](#calling-plan-user-in-the-united-states) 

- [Calling Plan user outside of the United States](#calling-plan-user-outside-of-the-united-states)

- [User who connects to Phone System through Direct Routing](#user-who-connects-to-phone-system-through-direct-routing )


### Calling Plan user in the United States  

There are requirements for when the phone number needs to be associated with an emergency location. To understand these requirements, Contoso reviewed [Considerations for Calling Plans](what-are-emergency-locations-addresses-and-call-routing.md#considerations-for-calling-plans). 

Based on these requirements, Contoso decided to associate the location with the telephone number when a number is assigned to a user in the United States.

### Calling Plan user outside of the United States 

To understand when a phone number needs to be associated with an emergency location, Contoso reviewed  [Considerations for Calling Plans](what-are-emergency-locations-addresses-and-call-routing.md#considerations-for-calling-plans). Based on the requirements, Contoso decided the following:  

-  Contoso will associate the location with the telephone number when a number is assigned to a user in Canada. 

- Contoso will assign an emergency location when the phone number is acquired from Office 365 or when a number is transferred from another service provider or carrier. 

### User who connects to Phone System through Direct Routing 

To plan for emergency routing for this use case, Contoso reviewed [Considerations for Direct Routing](what-are-emergency-locations-addresses-and-call-routing.md#considerations-for-direct-routing). Because Direct Routing users do not receive emergency calling in the same manner as Calling Plan users, Contoso had to decide on how to provide emergency calling. Direct Routing can be connected to an Emergency Routing Service Provider (ERSP). Direct Routing can also have an SBC that includes an Emergency Location Identification Number (ELIN).   

#### Emergency Routing Service Provider (ERSP) considerations

The Emergency Routing Service Providers (ERSPs) can automatically route emergency calls based upon the location of the caller.  

- If an Emergency Routing Service Provider is integrated into a Direct Routing deployment, emergency calls with a dynamically acquired location will be automatically routed to the Public Safety Answering Point (PSAP) serving that location. 

- Emergency calls without a dynamically acquired location are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center based upon the updated location. 


#### ELIN considerations

If an SBC ELIN application is integrated into a Direct Routing deployment, additional configuration steps need to occur to associate the emergency addresses with telephone numbers.  

Contoso decided to use Session Border Controllers that include Emergency Location Identification Number (ELIN) applications.  

## Security desk notification

The ability to notify the security desk when an emergency call is placed is available for both Microsoft Calling Plans and Phone System Direct Routing. Contoso reviewed the details in the Security desk notification to determine if this should be configured at their offices  

Contoso decided to use security desk notification.

## Configuration 

Contoso followed the steps in [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md) to: 

- Assign emergency addresses 

- Configure network settings 

- Configure Location Information Service 

- Configure emergency policies 

- Enable users and sites 

- Test emergency calling 

After dynamic emergency calling is configured, Contoso needed to assign the location to the appropriate user.  

- To add, change, or remove an emergency location for your organization, Contoso followed the steps in [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)

- To create places for buildings, floors, and offices, Contoso followed the steps in [Add, change, or remove a place for an emergency location](add-change-remove-emergency-place-organization.md) . 

- To assign an emergency location, Contoso followed the steps in [Assign or change an emergency location for a user](assign-change-emergency-location-user.md). 

 
