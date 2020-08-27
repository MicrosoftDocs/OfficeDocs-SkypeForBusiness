---
title: Teams for Telehealth
author: cichur
ms.author: v-cichur
manager: serdars
audience: ITPro
ms.topic: conceptual
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
description: Use Microsoft Teams to set up your Telehealth system
---

# Telehealth and Teams integration into Electronic Health Record admin

Microsoft Teams Electronic Health Record (EHR) connector makes it easy for clinicians to launch a virtual patient visit or consultation with another provider in Teams directly from the EHR system. The communication and collaboration of platform of Teams makes it easy for clinicians to cut through the clutter of traditionally fragmented systems so they can spend time providing the best possible care. Built on the Microsoft 365 cloud, Teams can help provide advanced security and empower healthcare customers to achieve their HIPAA, HITRUST compliance, and more.

-   Launch Teams meetings from both provider and patient portals.

-   Write back into EHR metadata on Connect/Disconnect events to enable automatic auditing and record keeping.

-   Integrate into clinician’s existing workflows while allowing them to leverage Microsoft Teams.

This integration supports the following virtual visit use cases in web and mobile:

-   Provider to patient.

-   Provider to provider inside your organization.

-   Provider to provider between organizations.

-   Multi-participants appointments.

### **Pre-requisites**

-   Active subscription to Healthcare Cloud \[LINK\] or stand alone \[LINK\] subscription model

-   Users must have an appropriate license. Office 365 A3, A5, E3, and E5, as well as Microsoft 365 Business Standard, A3, A5, E3, and E5 are supported.

-   Microsoft Teams should be adopted and used inside the organization

-   Organizations must have a current integration into Epic

-   Your systems must meet all [Software and browser prerequisites](https://docs.microsoft.com/microsoftteams/hardware-requirements-for-the-teams-app).

### **Getting started** 

#### **Create mapping**

The process to configure your healthcare organization to be able to launch virtual visits with Microsoft Teams starts by launching the EHR Connector URL \[link\] that can also be found in the Epic-Microsoft Teams Telehealth Integration Guide in AppOrchard marketplace. The O365 admin and Epic admin for your organization must complete the information and integration steps in the connector. For Epic configuration steps, please contact the Epic resource assigned to your organization

#### **Map Epic organization**

In this step your O365 administrator must receive a valid FHIR base URL and the admin username that will approve the configuration. O365 administrator must launch the connector and sign-in in order to start the configuration process.

-   FHIR base URL: This is a constant address that all FHIR API endpoints for the server's default FHIR version live under.

-   Configuration approver name: name of the Epic system administrator who will be responsible of approving the configuration Overall process

 [!Image of the Epic administrator configuration screen](../../media/ehr-connector-1.png)

#### **Verify and Approve configuration** 

In this step the Epic administrator for your healthcare organization that was added as an approver in the previous step must use the EHR Connector URL \[link\] to login using their Microsoft credentials. After successful validation, the user is going to be asked to login to Epic to validate the level of access for the user.

NOTE: O365 admin and Epic admin in your organizations can be the same person. In that case, add your own username as approver in the first step. You will still need to login to Epic to validate your access.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams\expand-teams-across-your-org\healthcare/media/image2.jpeg" style="width:5in;height:2.8125in" />

After a successful Epic login, the Epic administrator must approve the configuration to create the mapping. If the configuration is not correct, the O365 admin will have the ability to modify the original configurations by login into the connector again.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams\expand-teams-across-your-org\healthcare/media/image3.png" style="width:5in;height:2.8125in" />

#### **Review and Finish configuration** 

When the configuration information is approved by the Epic admin, you will have the opportunity to review the mapping and modify any configuration if needed. Finally, when the configuration mapping is correctly approved, you will see key data elements that you will need to complete the telehealth configuration in Epic.

NOTE: Please download and read the Epic-Microsoft Teams Telehealth Integration Guide found in AppOrchard for configuration steps.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams\expand-teams-across-your-org\healthcare/media/image4.png" style="width:5in;height:2.8125in" />

#### **Launching Teams virtual visits**

After completing the configuration steps in the EHR connector and in Epic, your organization is now ready to support video visits with Microsoft Teams. The solution is embedded in the patient and provider flows in their respective Epic portal, reducing the learning curve for users.

###### **Pre-requisites**

-   Healthcare organization must have completed Getting Started section from this document to create the mapping between the organization and Microsoft Teams.

-   Meeting must have been schedule by either the healthcare provider in any of the provider portals (Hyperspace, Haiku, Canto) or the patient in MyChart portal

###### **Patient Experience**

In MyChart, patients will be able to schedule appointments as they regularly do. Patient must select Microsoft virtual visit during the scheduling. When day and time for the appointment comes, the patient can launch a virtual visit from MyChart.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams\expand-teams-across-your-org\healthcare/media/image5.png" style="width:5in;height:3.72917in" />

Key features of the patient experience includes:

-   Patients are not required to create a Microsoft account or login to launch a virtual visit.

-   Patients are not required to download Microsoft Teams app to launch a virtual visit.

-   Virtual visits are supported in browser. For a list of supported software and browsers please see the following link [Software and browser prerequisites](https://docs.microsoft.com/en-us/microsoftteams/hardware-requirements-for-the-teams-app).

-   Patient will be placed in a lobby until the healthcare provider joins the appointment and allow them access to the virtual visit.

-   Test of video and microphone is allowed before joining the virtual visit

###### **Provider Experience**

Healthcare provider from your organization can also join virtual visits with Microsoft Teams from their porta (Hyperspace, Haiku, Canto). The begin virtual visit button is embedded in the provider flow where patient information is displayed.

Key features of the provider experience:

-   Providers can join virtual visits using supported browsers or the Microsoft Teams web application.

-   Providers must perform a one-time login to their Microsoft account when joining a virtual visit.

-   After the one-time login, the provider will be taken straight to the virtual appointment.

-   Providers have the option to end-call for all participants in the virtual appointment.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams\expand-teams-across-your-org\healthcare/media/image6.png" style="width:3.83333in;height:2.60417in" />

A very important feature supported by the integration is the real-time updates in the provider portal of connect and disconnect or participants for a given appointment. That way, the provider can join the virtual visit only when the patient is ready to take the consultation.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams\expand-teams-across-your-org\healthcare/media/image7.png" style="width:3.39583in;height:1.3125in" />

**Privacy and Location of Data**
================================

Teams integration into EHR systems optimized the process to reduce the amount of data being used and stored during integration and virtual visit flows. The solution follows the overall Teams privacy and data management principles and guidelines outlined here: <https://docs.microsoft.com/en-us/microsoftteams/teams-privacy>

Throughout the integration into EHR systems, Microsoft does not store any identifiable personal data of patients or healthcare providers. Medical data is not transferred or stored by any Microsoft service. For the service to effectively work the only data that is stored by Microsoft is the healthcare provider Epic identifier, that is used to mapped providers to meeting links. Sign-in and authentication actions are handled by each EHR system.
