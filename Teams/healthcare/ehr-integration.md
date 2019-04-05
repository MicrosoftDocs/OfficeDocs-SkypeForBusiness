---
title: "Integrating FHIR and Microsoft Teams"
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
description: Get started with Microsoft Teams Healthcare templates for EHR integration
---

# Get started with Microsoft Teams FHIR integration

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

- What is the new or updated experience. Include a screenshot (what does it look like?). 
    
- Is the feature on or off by default? 
    
- Where can they go to get more information? link to end user overview or landing page.
    
![Placeholder - maximum width for SOC article art is 520 pixels](images/)
  
## Set it up/Manage

### In Preview: **This feature** is in preview, how do I opt in? -OR- At GA or after: **This feature** is on by default for your organization.

To opt-in and use **this feature** while it's in preview, see **Setup tab**. -OR- To prevent your org or individuals from using this feature until you've reviewed it, you can remove the **feature** from the App launcher by following this article, [Prevent users from starting to use new features until my organization is ready](6f55cdae-078d-4834-86cc-fcef98ba74b8.md#Prevent). You can also make other changes such as [letting Microsoft know](6f55cdae-078d-4834-86cc-fcef98ba74b8.md#limits) when you want features to release to your tenant.

### How do I manage this feature or how do I set up this feature?

Cover these points: 

- Is this feature per org or per user? 
    
- Use PowerShell or UI?
    
- For Set up: short instructions on how to turn on the feature for the organization or for individual users. If you want to turn it off for individuals or your whole organization right away, see [How do I turn this feature on or off for my organization?](#Off)
    
- For Manage: sections with basic management tasks.
    
If there are more tasks, add links for where to find more help (like on a landing page?) 

## Security & Compliance

If your business has legal, regulatory, and technical standards to meet for content security and data use, this section is for you. 

### Where is the data associated with this feature stored?

Also include any other data implications.

### Does **insert feature/app name** meet our compliance requirements?

To help customers with their compliance needs related to Office 365, we have created a compliance framework that is designed to give customers visibility into Office 365’s compliance with global, regional and industry standards, and details how customers can control Office 365 services based on compliance needs. Review our [Office 365 Compliance Framework for Industry Standards and Regulations](http://go.microsoft.com/fwlink/p/?LinkId=615657) **insert feature/app name** is in.

## FAQ - Frequently-asked administrator questions about **feature**:

### Does this feature depend on any other features?

### List of dependent feature (e.g. Office Graph, Delve, etc….)

### What happens if I disable **dependent features, e.g. Graph**

Include details what experience will be if one or more of dependent features are disabled.

### Where can I find more controls and limits information?

Find your feature area in the service descriptions, and point to the specific content. starting point: [Office 365 Platform Service Description](https://technet.microsoft.com/en-us/library/office-365-platform-service-description.aspx)

