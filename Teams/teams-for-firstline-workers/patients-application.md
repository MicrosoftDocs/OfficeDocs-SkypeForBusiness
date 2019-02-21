---
title: Article title goes here       
author: jambirk           
ms.author: jambirk        
manager: serdars                    
audience: ITPro            
ms.topic: article                   
ms.service: msteams         
search.appverid: MET150
localization_priority: Normal
ms.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: 
description: Tasks and activities required for Teams service management, including monitoring service health, and assessing and ensuring network quality and usage.
---

# Introduction

The Patients Application is Microsoft Teams’ first-party care collaboration solution for healthcare professionals. Using the Patients Application, users can curate and review lists of patients for scenarios ranging from rounds and interdisciplinary team meetings to general patient monitoring.

The Microsoft Teams Patients Application connects to FHIR (Fast Healthcare Interoperability Resources) conforming EHR (Electronic Health Records) servers directly, and can connect to non-conforming EHR servers through a secondary integration server often facilitated by Microsoft Interop Partners.

> [!NOTE]
> Only team owners can initiate the EHR connection process. More information regarding the technical aspects of the application can be found HERE

The Patients Application does the following

- Connects to a  Fast Healthcare Interoperability Resources (FHIR) server
- For Team Owners
- Integrates with your EHR using the [FHIR protocol](http://hl7.org/fhir/R4/index.html)
- If any resources are missing in Patients this means the data is missing, not an issue with the Patients Application


Welcome to the Microsoft Teams Patients Application, Microsoft Teams’ first party care collaboration solution for healthcare professionals. Using the Patients Application, clinical users can curate and review lists of patients for scenarios ranging from rounds and interdisciplinary team meetings to general patient monitoring.

The Microsoft Teams Patients Application connects to FHIR (Fast Healthcare Interoperability Resources) conformant EHRs directly, and can connect to non-conformant EHRs through a secondary FHIR integration server often facilitated by Microsoft Interop Partners. Note that only team owners can initiate the EHR connection process. More information regarding the technical aspects of the application can be found HERE

The Patients Application, if available in your team, is present in the General channel as a tab. Clicking on this will open the app directly if your organization supports single sign on. Otherwise, the app will prompt you to login using your employer-supplied EHR credentials.