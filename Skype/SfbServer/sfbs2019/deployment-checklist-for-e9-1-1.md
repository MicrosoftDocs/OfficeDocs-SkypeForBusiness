---
title: "Deployment checklist for E9-1-1 in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: cc6a656a-6043-4b9b-85c2-5708b9bb1c06
description: "To plan effectively for Enhanced 9-1-1 (E9-1-1), be sure to include the following deployment requirements:"
---

# Deployment checklist for E9-1-1 in Lync Server 2013
[]
To plan effectively for Enhanced 9-1-1 (E9-1-1), be sure to include the following deployment requirements:
  
- Prerequisites for deploying E9-1-1.
    
- Steps that are required to deploy E9-1-1.
    
## Deployment Prerequisites for E9-1-1

Before you deploy E9-1-1, you must already have deployed your Lync Server internal servers, including a Central Management store, a Front End pool or a Standard Edition server, one or more Mediation Servers or Mediation Server pools, and Lync Server clients. In addition, an E9-1-1 deployment requires a SIP trunk to a qualified E9-1-1 service provider or an Emergency Location Identification Number (ELIN) gateway to your public switched telephone network (PSTN). Lync Server supports using E9-1-1 service providers only inside the United States.
  
## Deployment Process

The following table provides an overview of the E9-1-1 deployment process. For details about deployment steps, see [Configure Enhanced 9-1-1 in Lync Server 2013](configure-enhanced-9-1-1.md) in the Deployment documentation. 
  
|**Phase**|**Steps**|**Roles**|**Deployment documentation**|
|:-----|:-----|:-----|:-----|
|Configure voice usages, routes, and trunk configurations  <br/> | Create a new PSTN usage record. This is the same name that is used for the **PSTN Usage** setting in the location policy.  <br/>  Create or assign a voice route to the PSTN usage record created in the previous step and then point the gateway attribute to the E9-1-1 SIP trunk or ELIN gateway.  <br/>  For a SIP trunk E9-1-1 service provider, set the trunk that will be handling E9-1-1 calls over the SIP to pass PIDF-LO data by using the **Set-CsTrunkConfiguration -EnablePIDFLOSupport** cmdlet.  <br/>  Optionally, for a SIP trunk E9-1-1 service provider, create or assign a local PSTN route for calls that are not handled by the E9-1-1 service provider's SIP trunk. This route will be used if the connection to the E9-1-1 service provider is not available. If supported by your E9-1-1 service provider, assign a trunk configuration rule to the gateway that translates the 911 dial string into the direct inward dialing (DID) number of the national/regional Emergency Call Response Center (ECRC).  <br/> |CSVoiceAdmin  <br/> |[Configure an E9-1-1 voice route in Lync Server 2013](configure-an-e9-1-1-voice-route.md) <br/> |
|Create location policies and assign them to users and subnets  <br/> | Review the global location policy.  <br/>  Create a location policy with a user-level scope; or, if the organization has more than one site with different emergency usages, create a location policy with a network-level scope.  <br/>  Assign the location policy to network sites.  <br/>  Add the appropriate subnets to the network site.  <br/>  (Optional) Assign the location policy to user policies.  <br/> |CSVoiceAdmin  <br/> CSLocationAdmin (except for creating Location Policies)  <br/> |[Create location policies in Lync Server 2013](create-location-policies.md) <br/> [Add a location policy to a network site in Lync Server 2013](add-a-location-policy-to-a-network-site.md) <br/> [Associate subnets with network sites for E9-1-1 in Lync Server 2013](associate-subnets-with-network-sites-for-e9-1-1.md) <br/> |
|Configure the location database  <br/> | Populate the database with a mapping of network elements to locations.  <br/>  For ELIN gateways, add the ELINs to the \<CompanyName\> column.  <br/>  Configure the connection to the E9-1-1 service provider for validating addresses.  <br/>  Validate the addresses with the E9-1-1 service provider.  <br/>  Publish the updated database.  <br/>  For ELIN gateways, upload the ELINs to your PSTN carrier's Automatic Location Identification (ALI) database.  <br/> |CSVoiceAdmin  <br/> CSLocationAdmin  <br/> |[Configure the location database in Lync Server 2013](configure-the-location-database.md) <br/> |
|Configure Advanced Features (optional)  <br/> | Configure the URL for the SNMP application.  <br/>  Configure the URL for the location of the Secondary Location Information service.  <br/> |CSVoiceAdmin  <br/> |[Configure an SNMP application in Lync Server 2013](configure-an-snmp-application.md) <br/> [Configure a secondary Location Information service in Lync Server 2013](configure-a-secondary-location-information-service.md) <br/> |
   

