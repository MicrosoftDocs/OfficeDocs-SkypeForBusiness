---
title: "Negotiation settings for XMPP federated partners in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ef773942-ef92-4f71-85a1-738dfebdfa00
description: "The settings for the negotiation types in the configuration of an XMPP Partner have a wide variety of possible combinations. Not all of these combinations are valid. The table detailed in this topic will define the valid and not valid settings. Common configurations are presented in the first table, the second table detailing all possible combinations. Note that you cannot have Simple Authentication and Security Layer (SASL) unlessTransport Layer Security (TLS) is also available. SASL is sent in an unencrypted (readable) format and should never be transmitted unless protected by another means, such as TLS."
---

# Negotiation settings for XMPP federated partners in Lync Server 2013
[]
The settings for the negotiation types in the configuration of an XMPP Partner have a wide variety of possible combinations. Not all of these combinations are valid. The table detailed in this topic will define the valid and not valid settings. Common configurations are presented in the first table, the second table detailing all possible combinations. Note that you cannot have Simple Authentication and Security Layer (SASL) **unless**Transport Layer Security (TLS) is also available. SASL is sent in an unencrypted (readable) format and should never be transmitted unless protected by another means, such as TLS. 
  
**Common XMPP Federation Negotiation Methods**

|**Transport Layer Security (TLS)**|**Simple Authentication and Security Layer (SASL)**|**Dialback Authentication**|**Expected Authentication Method(s)**|**Notes**|
|:-----|:-----|:-----|:-----|:-----|
|Required  <br/> |Required  <br/> |False  <br/> |SASL over TLS  <br/> |TLS and SASL required helps to ensure that the SASL message stream is secure. Dialback is not available and cannot be used for a fallback method if the XMPP federated partner has not set TLS to required or optional.  <br/> |
|Required  <br/> |Optional  <br/> |True  <br/> |SASL over TLS, TLS Dialback, TCP Dialback  <br/> |By requiring TLS, if the XMPP federated partner has set SASL to optional or required SASL is used. If SASL is not available, Dialback over TLS will be used.  <br/> |
|Optional  <br/> |Optional  <br/> |True  <br/> |SASL over TLS, TLS Dialback, TCP Dialback  <br/> |While very flexible in the negotiation methods offered, these settings rely on the XMPP federation partner's settings. If the partner has TLS optional or required but SASL is not supported, TLS Dialback will be available. If the partner has TLS and SASL set to optional or required, the optimal selection of TLS over SASL is used.  <br/> |
|Not Supported  <br/> |Not Supported  <br/> |True  <br/> |TCP Dialback  <br/> |In many cases, TCP Dialback is the only possible solution. Less desirable than other options, it does provide some level of trust.  <br/> |
   
**XMPP Federation Negotiation Methods Matrix - Complete**

|**Transport Layer Security (TLS)**|**Simple Authentication and Security Layer (SASL)**|**Dialback Authentication**|**Expected Authentication Method**|**Notes, Warning or Error for Not Valid Configuration**|
|:-----|:-----|:-----|:-----|:-----|
|Required  <br/> |Required  <br/> |True  <br/> |SASL over TLS  <br/> |
> [!CAUTION]
> Dialback will not operate if both SASL and TLS are required. 
  
|
|Required  <br/> |Required  <br/> |False  <br/> |SASL over TLS  <br/> ||
|Optional  <br/> |Required  <br/> |True  <br/> |SASL over TLS, TLS Dialback, TCP Dialback  <br/> |
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Optional  <br/> |Required  <br/> |False  <br/> |SASL over TLS  <br/> |
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Not Supported  <br/> |Required  <br/> |True  <br/> |TCP Dialback  <br/> |
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Not Supported  <br/> |Required  <br/> |False  <br/> |
> [!CAUTION]
> Not Valid Configuration 
  
|
> [!CAUTION]
> Because SASL requires TLS, and TLS is not available, SASL/TLS cannot succeed. TCP Dialback is set to false, and cannot be used. 
  
|
|Required  <br/> |Optional  <br/> |True  <br/> |SASL over TLS, TLS Dialback  <br/> ||
|Required  <br/> |Optional  <br/> |False  <br/> |SASL over TLS  <br/> ||
|Optional  <br/> |Optional  <br/> |True  <br/> |SASL over TLS, TLS Dialback, TCP Dialback  <br/> |
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Optional  <br/> |Optional  <br/> |False  <br/> |SASL over TLS  <br/> |
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Not Supported  <br/> |Optional  <br/> |True  <br/> |TCP Dialback  <br/> |
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Not Supported  <br/> |Optional  <br/> |False  <br/> |
> [!CAUTION]
> Not Valid Configuration 
  
|
> [!CAUTION]
> SASL requires TLS. Allowing TLS to be optional may result in failed session negotiations. 
  
|
|Required  <br/> |Not Supported  <br/> |True  <br/> |TLS Dialback  <br/> |Configuration allows for TLS Dialback.  <br/> |
|Required  <br/> |Not Supported  <br/> |False  <br/> |Not Valid Configuration  <br/> |
> [!CAUTION]
> SASL or Dialback must be enabled. 
  
|
|Optional  <br/> |Not Supported  <br/> |True  <br/> |TLS Dialback, TCP Dialback  <br/> |Based on negotiation choices of the other end point, TCP or TLS Dialback will be accepted.  <br/> |
|Optional  <br/> |Not Supported  <br/> |False  <br/> |Not Valid Configuration  <br/> |
> [!CAUTION]
> SASL or Dialback must be enabled. 
  
|
|Not Supported  <br/> |Not Supported  <br/> |True  <br/> |TCP Dialback  <br/> |TCP Dialback is the only negotiation method available  <br/> |
|Not Supported  <br/> |Not Supported  <br/> |False  <br/> |Not Valid Configuration  <br/> |
> [!CAUTION]
> SASL or Dialback must be enabled. 
  
|
   

