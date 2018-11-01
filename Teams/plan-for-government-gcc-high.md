---
title: Plan for Microsoft 365 Government - GCC High deployments - Microsoft Teams
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.date: 11/01/2018
ms.topic: article
ms.service: msteams
ms.reviewer: daro
description: Guidance for IT pros to drive Office 365 deployments in entities that handle data subject to US government regulation  
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
---

# Plan for Microsoft 365 Government - GCC High deployments

This guidance is for IT pros who are driving deployments of Office 365 in US federal government entities or other entities that handle data that’s subject to government regulations and requirements, where the use of Microsoft 365 Government – GCC High is appropriate to meet these requirements.

> [!NOTE]
> If your organization has already met the Microsoft 365 Government – GCC High eligibility requirements and applied for and been accepted into the program, you can skip steps 1 through 4 and go directly to step 5 to begin your deployment.

## Step 1. Determine whether your organization needs Microsoft 365 Government - GCC High and meets eligibility requirements. 

The Microsoft 365 Government - GCC  High   environment provides compliance with US government requirements for cloud services. In addition to enjoying the features and capabilities of Office 365, organizations benefit from the following features that are unique to Microsoft 365 Government – GCC High:

- Your organization’s customer content is logically segregated from customer content in the commercial Office 365 services from Microsoft.
- Your organization’s customer content is stored within the United States.
- Access to your organization’s customer content is restricted to screened Microsoft personnel.
- Microsoft 365 Government – GCC High complies with certifications and accreditations that are required for US Public Sector customers.

You can find more information about the Microsoft 365 Government – GCC High offering for US Government customers at [Office 365 Government plans](https://products.office.com/government/compare-office-365-government-plans), including [eligibility requirements](https://products.office.com/government/compare-office-365-government-plans#EligibilityRequirements).

The [Office 365 US Government service description](https://docs.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government) describes the platform’s benefits, which are centered on meeting compliance requirements within the United States.


> [!Tip]
> You might want to transfer the tables of information in the service description into an Excel workbook and add two columns: **Relevant for my organization Y/N** and **Meets the needs of my organization Y/N**. Then you can review this list with your colleagues to confirm that this service meets your organization’s needs.


|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether Microsoft 365 Government - GCC High is appropriate for your organization.</li><li>Confirm that your organization meets eligibility requirements.</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Understand the capabilities provided by Microsoft 365 Government - GCC High.</li></ul>|

> [!Note]
> Microsoft 365 Government - GCC High is only available in the United States. Non–US Government customers can choose from a number of [Office 365 Government plans](https://products.office.com/en/government/compare-office-365-government-plans).

## Step 2. Understand which capabilities are currently unavailable or disabled by default. 

To accommodate the requirements of our government cloud customers, there are some differences between Microsoft 365 Government - GCC High and Enterprise plans. The features listed in the following table are unavailable.

| Feature                     | Reason            |
|-----------------------------|-------------------|
| Call and Meeting Recording  | Recording is dependent on Microsoft Stream, which will be available in US Government plans in the future. |
| Apps       | Non-compliant apps (such as bots, tabs, and connectors) won’t be available initially, but we’re working to make them available as soon as all their components meet the compliance bar. |
| Email a channel             | The current feature architecture isn’t supported in government plans. |
| Unified Presence            | We’re finishing work for our enterprise and GCC customers first for this important feature. It will be available to GCC High customers in the future.|
| Interop chat between Teams & Skype for Business users | Interop is dependent on Unified Presence Service (UPS) and cannot work until GCC High Teams tenants are enabled for UPS. |
| Email Notifications         | The current feature architecture isn’t supported in the US Government plans. Work is ongoing to make this feature available to US Government plan customers in the future.|


|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether the Microsoft 365 Government - GCC High feature set meets your organization’s needs.</li></ul> |
| ![](media/audio_conferencing_image9.png)<br/>Next step|<ul><li>Understand default security settings.</li></ul>|

## Step 3. Apply for Microsoft 365 Government - GCC High

Having decided that this service is right for your organization, start the process of [applying for this service](https://products.office.com/government/eligibility-validation).

## Step 4. Plan for governance

Determine your requirements for governance and how you can meet them. Go to [Plan for governance in Teams](plan-teams-governance.md) for more information.

## Step 5. Deploy Teams for collaboration

After you’ve been onboarded to Microsoft 365 Government – GCC High, you can follow the standard deployment approach of using [FastTrack](https://fasttrack.microsoft.com/fasttrack-faq) and your chosen partner to onboard the service.

When you’re ready, deploy Teams to [enable collaboration within your organization through teams and channels](teams-overview.md). Be sure to engage with your Adoption and Change Management team or Teams champions.


