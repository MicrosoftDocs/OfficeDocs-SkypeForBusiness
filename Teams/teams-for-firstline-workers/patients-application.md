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

### Opening the Patients Application

The Patients Application, if available in your team, is located in the General channel as a tab. Clicking on this will open the app directly if your organization supports single sign on. Otherwise, the app will prompt you to login using your employer-supplied EHR credentials.

### Creating a patient list

With the Patients Application, users in a Team can create lists to categorize and sort patients. For example, clinicians may want to curate a list of patients that they can label as High Risk. Lists can be created or renamed by navigating to dropdown located in the top left. Clicking Add list will enable the creation of a new list, whereas clicking on  … > Rename will allow you to rename an existing list, such as the default New List created when the application is first run.  

### Adding a patient to a list

Patients can be added to an existing list by clicking on + Add patient, located underneath the list name in the top left of the screen. For safety and compliance reasons, you can search for patients by either using a combination of at least three of the following fields:

1. First name
2. Last name
3. Birth date (required)
4. Gender

Or with a unique patient identifier – your healthcare organization may prefer one over the other:

1. MRN (Medical Record Number)
2. ID

Clicking search will reveal a list of matching patients, and clicking on the patient will add them to the list.

### Patient list  

The list can be sorte
