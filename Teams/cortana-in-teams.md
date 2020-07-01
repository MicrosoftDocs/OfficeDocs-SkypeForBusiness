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

> [!Note] Cortana voice assistance is supported on Microsoft Teams iOS and Android mobile apps in English only. It isn't currently available for GCC, GCC-High, DoD, EDU tenants. Expansion to additional languages and regions will happen as part of future releases.

Cortana voice assistance in the Teams mobile app enables Microsoft 365 Enterprise users to streamline communication, collaboration, and meeting-related tasks using spoken natural language. Users can speak to Cortana by clicking on the microphone button located in the upper right of the Teams mobile app. To quickly connect with their team while on the go, users can say queries such as “call Megan” or “send a message to my next meeting.” Users can also join meetings by saying “join my next meeting” and use voice assistance to share files, check their calendar, and more. These voice assistance experiences are delivered using [Cortana enterprise-grade services](https://docs.microsoft.com/en-us/microsoft-365/admin/misc/cortana-integration?view=o365-worldwide) that fully comply with Office 365’s privacy, security, and compliance promises as reflected in the [Online Services Terms (OST)](https://www.microsoft.com/en-us/licensing/product-licensing/products?rtc=1).

The image shows sending a chat in Cortana on a mobile device.

![Image shows a sequence of mobile screens showing a Cortana chat session](media/cortana-on-teams-mobile.png)

## Admin control and Limitations

Cortana voice assistance in Teams is delivered using services that fully comply with Office 365’s enterprise-level privacy, security, and compliance promises as reflected in the Online Services Terms (OST). The feature will be enabled by default for tenants. Tenant admins can control who in their tenant can use Cortana voice assistance in Teams using a policy (TeamsCortanaPolicy). This policy can be set at either a user account level or tenant level. Admins can use the CortanaVoiceInvocationMode field within this policy control to determine whether Cortana is disabled, enabled with push button invocation only, or with wake word invocation as well (applicable to devices that support it).

> [!Note] that at the time of the initial release for Microsoft 365 Enterprise users in the US in English, the Teams mobile app will not support wake word activation, but it will be supported in the future.

## User control

Individual users can try out Cortana voice assistance in the Teams mobile app by clicking the microphone button. They can also control whether Cortana in Teams is enabled for their device using a setting in the Teams mobile app.

1. Open the Teams mobile app.

2. Go to **Settings**.

3. Select **Cortana**.

4. Move the toggle to **On** or **Off**, depending on whether you want Cortana voice assistance on the device.
