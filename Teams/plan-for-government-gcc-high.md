---
title: Plan for Microsoft 365 Government - GCC High deployments - Microsoft Teams
author: lolajacobsen
ms.author: lolaj
manager: serdars
ms.date: 01/03/2019
ms.topic: article
ms.service: msteams
ms.reviewer: daro
description: Guidance for IT pros to drive Office 365 deployments in entities that handle data subject to US government regulation.  
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
> If your organization has already met the Microsoft 365 Government – GCC High eligibility requirements and applied for and been accepted into the program, you can skip steps 1 and 2 and go directly to step 3.

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

> [!Note]
> Microsoft 365 Government - GCC High is only available in the United States. Non–US Government customers can choose from a number of [Office 365 Government plans](https://products.office.com/en/government/compare-office-365-government-plans).

## Step 2. Apply for Microsoft 365 Government - GCC High

Having decided that this service is right for your organization, start the process of [applying for this service](https://products.office.com/government/eligibility-validation).


## Step 3. Understand Microsoft 365 Government - GCC High default security settings.

We recommend that you take time to carefully review your [admin and security settings](enable-features-office-365.md) before you modify them, and consider impacts on compliance before you make any changes to the default security settings.

|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether you’ll need to modify any of the default Microsoft 365 Government - GCC High security settings, resolving to first understand the impact of any changes you might make.</li></ul> |


## Step 4. Understand which Teams capabilities are currently available in Microsoft 365 Government - GCC High

To accommodate the requirements of our government cloud customers, there are some differences between Teams in Microsoft 365 Government - GCC High and Teams in the Enterprise plans. Refer to the following table to see which features are available.

|                             | Feature                     | GCC High       |
|-----------------------------|-----------------------------|----------------|
| Base | Login | Available |
| | Presence | Available |
| | Unified presence (Skype for Business and Teams unified) | On the Government backlog |
| Activity | Feed | Available |
|  | My Activity | Available |
| Chat | Conversation | Available |
| | Files | Available |
| | Org chart | Available |
| | Activity | Available |
| | InterOp (1:1 Teams-Skype for Business chat) | On the Government backlog |
| Teams | Channel message | Available |
| | Channel files | Available |
| | OneNote tab | On the Government backlog |
| | Email a channel | Not available |
| | Add member | Available |
| | Guest access | On the Government backlog |
| Meetings | Schedule meeting | Available |
| | Join meeting | Available |
| | VoIP meeting | Available |
| | Desktop sharing | Available |
| | Give and take control in sharing | Available |
| | Connect from a conference room | Available |
| | Anonymous join | Available |
| | Cloud recording | On the Government backlog |
| | Meeting notes | Available |
| | Broadcast meetings | On the Government backlog |
| | Federated meetings | Available |
| | Surface Hub support | On the Government backlog |
| Calls | Contacts | Available |
| | History | Available |
| | Voicemail | Available |
| | VoIP call | Available |
| | Skype for Business - Teams calling | Available |
| | Calling Plans | Not Available |
| | Audio conferencing (by allowing meeting participants to join via PSTN) | On the Government backlog |
| | Microsoft Phone System direct routing | On the Government backlog |
| | Lobby for PSTN callers | On the Government backlog |
| | Call queue | On the Government backlog |
| | Boss and delegate support | On the Government backlog |
| | Consultative and safe transfer | On the Government backlog |
| | Do not disturb breakthrough | On the Government backlog |
| | Distinctive ring | On the Government backlog |
| | 1:1 to group call escalation with Teams, Skype for Business, and PSTN participants | On the Government backlog |
| | Forward to group | On the Government backlog |
| | Transfer to PSTN call | On the Government backlog |
| | Emergency calling - Calling Plans | On the Government backlog |
| | Support for existing certified SIP phones | On the Government backlog |
| | USB HID | Available |
| | eDiscovery for both calls and meetings | Available |
| | Organization auto attendant | On the Government backlog |
| | Skype consumer - Teams call support | Not available |
| Files | Recent | Available |
| | Microsoft Teams | Available |
| Store | App Store | Not available |
| Search | Messages | Available |
| | People | Available |
| | Files | Available |
| | Slash commands | Available |
| Compliance | Compliance content search | Available |
| | Retention | Available |
| | Audit log search | Available |
| | Legal hold | Available |
| | eDiscovery | Available |

|    |     |
|-----------|------------|
| ![](media/audio_conferencing_image7.png) <br/>Decision point|<ul><li>Decide whether the Teams feature set meets your organization’s needs.</li></ul> |

## Step 5. Plan for governance

Determine your requirements for governance and how you can meet them. Go to [Plan for governance in Teams](plan-teams-governance.md) for more information.

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision point |<ul><li>Determine and document your governance requirements, following the guidelines in [Plan for governance in Teams](plan-teams-governance.md). </li></ul>|

## Step 6. Deploy Teams for collaboration

After you’ve been onboarded to Microsoft 365 Government – GCC High, you can follow the standard deployment approach of using [FastTrack](https://www.microsoft.com/fasttrack) and your chosen partner to onboard the service.

When you’re ready, deploy Teams to [enable collaboration within your organization through teams and channels](teams-overview.md). Be sure to engage with your Adoption and Change Management team or Teams champions.
