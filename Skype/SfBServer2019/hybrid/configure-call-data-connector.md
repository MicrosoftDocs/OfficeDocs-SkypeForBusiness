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

This article explains how to configure viewing Skype for Business server call Quality Data using the Skype for Business Online Call Quality Dashboard.

##  Onprem config side

https://docs.microsoft.com/en-us/SkypeForBusiness/management-tools/call-quality-dashboard/deploy-0

**So I'm guessing maybe users need to implement hybrid, then set up their monitoring store and QoE DB in the cloud instead of onprem. Alternately, they have monitoring store/ QoE DB locally, but it is replicated in the cloud and read by CQD online. not clear on how to set up replication. Onprem CQD install process did that part for the user, I think.**

Set up monitoring: 
https://docs.microsoft.com/en-us/SkypeForBusiness/deploy/deploy-monitoring/deploy-monitoring

CDR command Set-CsQoEConfiguration may have a new option that sends to SfBOL  https://docs.microsoft.com/en-us/SkypeForBusiness/deploy/deploy-monitoring/call-detail-recording-and-qoe     


### Minimum Hybrid config steps - onprem side
 Preferably these steps are already called out elsewhere. Carolyn will likely know where. her plan topic should sort out what flavors of hybrid are in play


## CQD Online

https://docs.microsoft.com/en-us/SkypeForBusiness/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard

Activation should be the same as for SfBOL. Or is it?

Since this now covers Teams too, I'm guessing you toggle to onprem views like you'd toggle to teams as described here: https://docs.microsoft.com/en-us/SkypeForBusiness/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard#selecting-product-data-to-see-in-reports 

or is there something else going on?