---
title: "Get started with Teams for Healthcare organizations"
author: dstrome
ms.author: dstrome
manager: serdars
audience: ITPro
ms.topic: article
ms.service: msteams
search.appverid: MET150
f1.keywords:
- NOCSH
localization_priority: Normal
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Healthcare
appliesto: 
  - Microsoft Teams
ms.reviewer: 
description: Learn about features for health care that include care coordination, secure messaging, telehealth, EHR integration, and firstline worker system integration.
ms.custom: seo-marvel-apr2020
---

# Get started with Teams for Healthcare organizations

Microsoft Teams offers a number of features useful for hospitals and other Healthcare organizations. Teams features are under development to aid hospitals with:

- Care Coordination and collaboration
- Secure Messaging
- Telehealth
- Electronic Healthcare Record (EHR) integration 
- Firstline Worker system integration 

The content in this section builds on the foundational capabilities of Teams, such as meetings, calling, and messaging, and assumes that you've already deployed Teams in your organization. If you haven't yet rolled out Teams, start by reading [How to roll out Microsoft Teams](../../How-to-roll-out-teams.md).

## Care Coordination - Microsoft Teams Patients app

> [!IMPORTANT]
> **Effective  October 30, 2020, the Patients app will be deprecated and users will no longer be able to 
>install it from the Teams app store. We encourage you to start using the [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db) in Teams today.**
>
>Patients app data is stored in the group mailbox of the Office 365 group that backs the team. When the Patients app is retired, all data associated with it will be retained in this group but can no longer be accessed through the user interface. Current users can re-create their lists using the [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db).
>
>The [Lists app](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db) is pre-installed for all Teams users and is available as a tab in every team and channel. With Lists, care teams can create patient lists using the built-in Patients template, from scratch, or by importing data to Excel. To learn more about how to manage the Lists app in your organization, see [Manage the Lists app](../../manage-lists-app.md).

[!INCLUDE [preview-feature](../../includes/preview-feature.md)]

Microsoft Teams now has a care coordination solution specific to healthcare organizations to help them provide the best patient care. The crux of the care coordination solution, the  Microsoft Teams Patients app, is a first party tab app that integrates with electronic health record (EHR) systems using a Fast Healthcare Interoperability Resources ([FHIR](https://www.hl7.org/fhir/)) interface to bring valuable medical information into Microsoft Teams in context to enable clinical collaboration and communication.  

The care coordination solution can interface with leading Independent Software Vendors (ISVs) that can connect the Patients app to your EHR systems using existing health data standards like HL7v2 and FHIR. Microsoft partners with the following industry leaders to establish electronic health record integration with Teams:

- Datica (through their [CMI](https://datica.com/compliant-managed-integration/) offering)
- Infor Cloverleaf (through the [Infor FHIR Bridge](https://pages.infor.com/hcl-infor-fhir-bridge-brochure.html))
- Redox (through the [R^FHIR server](https://www.redoxengine.com/fhir/))
- Dapasoft (through [Corolar on FHIR](https://www.dapasoft.com/corolar-fhir-server-for-microsoft-teams/))

An EHR integration and interop partner trying to implement Microsoft Teams for a healthcare provider organization needs to provide the Patients app a secure and authenticated connection with the healthcare provider organization's EHR systems. This enables the one-directional (Read only) flow of the relevant patient records into to the Patients app. The Patients app understands the FHIR format, so the partner is also responsible for transforming the aggregated data from various other formats like HL7v2, etc. into FHIR DSTU2 or STU3.

<br>

![Illustration highlighting Care Coordination and collaboration](../../media/ehr-1.png)

<br>

The Patients app integrates with electronic health records (EHR) systems and enables care providers to communicate about patient care in real-time within Teams' secure platform. The Patients app is the first major investment in the care coordination area which aims to address the following challenges:

- Low efficiency in hand-offs and critical communication through the patient experience
- Siloed information that creates administrative burdens
- Dissatisfaction among clinicians with complex and fragmented collaboration tools
- Inefficient in-person care coordination that can burn too much expensive clinical time

Microsoft Teams enables physicians, clinicians, nurses, and other staff to collaborate efficiently by:

- Being part of a single virtualized team that works and collaborates on Office documents
- Having persistent conversations about different patients needing attention
- Using channels with tabs as a way to structure their work, with additional help from tabs to which they can pin information sources
- Using channel meetings with the power of Teams audio, video, screen sharing, recording, and transcription features to manage daily meetings
- Using the Patients app to curate a list of high-risk patients that must be monitored, and pulls their latest details from the EHR system. The Patients app itself adds the following features to Microsoft Teams:

    - Ability to create multiple patient lists within a single channel.
    - Ability to view and sort information displayed about patients through configurable columns.
    - Ability to auto-provision the app through a team template.
    - Available on the Teams App for iOS and Android for mobile first healthcare workers as well as Microsoft Teams web and desktop client.
    - Support for FHIR DSTU2 and STU3 versions via parsing of conformance statement.
    - Audit Logs for all view and search actions on its user interface to safeguard PHI per HIPAA guidelines.

The Patients app is built on the Teams extensibility platform and takes advantage of the Tabs framework to display rich patient content within a channel. To learn more about other Teams apps and the platform itself, please see [Apps for Microsoft Teams](/microsoftteams/platform/concepts/apps/apps-overview).  

> [!NOTE]
> The Patients app is in private preview and the FHIR interface is in beta. Released versions are not expected to be backward compatible.

![Screen shot of the Patients app on desktop and mobile devices](../../media/ehr-2.png)

See [Integrating Electronic Healthcare Records into Microsoft Teams](patients-app.md) for implementation details,.

## Teams templates

New templates for creating Teams were developed to apply to a Hospital setting, and more are expected soon. This makes it easier to create teams that Healthcare workers use to coordinate care for patients in various departments or wards. See [Get started with Teams templates for Healthcare organizations](healthcare-templates.md). Teams can be started for internal departments such as cardiology, or for care wards, and more templates are in development.

## Lists app

[!INCLUDE [preview-feature](../../includes/preview-feature.md)]

The Lists app in Teams helps teams track information and organize work. The app is pre-installed for all Teams users and is available as a tab in every team and channel. Lists can be created from scratch, from predefined templates, or by importing data to Excel.

Care teams can use the Patients template to get started. They can create lists to track the needs and status of patients. Existing patient data on Excel spreadsheets can be brought in to create a list in Teams. These lists can be used for scenarios such as rounds and patient monitoring to coordinate care.

For example, a charge nurse creates a patient list in a team that includes all care team members. During rounds, the care team access Teams on their mobile devices and update patient information in the list, which everyone on the team can view to stay in sync. At rounding sessions where the care team gathers to discuss and evaluate key health performance metrics to ensure a patient is on the right glide path to discharge, they can share this information using Teams on a large display screen. Care team members who aren't on site can join remotely.

Here's an example list which was set up for patient rounding.

:::image type="content" source="../../media/lists-patients-example.png" alt-text="Screenshot of example list for patient rounding":::

To learn more, see [Manage the Lists app for your organization in Teams](../../manage-lists-app.md).

## Secure Messaging

Secure messaging supports collaboration within care teams, including several new features:

- A message sender can set a special priority for their message, so the recipient is repeatedly notified until they read the message.
- A message sender can request a read receipt, so they are notified when a message they sent was read by the message recipient.


Together, these features allow quicker attention to urgent messages and confidence that the message was received and read. New care teams using these features can be created on a per-patient basis. These features are policy-based, and can be assigned to individuals or entire Teams.

See [Get started with Secure Messaging policies for Healthcare organizations](messaging-policies-hc.md) for further details.

Also related to secure messaging is the ability to have other tenants federated by Healthcare organizations, allowing richer inter-tenant communication. (See [Manage external access (federation) in Microsoft Teams](../../manage-external-access.md)).

## Firstline Worker integration

Microsoft Teams integrates with Firstline Worker, which can be used to coordinate shift staffing features and more. See [Manage the Shifts app for your organization in Microsoft Teams](../shifts/manage-the-shifts-app-for-your-organization-in-teams.md).
