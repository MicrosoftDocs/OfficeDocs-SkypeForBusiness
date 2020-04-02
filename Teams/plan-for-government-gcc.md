---
title: Plan for Microsoft 365 Government - GCC deployments - Microsoft Teams
author: lolajacobsen
ms.author: heidip
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: daro
audience: admin
description: Guidance for IT pros to drive Office 365 deployments in entities that handle data subject to US government regulation
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: Teams-upgrade-guidance
ms.collection: 
  - M365-collaboration
  - remotework
appliesto: 
  - Microsoft Teams
---

# Plan for Microsoft 365 Government - GCC deployments

This guidance is for IT pros who are driving deployments of Office 365 in US federal, state, local, tribal, or territorial government entities or other entities that handle data that's subject to government regulations and requirements, where the use of Microsoft 365 Government - GCC is appropriate to meet these requirements. New March 26, 2020: Don't miss our downloadable [Quick Start guide for GCC](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/Quick-Start-Guide-for-GCC.pdf?raw=true).

> [!IMPORTANT]
> Microsoft Teams is experiencing a tremendous spike in online calls and audio/video conferencing due to the coronavirus (COVID-19) pandemic.<br/>
> 
>In response to the unprecedented increase in calls, and to ensure continuity and availability, Microsoft is allowing Microsoft Teams GCC audio/video servers to leverage processing capacity in our commercial datacenters, as well as in our government datacenters.<br/>
> 
>These audio/video servers reside within the Microsoft Azure FedRAMP High accreditation boundary servers in the United States and do not store any customer content. However, these servers are processing audio and video for calls and conferences and are operating under our commercial staff during this interim period.<br/>
> 
>Qualified, screened personnel are monitoring these servers for potential access to customer data by reviewing any interactive log-ons to these servers. Qualified personnel meet GCC requirements for access to customer content. For details about screening requirements, see the [GCC service description](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc).<br/>
> 
>Thank you for your support as we take steps to ensure that our services remain available and reliable in these extraordinary times.<br/>


> [!NOTE]
> If your organization has already met the Microsoft 365 Government - GCC eligibility requirements and applied for and been accepted into the program, you can skip steps 1 and 2 and go directly to step 3. 

## Step 1. Determine whether your organization needs Microsoft 365 Government - GCC and meets eligibility requirements. 

The Microsoft 365 Government - GCC environment provides compliance with US government requirements for cloud services, including FedRAMP Moderate, and requirements for criminal justice and federal tax information systems (CJI and FTI data types).

In addition to enjoying the features and capabilities of Office 365, organizations benefit from the following features that are unique to Microsoft 365 Government - GCC:

-   Your organization's customer content is logically segregated from customer content in the commercial Office 365 services from Microsoft.
-   Your organization's customer content is stored within the United States.
-   Access to your organization's customer content is restricted to screened Microsoft personnel.
-   Microsoft 365 Government - GCC complies with certifications and accreditations that are required for US Public Sector customers.

You can find more information about the Microsoft 365 Government - GCC offering for US Government customers at [Office 365 Government plans](https://products.office.com/government/compare-office-365-government-plans), including [eligibility requirements](https://products.office.com/government/compare-office-365-government-plans#EligibilityRequirements).

The [Office 365 US Government service description](https://technet.microsoft.com/library/mt774581.aspx) describes the platform's benefits, which are centered around meeting compliance requirements within the United States.

> [!Tip]
> You might want to transfer the tables of information in the service description into an Excel workbook and add two columns: **Relevant for my organization Y/N** and **Meets the needs of my organization Y/N**. Then you can review this list with your colleagues to confirm that this service meets your organization's needs.

|    |     |
|-----------|------------|
| ![An icon depicting decision points](media/audio_conferencing_image7.png) <br/>Decision points|<ul><li>Decide whether Microsoft 365 Government - GCC is appropriate for your organization.</li><li>Confirm that your organization meets eligibility requirements.</li></ul> |

> [!Note]
> Microsoft 365 Government - GCC is only available in the United States. Non–US Government customers can choose from a number of [Office 365 Government plans](https://products.office.com/en/government/compare-office-365-government-plans).


## Step 2. Apply for Microsoft 365 Government - GCC

Having decided that this service is right for your organization, start the process of [applying for this service here](https://products.office.com/government/eligibility-validation).

## Step 3. Understand Microsoft 365 Government - GCC default security settings.

We recommend that you take time to carefully review your [admin and security settings](enable-features-office-365.md) before you modify them, and consider impacts on compliance before you make any changes to the default security settings.

|    |     |
|-----------|------------|
| ![An icon depicting a decision point](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether you'll modify any of the default Microsoft 365 Government - GCC security settings, resolving to first understand the impact of any changes you might make.</li></ul> |

## Step 4. Understand which capabilities are currently unavailable or disabled by default.

To accommodate the requirements of our government cloud customers, there are some differences between Microsoft 365 Government - GCC and Enterprise plans. Refer to the following table to see which features are available.

[Microsoft Teams service description](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description)

> [!Note]
> Once other workloads are fully available in the GCC cloud, then they will become available in Teams when all additional  integration work is completed.


|    |     |
|-----------|------------|
| ![An icon depicting a decision point](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether the Teams feature set meets your organization's needs.</li></ul> |

## Step 5. Plan for governance

Determine your requirements for governance and how you can meet them. Go to [Plan for governance in Teams](plan-teams-governance.md) for more information.

|    |     |
|-----------|------------|
| ![An icon depicting a decision point](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Determine and document your governance requirements, following the guidelines in [Plan for governance in Teams](plan-teams-governance.md).</li></ul> |

## Step 6. Deploy Teams for collaboration

After you've been onboarded to Microsoft 365 Government – GCC, follow the recommended deployment path outlined in [How to roll out Microsoft Teams](How-to-roll-out-teams.md). Be sure to engage with your Adoption and Change Management team and Teams champions.

You can also work with [FastTrack](https://www.microsoft.com/fasttrack) or your chosen partner to onboard the service.

## Step 7. Deploy Teams for meetings and voice

This is also a great time to use Teams with your wider stakeholder group to start planning for rolling out meetings and [cloud voice features](cloud-voice-deployment.md).

