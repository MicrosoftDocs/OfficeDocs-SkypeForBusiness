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

# Configure Call Data Connector

[!INCLUDE [disclaimer](../disclaimer.md)]

This article explains how to configure viewing Skype for Business server Call Quality Data using the Skype for Business Online Call Quality Dashboard. This configuration is primarily done using a wizard built into the Skype for Business Server Control Panel.

To perform these tasks, you will need to be authenticated to your Office 365 Tenant and be a Server Admin for Skype for Business Server and also A Global Administrator is Office 365.


##  Server configuration

### Set up monitoring 

Follow the steps provided in https://docs.microsoft.com/en-us/SkypeForBusiness/deploy/deploy-monitoring/deploy-monitoring
to configure both Call Detail Recording and Quality of Experience, or run the following commands from within the Skype for Business Server Management Shell:

```
Set-CsCdrConfiguration -Identity "global" -EnableCDR $True
Set-CsQoEConfiguration -Identity "global" -EnableQoE $True
```


###  Configuring hybrid and other dependencies

Call Data Connector requires the following Hybrid connection:
- Edge server federation is enabled 
- Federation between Skype for Business Server and Office 365 is established
- Office 365 federation enabled
- A shared SIP address space for Skype for Business Server and Office  365 is configured.

once all these are set up, 

**So the Hybrid wizard enables Data Connector, it's a single option in a longer process.**



## CQD Online

If we are supporting migration from onprem to hybrid users will need to turn on CQD online as described in  Https://docs.microsoft.com/en-us/SkypeForBusiness/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard

**Activation** as described there might or might not be the same as for pure SfBOL. 

Since CQD OL now covers Teams too, I'm guessing you toggle to onprem data views like you'd toggle to teams as described here: https://docs.microsoft.com/en-us/SkypeForBusiness/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard#selecting-product-data-to-see-in-reports 
