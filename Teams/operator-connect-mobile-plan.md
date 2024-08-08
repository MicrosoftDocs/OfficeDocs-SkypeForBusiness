---
title: Plan for Teams Phone Mobile
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.date: 07/08/2024
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
ms.reviewer: crowe
search.appverid: MET150

description: Learn more about Teams Phone Mobile, such as requirements and planning for deployment.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Plan for Teams Phone Mobile

This article is for administrators and IT professionals who are evaluating Teams Phone Mobile. This article describes Teams Phone Mobile benefits and requirements.

Teams Phone Mobile is another option for providing Public Switched Telephone Network (PSTN) connectivity with Microsoft Teams Phone. With Teams Phone Mobile, a user’s SIM-enabled phone number is also their Teams phone number. The users in your organization can use a single phone number in Microsoft Teams across both their mobile service and desk lines, and seamlessly transition between networks and devices.

For a list of operators participating in the Microsoft Teams Phone Mobile program and the countries or regions where their service is available, see [Microsoft 365 Teams Phone Mobile](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/teams-phone-mobile).

Teams Phone Mobile can play a key role in your organization's strategy to enable a mobile workforce, providing more flexible and efficient mobile-centric user experiences along with enterprise-grade security and compliance settings.

You might consider a combination of voice services. For example, you might choose Teams Phone Mobile for your sales and field organizations that require mobile support, but another solution for your onsite call center organization that relies on desk phones. For more information about Teams voice solutions and PSTN connectivity options, see [Plan your Teams voice solution](cloud-voice-landing-page.md) and [PSTN connectivity options](pstn-connectivity.md). 

 Teams Phone Mobile might be the right solution for your organization if:

-	You want to use a primary company-owned, SIM-enabled mobile number for Teams Phone as a single number solution.

-	Your preferred operator is a participant in the Microsoft Teams Phone Mobile program.

-	You want to find a new operator to enable calling in Teams.

If you decide Teams Phone Mobile is the right solution for your organization, after reading this article, see [Configure Teams Phone Mobile](operator-connect-mobile-configure.md).


## Benefits

If your existing operator is a participant in the Teams Phone Mobile program, they can manage the service for bringing PSTN calling to Teams. The Teams Phone Mobile program provides the following benefits for your organization:

- **Users have one business-provided number for mobile, desk, and Microsoft Teams**. Users can work flexibly and securely from any location, device, or network.  

- **Improve availability and responsiveness of employees.** Provides reliable communication solutions with failover options using cellular voice network or internet connections. Users can seamlessly move between devices and Teams endpoints without dropping calls or losing context.

- **Opportunities to streamline support and eliminate redundant services.** Your organization can consolidate redundant fixed-line and mobile services, as well as reduce the number of devices and hardware to purchase, manage, and support.

-	**Security, privacy  and compliance capabilities of Teams.** Your organization can extend enterprise-grade business policies such as recording and retention to voice calls on native mobile devices. Calls from users’ devices can also be configured to appear as though they’re coming from the organization to avoid exposing users’ mobile numbers externally.

- **The power of Teams.** Users can seamlessly “uplift” calls to Teams on any device (laptop, tablet, desk phone or mobile phone) thereby creating valuable opportunities to collaborate by adding video, sharing content, recording and transcription, inviting new participants, and more.

- **True mobile integration.** Users have access to combined call history, unified voice mail, and presence across Teams and native mobile devices. 

## Features

Teams Phone Mobile users can leverage existing [Teams Phone features](here-s-what-you-get-with-phone-system.md), as well as the following:

- **SIM-enabled phone number calling with Teams**. Users can make and receive calls from their smartphone’s native dialer or Teams endpoints using a single business owned SIM-enabled mobile number. When users make an outbound call from their Smartphone’s native dialer or any Teams endpoint, they can show either their mobile or a company service number. Incoming calls ring the smartphone native dialer and simultaneously ring active Teams clients.

-	**Move calls between devices and endpoints**. Users can seamlessly move a call from their smartphone native dialer to any Teams endpoint without dropping the call. Users can move calls from the native dialer to the Teams app on the same device as well as endpoint transfer to another device with Teams. 

- **Access to compliance recordings** available for native dialer and Teams app calls. (If your organization has the required subscriptions and services).

- **Ability to add a SIM-enabled mobile number** as part of the companies’ Teams Phone Call Queues and PBX.

- **Ability to show a mobile number or company’s advertised number as outbound caller ID** when making outbound calls from the smartphone’s native dialer or any Teams endpoint.

- **Ability to transfer calls to colleagues** for further assistance using Teams app. Users can choose between blind and consultative call transfers. 

- **Combined called history in Teams** (irrespective of Teams or phone dialer).

- **Presence integration.**  If the user is on a call on the native dialer, their status in Teams will update to “In the Call”. 

- **Unified Voicemail and business unanswered settings** on all Teams endpoints and email with business enforced archival periods.

- **Ability to select whether incoming calls ring the native dialer or the Teams app** on the SIM-enabled mobile device.

## Licenses and requirements

Ensure your organization has the following Microsoft 365 services:

- Teams Phone SKU or E5 with Teams

To enable phone number assignments with Teams Phone Mobile, make sure your users:

- Have Teams Phone licenses. To learn more, see [What is Phone System?](what-is-phone-system-in-office-365.md) and [Assign Teams add-on licenses to users](teams-add-on-licensing/assign-teams-add-on-licenses.md).

- Have an eligible mobile subscription with your preferred operator that supports their SIM-enabled phone number to be used for Teams Phone. Your operator will upload the phone numbers to your Microsoft 365 tenant.

- Are in TeamsOnly mode. Users must be in TeamsOnly mode, but your entire organization does not. To learn more, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md).


## Related articles

For administrators:

- [Configure Teams Phone Mobile](operator-connect-mobile-configure.md)
- [Manage phone numbers for Teams Phone Mobile](operator-connect-mobile-configure-numbers.md)

For users in your organization:

- [Get started with Teams Phone Mobile](https://prod.support.services.microsoft.com/en-us/office/getting-started-with-teams-phone-mobile-c37a6764-6c4f-4685-a26f-b84c12a71697)
- [Manage call settings in Teams Phone Mobile](https://prod.support.services.microsoft.com/en-us/office/manage-call-settings-in-microsoft-teams-phone-mobile-dbe4098a-198f-4101-b769-ecf0da9b33e2)
