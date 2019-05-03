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

## Care Coordination - Microsoft Teams Patients app

[!INCLUDE [preview-feature](../includes/preview-feature.md)]

Microsoft Teams now has a care coordination solution specific to healthcare organizations to help them meet their ultimate goal of providing the best patient care. The crux of the care coordination solution, the  Microsoft Teams Patient App, is a first party tab app that integrates with electronic health record (EHR) systems using a Fast Healthcare Interoperability Resources ([FHIR](https://www.hl7.org/fhir/)) interface to bring valuable medical information into Microsoft Teams.  

The care coordination solution can interface with leading Independent Software Vendors (ISVs) that can connect the Patients App to your EHR systems using existing health data standards like HL7v2 and FHIR. Microsoft partners with the following industry leaders to establish electronic health record integration with Teams:

- Datica (through their [CMI](https://datica.com/compliant-managed-integration/) offering)
- Infor Cloverleaf (through the [Infor FHIR Bridge](https://pages.infor.com/hcl-infor-fhir-bridge-brochure.html))
- Redox (through the [R^FHIR server](https://www.redoxengine.com/fhir/))
- Dapasoft (through [Corolar on FHIR](https://www.dapasoft.com/corolar-fhir-server-for-microsoft-teams/))

An EHR integration and interop partner trying to implement Microsoft Teams for a healthcare provider organization needs to provide the Patients App a secure and authenticated connection with the healthcare provider organization's EHR systems. This enables the one-directional (Read only) flow of the relevant patient records into to the Microsoft Teams Patients App. The Microsoft Teams Patients App understands the FHIR format, so the partner is also responsible for transforming the aggregated data from various other formats like HL7v2, etc. into FHIR DSTU2 or STU3.

<br>

![EHR integration](../media/ehr-1.png)

<br>

The Patients app integrates with electronic health records (EHR) systems and enables care providers to communicate about patient care in real-time within Teams’ secure platform. The Patients app is the first major investment in the care coordination area which aims to address the following challenges:

- Low efficiency in hand-offs and critical communication through the patient experience
- Siloed information that creates administrative burdens
- Dissatisfaction among clinicians with complex and fragmented collaboration tools
- Inefficient in-person care coordination that can burn too much expensive clinical time

Microsoft Teams enables physicians, clinicians, nurses, and other staff to collaborate efficiently by:

- Being part of a single virtualized team that works and collaborates on Office documents
- Having persistent conversations about different patients needing attention
- Using channels with tabs as a way to structure their work, with additional help from tabs to which they can pin information sources
- Using channel meetings with the power of Teams audio, video, screen sharing, recording, and transcription features to manage daily meetings
- Using the Microsoft Teams Patient App to curate a list of high-risk patients that must be monitored, and pulls their latest details from the EHR system. The Microsoft Teams Patients App itself adds the following features to Microsoft Teams:

    - Ability to create multiple patient lists within a single channel.
    - Ability to view and sort information displayed about patients through configurable columns.
    - Ability to auto-provision the app through a team template.
    - Available on the Teams App for iOS and Android for mobile first healthcare workers as well as Microsoft Teams web and desktop client.
    - Support for FHIR DSTU2 and STU3 versions via parsing of conformance statement.
    - Audit Logs for all view and search actions on its user interface to safeguard PHI per HIPAA guidelines.

The Microsoft Teams Patients app is built on the Teams extensibility platform and takes advantage of the Tabs framework to display rich patient content within a channel. To learn more about other Teams apps and the platform itself, please see [Apps for Microsoft Teams](https://docs.microsoft.com/microsoftteams/platform/concepts/apps/apps-overview).  

> [!NOTE]
> The Microsoft Teams Patient App is in private preview and the FHIR interface is in beta. Released versions are not expected to be backward compatible.

![Patients app screenshot](../media/ehr-2.png)

See [Integrating Electronic Healthcare Records into Microsoft Teams](../../healthcare/patients-app.md) for implementation details,.

## Templates 

New templates for creating Teams were developed to apply to a Hospital setting, and more are expected soon. This makes it easier to create Teams that Healthcare workers use to coordinate care for patients in various departments or wards. See [Get started with Teams templates for Healthcare organizations](healthcare-templates.md). Teams can be started for internal departments such as cardiology, or for care wards, and more templates are in development.

## Secure Messaging

Secure messaging supports collaboration within care teams, including several new features:

- A message sender can set a special priority for their message, so the recipient is repeatedly notified until they read the message.
- A message sender can request a read receipt, so they are notified when a message they sent was read by the message recipient.

Together, these features allow quicker attention to urgent messages and confidence that the message was received and read. New care teams using these features can be created on a per-patient basis. These features are policy-based, and can be assigned to individuals or entire Teams.

See [Get started with Secure Messaging policies for Healthcare organizations](messaging-policies-hc.md) for further details.

## Firstline Worker integration

Microsoft Teams integrates with Firstline Worker, which can be used to coordinate shift staffing features and more.

 See the following articles:

- [Move your Microsoft StaffHub teams to Shifts in Microsoft Teams](../shifts/move-staffhub-teams-to-shifts-in-teams.md)

- [Manage the Shifts app for your organization in Microsoft Teams](../shifts/manage-the-shifts-app-for-your-organization-in-teams.md)
