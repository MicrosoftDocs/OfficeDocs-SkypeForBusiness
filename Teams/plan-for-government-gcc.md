---
title: Plan for Microsoft 365 Government - GCC deployments - Microsoft Teams
author: lolajacobsen
ms.author: lehewe
manager: serdars
ms.date: 09/14/2018
ms.topic: article
ms.service: msteams
ms.reviewer: lehewe
description: Guidance for IT pros to drive Office 365 deployments in entities that handle data subject to US government regulation  
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
---

# Plan for Microsoft 365 Government - GCC deployments

This guidance is for IT pros who are driving deployments of Office 365 in US federal, state, local, tribal, or territorial government entities or other entities that handle data that’s subject to government regulations and requirements, where the use of Microsoft 365 Government - GCC is appropriate to meet these requirements.

> [!NOTE]
> If your organization has already met the Microsoft 365 Government - GCC eligibility requirements and applied for and been accepted into the program, you can skip steps 1 through 4 and go directly to step 5 to begin your deployment. 

## Step 1. Determine whether your organization needs Microsoft 365 Government - GCC and meets eligibility requirements. 

The Microsoft 365 Government - GCC environment provides compliance with US government requirements for cloud services, including FedRAMP Moderate, and requirements for criminal justice and federal tax information systems (CJI and FTI data types).

In addition to enjoying the features and capabilities of Office 365, organizations benefit from the following features that are unique to Microsoft 365 Government - GCC:

-   Your organization’s customer content is logically segregated from customer content in the commercial Office 365 services from Microsoft.
-   Your organization’s customer content is stored within the United States.
-   Access to your organization’s customer content is restricted to screened Microsoft personnel.
-   Microsoft 365 Government - GCC complies with certifications and accreditations that are required for US Public Sector customers.

You can find more information about the Microsoft 365 Government - GCC offering for US Government customers at [Office 365 Government plans](https://products.office.com/government/compare-office-365-government-plans), including [eligibility requirements](https://products.office.com/government/compare-office-365-government-plans#EligibilityRequirements).

The [Office 365 US Government service description](https://technet.microsoft.com/library/mt774581.aspx) describes the platform’s benefits, which are centered around meeting compliance requirements within the United States.

> [!Tip]
> You might want to transfer the tables of information in the service description into an Excel workbook and add two columns: **Relevant for my organization Y/N** and **Meets the needs of my organization Y/N**. Then you can review this list with your colleagues to confirm that this service meets your organization’s needs.


|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether Microsoft 365 Government - GCC is appropriate for your organization.</li><li>Confirm that your organization meets eligibility requirements.</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Understand the capabilities provided by Microsoft 365 Government - GCC.</li></ul>|

> [!Note]
> Microsoft 365 Government - GCC is only available in the United States. Non–US Government customers can choose from a number of [Office 365 Government plans](https://products.office.com/en/government/compare-office-365-government-plans).

## Step 2. Understand which capabilities are currently unavailable or disabled by default. 

To accommodate the requirements of our government cloud customers, there are some differences between Microsoft 365 Government - GCC and Enterprise plans. The features listed in the following table are unavailable.

| Feature                     | Reason            |
|-----------------------------|-------------------|
| Call and Meeting Recording  | Recording is dependent on Microsoft Stream, which will be available in US Government plans in the future. |
| Apps       | Apps (such as bots, tabs, and connectors) won’t be available initially, but we’re working to make them available as soon as all their components meet the FedRAMP Moderate compliance bar. |
| Email a channel             | The current feature architecture isn’t supported in government plans. |
| Unified Presence            | We’re finishing work for our enterprise customers first for this important feature. It will be available to government customers in the future. |
| Interop chat between Teams & SfB users            | Interop is dependent on Unified Presence Service (UPS) and cannot work until GCC Teams Tenants are enabled for UPS. |
| Email Notifications         | The current feature architecture isn’t supported in the US Government plans. Work is ongoing to make this feature available to US Government plan customers in the future. |


|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether the Microsoft 365 Government - GCC feature set meets your organization’s needs.</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Understand default security settings.</li></ul>|

## Step 3. Understand Microsoft 365 Government - GCC default security settings.

We recommend that you take time to carefully review your [admin and security settings](enable-features-office-365.md) before you modify them, and consider impacts on compliance before you make any changes to the default security settings.

|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether you’ll modify any of the default Microsoft 365 Government - GCC security settings, resolving to first understand the impacts of any changes you might make.</li></ul> |

## Step 4. Apply for Microsoft 365 Government - GCC

Having decided that this service is right for your organization, start the process of [applying for this service here](https://products.office.com/government/eligibility-validation).

## Step 5. Plan for governance

Determine your requirements for governance and how you can meet them. Go to [Plan for governance in Teams](plan-teams-governance.md) for more information.

## Step 6. Deploy Teams for collaboration

After you’ve been onboarded to Microsoft 365 Government - GCC, you can follow the standard deployment approach of using [FastTrack](https://fasttrack.microsoft.com/fasttrack-faq) and your chosen partner to onboard to the service.

When you’re ready, deploy Teams to [enable collaboration within your organization through teams and channels](teams-overview.md). Be sure to engage with your Adoption and Change Management team or Teams champions.

## Step 7. Deploy Teams for meetings and voice

This is also a great time to use Teams with your wider stakeholder group to start planning for rolling out meetings and [cloud voice features](cloud-voice-deployment.md).

