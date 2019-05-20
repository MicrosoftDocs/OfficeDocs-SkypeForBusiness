---
title: "Deploy emergency services in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- IT_Skype16
- Strat_SB_Admin
ms.custom: 
ms.assetid: cc6a656a-6043-4b9b-85c2-5708b9bb1c06
description: "Deploy E9-1-1 in Skype for Business Server Enterprise Voice. Includes prerequisites and deployment process checklist."
---

# Deploy emergency services in Skype for Business Server
 
Deploy E9-1-1 in Skype for Business Server Enterprise Voice. Includes prerequisites and deployment process checklist.
  
Enhanced 9-1-1 (E9-1-1) is an emergency notification feature that associates the calling party's telephone number with a civic or a street address. Using this information, the Public Safety Answering Point (PSAP) can immediately dispatch emergency services to the caller in distress.
  
To support E9-1-1, Skype for Business Server must be able to correctly associate a location with a client and to make sure that this information is used to route the emergency call to the nearest PSAP.
  
## Deployment Prerequisites for E9-1-1

Before you deploy E9-1-1, you must already have deployed your Skype for Business Server internal servers, including a Central Management store, a Front End pool or a Standard Edition server. You must also deploy one or more Mediation Servers, either standalone or collocated with Front End Servers. In addition, an E9-1-1 deployment requires a SIP trunk to a qualified E9-1-1 service provider or an Emergency Location Identification Number (ELIN) gateway to your public switched telephone network (PSTN).
  
## Deployment Process

The following table provides an overview of the E9-1-1 deployment process.
  
|**Phase**|**Steps**|**Roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Configure voice usages, routes, and trunk configurations  <br/> |1. Create a new PSTN usage record. This is the same name that is used for the **PSTN Usage** setting in the location policy. <br/> 2. Create or assign a voice route to the PSTN usage record created in the previous step and then point the gateway attribute to the E9-1-1 SIP trunk or ELIN gateway.  <br/> 3. For a SIP trunk E9-1-1 service provider, set the trunk that will be handling E9-1-1 calls over the SIP to pass PIDF-LO data by using the **Set-CsTrunkConfiguration -EnablePIDFLOSupport** cmdlet. <br/> 4. Optionally, for a SIP trunk E9-1-1 service provider, create or assign a local PSTN route for calls that are not handled by the E9-1-1 service provider's SIP trunk. This route will be used if the connection to the E9-1-1 service provider is not available. If supported by your E9-1-1 service provider, assign a trunk configuration rule to the gateway that translates the 911 dial string into the direct inward dialing (DID) number of the national/regional Emergency Call Response Center (ECRC).  <br/> |CSVoiceAdmin  <br/> |[Configure an E9-1-1 voice route in Skype for Business Server](configure-an-e9-1-1-voice-route.md) <br/> |
|Create location policies and assign them to users and subnets  <br/> |1. Review the global location policy.  <br/> 2. Create a location policy with a user-level scope; or, if the organization has more than one site with different emergency usages, create a location policy with a network-level scope.  <br/> 3. Assign the location policy to network sites.  <br/> 4. Add the appropriate subnets to the network site.  <br/> 5. (Optional) Assign the location policy to user policies.  <br/> |CSVoiceAdmin  <br/> CSLocationAdmin (except for creating Location Policies)  <br/> |[Create location policies in Skype for Business Server](create-location-policies.md) <br/> [Add a location policy to a network site in Skype for Business Server](add-a-location-policy-to-a-network-site.md) <br/> [Associate a subnet with a network site](deploy-network.md#BKMK_AssociateSubnets) <br/> |
|Configure the location database  <br/> |1. Populate the database with a mapping of network elements to locations.  <br/> 2. For ELIN gateways, add the ELINs to the \<CompanyName\> column.  <br/> 3. Configure the connection to the E9-1-1 service provider for validating addresses.  <br/> 4. Validate the addresses with the E9-1-1 service provider.  <br/> 5. Publish the updated database.  <br/> 6. For ELIN gateways, upload the ELINs to your PSTN carrier's Automatic Location Identification (ALI) database.  <br/> |CSVoiceAdmin  <br/> CSLocationAdmin  <br/> |[Configure the location database in Skype for Business Server](configure-the-location-database.md) <br/> |
|Configure Advanced Features (optional)  <br/> |1. Configure the URL for the SNMP application.  <br/> 2. Configure the URL for the location of the Secondary Location Information service.  <br/> |CSVoiceAdmin  <br/> |[Configure an SNMP application in Skype for Business Server](configure-an-snmp-application.md) <br/> [Configure a secondary Location Information service in Skype for Business Server](secondary-location-information-service.md) <br/> |
   

