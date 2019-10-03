---
title: "Auditing Patients app for Teams IT and compliance admins "
author: jambirk
ms.author: jambirk 
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

An Audit log for Patients app activity allows after-incident response teams to review changes to a patient's Electronic Medical Records (EMR) or Patient Healthcare Information (PHI) and determine if changes or improvements in policy or procedure for PHI access in productivity tools are needed. The audit log events cover actions performed through the Patients app user interface.

## Meet HIPAA requirements

According to HIPAA guidelines, healthcare providers are required to keep records of all access to PHI, so that it is possible for the changes to be audited. Microsoft is committed to its enterprise customers using Microsoft Teams, and to helping them meet HIPAA requirements and controls. Access to PHI via the Patients App is fully tracked and logs are made available in the M365 Security and Compliance center, as described in the [Audit Log Search functionality](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) article.

> [!IMPORTANT]
> The burden of maintaining patient privacy is placed on the healthcare provider by law. The law entitles patients to privacy, and requires that an IT admin or HIPAA controller can easily determine which nurse, clinician, or social worker accessed or altered patient records. One of the most common examples of a PHI access violation is access to VIP patients. The audit log functionality is required to conduct investigations of any PHI access violation, and to meet HIPAA requirements.

<!-- add an image from the security and compliance center audit log search page showing an event, Ansuman please let me know whether we need to copy an existing screen shot (and which one) or grab a new one -->

## Enable Audit logs for the Patients App

An Audit is dependant on several prior configurations:

1. The admin would have to work with their FHIR service provider to have EMR in a format used by the Patients App. See [Integrating Electronic Healthcare Records into Microsoft Teams](patients-app.md).
2. A healthcare provider admin would have to enable the patients app in Teams Admin center. See [Manage app setup policies in Microsoft Teams](../../teams-app-setup-policies.md) and related articles for more information.
3. The admin would have to enable activity audits in O365, the same way they enable any activity log audit in Office 365, as described in [Before you begin](https://docs.microsoft.com/en-us/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance#before-you-begin) and [Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search). If audit logging is already on, nothing special is needed for the Patients App. Any time a healthcare provider installs and runs the app within a Team, the audit logs record their PHI activity.
4. The admin would then need to announce availability of the Patients app, and Healthcare workers would have to start generating activity to be included in an audit.

<!-- add link out to client doc when available -->

## Run an audit

For instructions on running a search of the activity log, see [Search the audit log](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#search-the-audit-log).

## Logged activities for Patients app

The Patients app has its own logged activities, listed in the following table:

|Friendly name |Operation|Description|
|:---|:---|:---|
| Viewed patient list | PatientListView | A user viewed a patient list.|
| Viewed patient details | PatientView | A user viewed a patient record.|
| Created patient list | PatientListCreate | A user created a list of patients.|
| Deleted patient list | PatientListDelete | A user deleted a list of patients.|
| Added patient to list | PatientListAddPatient | A patient was added to a list of patients. |
| Removed patient from list|PatientListRemovePatient | A patient was removed from a list of patients. |
| Renamed patient list | PatientListRename | A list of patients was renamed. |
| Edited a list column | PatientListEditColumns | A column in a list of patients was edited (added or removed). |
| Added note for patient | PatientNoteAdd | A note was added to a patient record. |
| Edited patient details | PatientDetailsEdit | A detail on a patient record was edited. |
| Exported patient data | ExportInitiation | A patient record was exported <!-- from EMR? to where? --> by the app. |
| Created patient schema | PatientSchemaCreate | A new schema for patients was created. |
| Updated patient schema | PatientSchemaUpdate  | Updated existing schema for patients. |
| Searched for a patient from EHR | PatientSearch | Searched a patient record in the EHR service. |
| Connected to EMR  | EHRConnectionSet | Set the EHR FHIR Server connection string. |
||||

You can customize your Audit as needed to search for or filter on any of these logged activities.

Logged activities for Microsoft Teams in general are described in [Microsoft Teams activities](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#microsoft-teams-activities).

## Related topics

[Search the Office 365 Audit log](https://docs.microsoft.com/en-us/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)

[Integrating Electronic Healthcare Records into Microsoft Teams](patients-app.md)
