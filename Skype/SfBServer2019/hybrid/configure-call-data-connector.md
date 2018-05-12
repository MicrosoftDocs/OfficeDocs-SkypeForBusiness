---
title: "Configure call data connector"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for configuring the Call Data Connector feature, which allows telemetry from Skype for Business on-premises to be viewed using Skype for Business online tools."
---

# Configure call data connector

[!INCLUDE [disclaimer](../disclaimer.md)]

This article explains how to configure viewing Skype for Business server Call Quality Data using the Skype for Business Online Call Quality Dashboard.

For now, links to SFBOL and server 2015 content are provided as a reference while we determine what we can leverage from existing content and what we will need to create.

##  Server configuration

###  Configuring hybrid and other dependencies

**At this time we need clarification on which of the several flavors of hybrid are intended. Therefore this section is TBD** 

Is there a plan to support running CQD in parallel both online and onprem? 
Is there a required order? Could one perhaps set up Monitoring and CQD onprem first and then migrate the functionality to OL?


### Set up monitoring 

CQD onprem uses data produced when monitoring and Call Detail Recording is implemented, sending call data from FE servers to a Monitor server role (explained in onprem CQD doc), which has its call data replicated to a local SQL server and read by the CQD app. Assuming a dedicated monitoring server will be implemented onprem then the replication will instead be sent to a repository in Azure, we should be able to re-use or point to the steps provided in https://docs.microsoft.com/en-us/SkypeForBusiness/deploy/deploy-monitoring/deploy-monitoring

If the functions of a Monitoring Server will happen in the cloud, we'll need to understand which cmdlets or options set that up, or if setting that up happens in the updated Control Panel or Topology Builder.

### Set up Call Detail Recording 

This is already documented for onprem,  but this may be where the switch is thrown and our onprem data gets sent to CQD OL. My guess is  the CDR command Set-CsQoEConfiguration may have a new option that sends to SfBOL  https://docs.microsoft.com/en-us/SkypeForBusiness/deploy/deploy-monitoring/call-detail-recording-and-qoe  
   

Onprem CQD docs for reference
https://docs.microsoft.com/en-us/SkypeForBusiness/management-tools/call-quality-dashboard/deploy-0


## CQD Online

If we are supporting migration from onprem to hybrid users will need to turn on CQD online as described in  Https://docs.microsoft.com/en-us/SkypeForBusiness/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard

**Activation** as described there might or might not be the same as for pure SfBOL. 

Since CQD OL now covers Teams too, I'm guessing you toggle to onprem data views like you'd toggle to teams as described here: https://docs.microsoft.com/en-us/SkypeForBusiness/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard#selecting-product-data-to-see-in-reports 
