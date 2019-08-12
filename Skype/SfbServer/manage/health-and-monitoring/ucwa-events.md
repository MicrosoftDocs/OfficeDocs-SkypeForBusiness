---
title: "UCWA events in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 26cb409d-f4e4-43c7-873f-b694702d491d
description: "Summary: Learn about the Unified Communications Web API (UCWA) in Skype for Business Server."
---

# UCWA events in Skype for Business Server
 
**Summary:** Learn about the Unified Communications Web API (UCWA) in Skype for Business Server.
  
Skype for Business Server uses the Unified Communications Web API (UCWA) for a number of purposes, from accessing Microsoft Exchange for contact searches to updating presence for mobile clients.
  
UCWA will write records of operational behavior as event types Informational, Warning, and Error. The following table describes the events that can be written by the UCWA components.
  
|**Event ID**|**Event type**|**Summary**|**Cause and resolution**|
|:-----|:-----|:-----|:-----|
|20001  <br/> |Informational  <br/> |UCWA initialized  <br/> |N/A  <br/> N/A  <br/> |
|20002  <br/> |Error  <br/> |UCWA encountered an unexpected exception during initialization  <br/> |An unexpected error has occurred during initialization  <br/> Examine the exception details in the associated event log entry to determine the possible cause  <br/> |
|20003  <br/> |Error  <br/> |UCWA encountered an unhandled exception  <br/> |An unhandled exception happened  <br/> Restart the server. If the problem persists contact product support  <br/> |
|20004  <br/> |Error  <br/> |Cannot access Exchange for HD photo  <br/> |Connection to Exchange is not available  <br/> Make sure the connection to Exchange is available  <br/> |
|20005  <br/> |Informational  <br/> |Recovered from failing to access Exchange for HD photo  <br/> |N/A  <br/> |
|20006  <br/> |Error  <br/> |Cannot access Exchange for contact search  <br/> |Connection to Exchange is not available  <br/> Make sure the connection to Exchange is available  <br/> |
|20007  <br/> |Informational  <br/> |Recovered from failing to search contact in Exchange  <br/> |N/A  <br/> |
|20008  <br/> |Warning  <br/> |Attempt to subscribe more than the allowed presence subscriptions per application  <br/> |Attempt to subscribe more than the allowed presence subscriptions per application  <br/> Check the clients for unnecessary subscriptions  <br/> |
|20009  <br/> |Warning  <br/> |Attempt to subscribe more than the allowed presence subscriptions per batch  <br/> |Attempt to subscribe more than the allowed presence subscriptions per batch  <br/> Check the clients for unnecessary subscriptions  <br/> |
|20010  <br/> |Error  <br/> |Cannot retrieve inband data  <br/> |Cannot retrieve inband data  <br/> If the problem persists contact product support  <br/> |
|20011  <br/> |Error  <br/> |Cannot subscribe presence  <br/> |Cannot subscribe presence  <br/> If the problem persists contact product support  <br/> |
|20012  <br/> |Error  <br/> |Failed to register endpoint  <br/> |Failed to register endpoint  <br/> If the problem persists contact product support  <br/> |
|20013  <br/> |Error  <br/> |IM MCU is unavailable  <br/> |IM MCU is unavailable  <br/> See whether IM MCU is running  <br/> |
|20014  <br/> |Informational  <br/> |Recovered from failing to connect to IM MCU  <br/> |N/A  <br/> |
|20015  <br/> |Error  <br/> |AV MCU is unavailable  <br/> |AV MCU is unavailable  <br/> See whether AV MCU is running  <br/> |
|20016  <br/> |Informational  <br/> |Recovered from failing to connect to AV MCU  <br/> |N/A  <br/> |
|20017  <br/> |Error  <br/> |AS MCU is unavailable  <br/> |AS MCU is unavailable  <br/> See whether AS MCU is running  <br/> |
|20018  <br/> |Informational  <br/> |Recovered from failing to connect to AS MCU  <br/> |N/A  <br/> |
|20019  <br/> |Error  <br/> |Data MCU is unavailable  <br/> |Data MCU is unavailable  <br/> See whether Data MCU is running  <br/> |
|20020  <br/> |Informational  <br/> |Recovered from failing to connect to Data MCU  <br/> |N/A  <br/> |
|20021  <br/> |Error  <br/> |Cannot join IM MCU  <br/> |Cannot join IM MCU  <br/> See whether IM MCU is running  <br/> |
|20022  <br/> |Error  <br/> |Cannot join AV MCU  <br/> |Cannot join AV MCU  <br/> See whether AV MCU is running  <br/> |
|20023  <br/> |Error  <br/> |Cannot join AS MCU  <br/> |Cannot join AS MCU  <br/> See whether AS MCU is running  <br/> |
|20024  <br/> |Error  <br/> |Cannot join Data MCU  <br/> |Cannot join Data MCU  <br/> See whether Data MCU is running  <br/> |
|20025  <br/> |Error  <br/> |Cannot access active directory for photo  <br/> |Connection to active directory is not available  <br/> Make sure the connection to active directory is available  <br/> |
|20026  <br/> |Informational  <br/> |Recovered from failing to access active directory for photo  <br/> |N/A  <br/> |
|20027  <br/> |Warning  <br/> |Cannot deserialize  <br/> |Cannot deserialize  <br/> If the problem persists contact product support  <br/> |
   

