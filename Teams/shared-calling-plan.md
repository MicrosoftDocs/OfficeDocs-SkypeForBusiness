---
title: "Plan for Shared Calling"
ms.reviewer: jenstr
ms.date: 09/19/2023
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
ms.custom: 
  - Phone System
description: "In this article, you'll learn about Teams Phone Shared Calling."
---

# Plan for Shared Calling

This article describes what you need to know before configuring Shared Calling for Teams Phone.

If you have users who aren't heavy users of the Public Switched Telephone Network (PSTN), they might not need a dedicated assigned phone number. Instead, for these users, you should consider Shared Calling as a simpler, easier-to-implement phone solution for you organization. Shared Calling greatly simplifies phone number management for some users. Shared Calling also reduces costs for your organization because you don't need a dedicated phone number for every user.

Let's start with some definitions that you'll need to know for Shared Calling:

| Term | Definition |
|----------|-----------|
|Auto attendant|Directs a caller to an appropriate person or department based on the caller's input to the provided menu options; for example. dial by name or dial by extension. The Auto attendant phone number used is specified by the resource account associated with the Auto attendant.<br><br>For more information about using Auto attendants, see [Plan for Auto attendants](plan-auto-attendant-call-queue.md) and [Set up Auto attendants](create-a-phone-system-auto-attendant.md).|
|Inbound calls|An incoming call that comes from a PSTN to a user in your organization. When a Shared Calling user receives an inbound PSTN call, the call connects to the Auto attendant.|
|Outbound calls|An outgoing call by a user in your organization to a PSTN. When a Shared Calling user makes an outbound call to the PSTN, the recipients see the caller ID of the Auto attendant.|

With Shared Calling, instead of assigning a phone number to every user, you use the phone number of an Auto attendant for outbound and inbound PSTN calls. The Shared Calling routing policy configures the resource account used for outbound calls and emergency numbers that will be used as emergency callback numbers.

To set up Shared Calling, you'll need to perform the following steps.  These steps are described in detail in [Configure Shared Calling](shared-calling-setup.md). 

1. Assign Teams Phone licenses and enable users for voice. 

2. Assign number to resource account for outbound calling. 

3. Associate resource account with Auto attendant for inbound calling. 

4. Assign Pay-As-You-Go Calling Plan to Calling Plan service number. 

5. Assign and fund a Communication credits license. 

6. Create voice routing policy without PSTN usages. 

7. Enable emergency calling for users. 

8. Create your Shared Callig policy.  

You must have Teams PowerShell Module version 5.5.0 or higher to use the new TeamsSharedCallingRoutingPolicy cmdlets. You'll use these cmdlets to create and manage Shared Calling policies. 


## Related topics

- [Configure Shared Calling](shared-calling-setup.md)
- [Shared Calling example scenario](shared-calling-scenario.md)
- [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md)
- [Set up Auto attendants](create-a-phone-system-auto-attendant.md)
- [Manage resource accounts](manage-resource-accounts.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
