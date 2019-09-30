---
title: "Auditing Patients app for Teams IT and compliance admins "
author: jambirk, anach
ms.author: jambirk, anach 
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto: Microsoft Teams
ms.reviewer: anach
description: Patients app for Teams admins
---

# Auditing logs for Patients app

Keeping an Audit log for Patients app activity allows after-incident response teams to review changes to a patient's Electronic Medical Records (EMR) and determine if changes or improvements in policy or procedure for PHI access in productivity tools are needed. The audit log events cover an extensive set of UI actions possible through the Patients app UI. 

<!-- remember to add link to security page and from security page  -->

## Usage example

Why would an admin need to enable this feature or perform this task in real life? 

Per HIPAA guidelines, all access to PHI must be audited. Microsoft is committed to help its enterprise customers using Microsoft Teams meet HIPAA requirements and controls and therefore access to PHI via the Patients App is fully audited and made available in the [Audit Log Search functionality](https://docs.microsoft.com/en-us/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) in the M365 Security and Compliance center.

The burden of patient privacy is clearly on the provider and the law entitles patients to privacy. An IT or HIPAA controller/admin can easily determined which nurse, clinician or social worker acccessed which patient records or altered them. One of the most common examples of PHI access violation is access to VIP patients.Therefore, the audit log functionality helps in investigations around PHI access violation. 

<!-- add an image from the security and compliance center audit log search page showing an event-->

## Enabling Audit logs for the Patients App

<!-- add link out to client doc -->

You enable activity audits for Patients App the same way you would any other activity in Office 365 as described in [Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search). If audit logging is already on, you don't need to do anything special for the Patients App. Anytime users intall and run it within a Team, the audit logs will flow through. 

## Run an audit

For instructions on running a search of the activity log, see 
[Search the audit log](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#search-the-audit-log).

<!-- Need to update audit log docs article with Mark Johnson to add Teams healthcare events too -->

## Logged activities for Patients app

Logged activities for Microsoft Teams are described in [Microsoft Teams activities](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#microsoft-teams-activities).

The Patients app has its own logged activities, listed in the following table:

<!-- a lot of this is first-pass guesswork. @ansuman please review-->

|Friendly name |Operation|Description|
|:---|:---|:---|
| Viewed patient list | PatientListView | A user viewed a patient list.|
| Viewed patient details | PatientView | A user viewed a patient record. |
| Created patient list | PatientListCreate | A user created a list of patients. |
| Deleted patient list | PatientListDelete | A user deleted a list of patients. |
| Added patient to list | PatientListAddPatient | A patient was added to a list of patients. |
| Removed patient from list|PatientListRemovePatient | A patient was removed from a list of patients. |
| Renamed patient list | PatientListRename | A list of patients was renamed. |
| Edited a list column | PatientListEditColumns | A column in a list of patients was edited (added or removed). |
| Added note for patient | PatientNoteAdd | A note was added to a patient record. |
| Edited patient details | PatientDetailsEdit | A detail on a patient record was edited. |
| Exported patient data | ExportInitiation | A patient record was exported <!-- from EMR? to where? --> by the app. |
| Created patient schema | PatientSchemaCreate | Created a new schema for patients. |
| Updated patient schema | PatientSchemaUpdate  | Updated existing schema for patients. |
| Searched for a patient from EHR | PatientSearch | Searched a patient record in the EHR service. |
| Connected to EMR  | EHRConnectionSet | Set the EHR FHIR Server connection string. |
||||

## Related topics
[Searching the Office 365 Audit log](https://docs.microsoft.com/en-us/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)
[Integrating Electronic Healthcare Records into Microsoft Teams](../expand-teams-across-your-org/healthcare/patients-app.md)
