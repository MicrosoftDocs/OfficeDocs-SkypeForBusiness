---
title: Data, privacy, and security for intelligent recap in Teams Premium
ms.author: danbrown
author: DHB-MSFT
manager: laurawi
ms.topic: conceptual
ms.service: msteams
ms.reviewer: meajam
audience: ITPro
ms.date: 10/09/2023
description: Learn about what content is used to provide intelligent recap and how intelligent recap uses AI
ms.localizationpriority: medium
---

# Data, privacy, and security for intelligent recap in Teams Premium

Intelligent recap uses AI to automatically provide a comprehensive overview of your meeting, helping users save time catching up and coordinating next steps. Found on the **Recap** tab in Teams calendar and chat, users see AI-powered insights like automatic generated meeting notes, suggested tasks, and personalized highlights to help them quickly find the most important information, even if they miss the meeting. Intelligent recap is available as part of Teams Premium, which is an add-on license that provides additional features to make Teams meetings more personalized, intelligent, and secure. To get access to Teams Premium, contact your IT admin.

For an overview of intelligent recap, see [Meeting recap in Microsoft Teams](https://support.microsoft.com/office/c2e3a0fe-504f-4b2c-bf85-504938f110ef), or you can watch the [How to use Intelligent recap in Microsoft Teams Premium](https://www.youtube.com/watch?v=n-ub_VdpkAI) video.

## What content is used to provide intelligent recap and where is it stored?

The following table shows what content is used to provide intelligent recap and where that content is stored. All the features listed in the table follow the meeting recording retention policy. For more information, see [Teams meeting recording](../meeting-recording.md?tabs=meeting-policy) and [Learn about retention for Microsoft Teams](/purview/retention-policies-teams).

|Feature  |Description  |Created from  |Stored in  |
|---------|---------|---------|---------|
|AI-generated notes|Understand key points from the discussion|Meeting transcript|Stored in an Exchange folder in the mailboxes of the meeting participants.|
|AI-generated tasks|Understand suggested tasks and who they’re assigned to|Meeting transcript|Stored in an Exchange folder in the mailboxes of the meeting participants.|
|Personalized timeline markers|Video markers for when your name was mentioned|- Meeting transcript </br> - User display name|Stored in an Exchange folder in the mailboxes of the meeting participants.|
||Video markers for when a screen was shared|- Meeting transcript </br> - Meeting recording|Stored in OneDrive or SharePoint together with the meeting recording|
||Video markers for when you joined/left the meeting|- Meeting transcript </br> - Attendance report|Stored in an Exchange folder in the mailboxes of the meeting participants.|
|Speaker timeline markers|Speaker timeline markers allow you to jump to different speakers. Organized by those you work most closely with.|Meeting transcript|Stored in an Exchange folder in the mailboxes of the meeting participants.|
|Auto-generated chapters and topics|Chapters and topics divide the meeting into sections so it’s easy to jump right to where you would like to review.|- Meeting transcript </br> - PowerPoint Live|Stored in OneDrive or SharePoint together with the meeting recording|

## How Microsoft uses data to provide intelligent recap 

Intelligent recap automatically inherits your organization’s security, compliance, and privacy policies for Microsoft Teams.

Intelligent recap abides by Microsoft’s commitments to data security and privacy in the enterprise. Data is managed in accordance with our current commitments, while the existing compliance boundaries and privacy protections make intelligent recap the AI solution you can trust. For more information, see [Privacy and Microsoft Teams](../teams-privacy.md) and [regional and country compliance information on the Microsoft Trust Center](https://www.microsoft.com/trust-center/compliance/regional-country-compliance).

Intelligent recap also abides by Microsoft’s commitments to data residency in the enterprise. Data in Teams resides in the geographic region associated with your Microsoft 365 (or Office 365) organization. Intelligent recap is also [multi-geo](/microsoft-365/enterprise/microsoft-365-multi-geo) capable, for tenants that span multiple geographic locations. To review Microsoft’s data residency policy and documentation, see [Data Residency Overview and Definitions](/microsoft-365/enterprise/m365-dr-overview). 

Customer data isn‘t logged or used for any AI model training or testing.

## What parts of intelligent recap are using OpenAI’s GPT Model?

Currently, only the AI-generated notes feature within intelligent recap uses a GPT model from Open AI. However, more AI-based features may leverage GPT in future versions of Teams Premium.

Customer data isn’t shared with non-Microsoft parties, including with Open AI. Microsoft runs the GPT-based models internally using a dedicated GPT service (Azure OpenAI). This dedicated service runs within the compliance boundaries that are used only for Microsoft 365 (and Office 365) services. AI-generated notes and AI-generated tasks call this dedicated and compliant GPT service, as well as other internal AI models, to produce AI-generated notes and tasks.