---
title: Cortana voice assistant in Microsoft Teams
author: cichur
ms.author: v-cichur
manager: serdars
ms.topic: conceptual
ms.service: msteams
audience: admin
ms.reviewer: akshbhat
search.appverid: MET150
description: Learn how to use Cortana voice assistant with Teams
localization_priority: Normal
ms.custom: 
- Teams-upgrade-guidance
- seo-marvel-mar2020
f1.keywords:
- NOCSH
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Cortana voice assistance in Teams 

Cortana voice assistance in the Teams mobile app helps users simply perform communication, collaboration, and meeting-related tasks using spoken natural language. Users can speak to Cortana by clicking on the microphone button located in the upper right of the Teams mobile app. They can connect with someone while on the go by making a voice query such as “call Megan” or “send a message to my next meeting.” Users can also join meetings by saying “join my next meeting.” Cortana in Teams meets the same enterprise-level privacy, security, and compliance promises as reflected in the [Online Services Terms (OST)](https://www.microsoft.com/licensing/product-licensing/products?rtc=1).  

## Admin control 

Admins can control who in their tenant can use Cortana voice assistance in Teams using a policy (TeamsCortanaPolicy). This policy can be set at either a user account level or tenant level. Admins can also use the CortanaVoiceInvocationMode field within this policy control to determine whether Cortana is enabled with push button invocation only, or with wake word invocation as well (applicable to devices that support it). Note that at the time of the initial release for Microsoft 365 Enterprise users in the US in English, the Teams mobile app will not support wake word activation, but it will be supported in the future. 

## User control 

Individual users can try out Cortana voice assistance in the Teams mobile app by clicking on the microphone button. They can also control whether Cortana in Teams is enabled for their device via a setting in the Teams mobile app. 

1. Open the Teams mobile app. 

2. Go to **Settings**. 

3. Select **Cortana**. 

4. Move the toggle to **On** or **Off**, depending on whether you want Cortana voice assistance on this device. 
