---
title: "User health team templates"
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
description:  health team templates
---

# New Healthcare-centric templates

You can enter the info needed for these features in this working page, when the time comes the content can be integrated into 
https://docs.microsoft.com/en-us/MicrosoftTeams/expand-teams-across-your-org/healthcare/healthcare-templates 


## User sideloaded health team templates (June release, Aaron Lai PM)

Enable end-users to sideload templates using in-app UI flow

Admins can distribute templates using sharepoint or website


## FHIR/ EHR integration (presumed template related, June release, Ansuam Acharya PM)

FHIR Integration for Microsoft Teams	

Need technical documentation for our application's FHIR interface with pointers to how to build a FHIR Server using OSS (MSR documentation) + UI Screenshots of Teams features where Patient data shows up	

This is more dev documentation but I chatted with Andrew Clear who owns the Teams platform documentation and he mentioned that the right place to slot this in would be under the Teams for healthcare section. I have a lot of the material ready in a word doc present here: https://microsoft.sharepoint.com/:w:/t/OfficeHealthcareSolutions/EfcebK9Z4FxDsRx2HC2T7JYBQYb-qM9otJIcuWIphyxDew?e=orJAQR

Also have excerpted high-level info from Ansuman's blog:

### EHR integration

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

## FeatureName overview

Short overview of what the new feature is. 

- What is the new or updated experience?

- Does this feature replace an existing feature/experience? If yes, what is the transition plan?

- Does this feature has dependency on other features? If yes, list/explain the dependencies.

- List the key deployment scenarios - why would people use this feature? 

## [OPTIONAL] Planning for feature

Some features would require careful pre-planning before deployment can begin. For those features, cover what planning tasks customers should complete.

## Configure feature

How do you configure this feature? Cover these points: 

- Are there any prerequisites?

- Is this feature per org or per user? 

- Use PowerShell or UI?

- Short instructions on how to turn on the feature for the organization or for individual users. 

## Manage feature

- Add subsections with basic management tasks that would be required or that we expect customer to perform. 

### Management task 1

### Management task 2

## Security & Compliance

List any security or compliance impact of this feature here. Cover the following:

- Where is the data associated with this feature stored?

- Include any other data implications such as GDPR compliance.


## Related topics

[Get started with Teams templates](../get-started-with-teams-templates.md)

[Get started with Teams for Healthcare organizations](teams-in-hc.md)


