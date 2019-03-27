---
title: "Get started with Teams for Healthcare organizations"
author: jambirk
ms.author: jambirk 
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: 
description: Get started with Teams for Healthcare organizations
---

# Get started with Teams for Healthcare organizations

Microsoft Teams offers a number of features useful for hospitals and other Healthcare organizations. Teams features are under development to aid hospitals with:

- Care Coordination
- Secure Messaging
- Electronic Healthcare Record (EHR) integration
- Firstline Worker integration

## Care Coordination

Care coordination is one of the key pillars for our investments in Microsoft Teams in healthcare. The solution gives healthcare teams a secure hub for coordinating care across multiple patients. It integrates with electronic health records (EHR) systems and enables care providers to communicate about patient care in real-time within Teams’ secure platform. Teams allows organizations to address problems like:

- Low efficiency in hand-offs and critical communication throughout the care continuum
- Siloed information that creates administrative burden in the healthcare system
- Dissatisfaction among clinicians with complex and fragmented collaboration tools
- Inefficient and in-person coordination among professionals that can consume too much clinical time and cost

New templates for creating Teams were developed to apply to a Hospital setting, and more are expected soon. This makes it easier to create Teams that Healthcare workers use to coordinate care for patients in various departments or wards. See [Get started with Teams templates for Healthcare organizations](healthcare-templates.md). Teams can be started for internal departments such as cardiology, or for care wards, and more templates are in development.

## Secure Messaging

Secure messaging supports collaboration within care teams, including several new features:

- A message sender can set a special priority for their message, so the recipient is repeatedly notified until they read the message.
- A message sender can request a read receipt, so they are notified when a message they sent was read by the message recipient.

Together, these features allow quicker attention to urgent messages and confidence that the message was received and read. New care teams using these features can be created on a per-patient basis. These features are policy-based, and can be assigned to individuals or entire Teams.

See [Get started with Secure Messaging policies for Healthcare organizations](messaging-policies-hc.md) for further details.

## EHR integration

Electronic health information records integration using [FHIR](https://www.hl7.org/fhir/overview.html) (Fast Healthcare Interoperability Resources) will be enabled using Teams Templates. The feature is not yet in general release.

The care coordination solution in Microsoft Teams involves a first party tab app that integrates with electronic health record (EHR) systems via an FHIR interface to bring medical information from record systems into Microsoft Teams. This helps clinical workers access crucial patient information and communicate among themselves to optimize patient care. One of the key challenges to achieving coordinated care is the lack of interoperability between electronic systems in healthcare. Enabling interoperability through an industry backed standard like FHIR enables clinicians to have the best information available at the point of care when making diagnosis and treatment decisions.

The health records solution depends on partnerships with leading healthcare Independent Software Vendors (ISVs) that can connect Teams to a Healthcare provider's EHR systems based on industry-wide data standards. Microsoft has working partnerships with the following healthcare partners to establish electronic health record integration: 
- [Datica](https://datica.com/compliant-managed-integration/) (CMI offering)
- [Infor Cloverleaf](https://pages.infor.com/hcl-infor-fhir-bridge-brochure.html)  (Info FHIR Bridge)
- [Redox](https://www.redoxengine.com/fhir/) (R^FHIR server)
- [Dapasoft](https://www.dapasoft.com/corolar-fhir-server-for-microsoft-teams/) (Corolar on FHIR)

The **HL7 Fast Healthcare Interoperability Resources (FHIR) standard** is rapidly gaining support in the healthcare community as the next generation standards framework for interoperability. HL7 FHIR is rapidly gaining support in the healthcare community as the next generation standards framework for interoperability, and it’s clear why. FHIR is an extensible and modern standard based on a web-based APIs including HTTPS and RESTful protocols.

Today, the 1st party app (which sits in the general channel of a Team as a tab app) lets a care team – doctors, physician assistants, nurses, social workers, dietitians, case managers and more in a hospital unit or ward create lists of patients that they want to monitor to coordinate care.

The app has an underlying service layer with an operational FHIR client interface that can query relevant patient medical information, connected to underlying EHR systems deployed within a provider organization. Listed below are some of its key features: 

- Ability to fetch latest patient data from the EHR systems
- Ability to create multiple patient lists within a single channel. 
- Ability to view and sort information displayed about patients through configurable columns. 
- Ability to auto-provision the application through a team template. 
- Available on the Teams App for iOS and Android for mobile first healthcare workers. 
- Support for FHIR DSTU2 and STU3 versions via parsing of conformance statement.

Teams aligns with the FHIR open source community by using an open source and community-maintained FHIR parser library from GitHub as a key component of our code base. The Microsoft Teams FHIR implementation is also aligned with Project Argonaut (and follows the US Core Profiles) for all FHIR resources.

Microsoft Teams is Tier D compliant per the Office 365 compliance framework and supports the HITRUST CSF and HIPAA BAA (business associate agreement) which allows a covered entity to sign a BAA  per Microsoft Volume licensing and Online service Terms. Microsoft Teams can be used to store and share ePHI data.

The data Teams pulls from EHR systems is not stored at REST. Also, there are 11 events for read actions performed by clinical users inside the Microsoft Teams care coordination solution that show up in Security and Compliance audit logs.

<!-- most of the above is snipped from https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Integrate-electronic-health-records-into-Microsoft-Teams-care/ba-p/334042 -->

## Firstline Worker integration

Microsoft Teams integrates with Firstline Worker, which can be used to coordinate shift staffing and more features. 

<!-- See the following articles:

- [Get started with Microsoft Teams Firstline Worker in Healthcare settings](../teams-for-firstline-workers/firstline-healthcare.md)
- [Microsoft Teams for firstline workers](../teams-for-firstline-workers/teams-for-firstline-workers.md)  -->
