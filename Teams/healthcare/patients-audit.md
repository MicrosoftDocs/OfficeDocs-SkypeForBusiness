---
title: "Auditing Patients app for Teams admins "
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

Keeping an Audit log for Patients app activity allows after-incident response teams to review changes to patients records and determine if changes or improvements in policy or procedure are needed.

<!-- remember to add link to security page and from security page  -->

## Usage example

Why would an admin need to enable this feature or perform this task in real life? What questions does this answer, or what problem does it solve? Answer the question in the back of the Admin's mind: "Why is this worth my time?"

Could sometimes be a before/after illustration that shows something going wrong because the feature isn't available or being used, and then the same situation with a better outcome because the feature helped the users.

<!-- Ansuman will add-->

## Configure Patients app

For information on how to prepare your environment to use Patients app, see [Integrating Electronic Healthcare Records into Microsoft Teams](../expand-teams-across-your-org/healthcare/patients-app.md).  You will also need to see [Manage app setup policies in Microsoft Teams](../teams-app-setup-policies.md) to enable Patients app for your organization.

<!-- add link out to client doc -->

You enable activity audits for Patients App the same way you would any other activity in Office 365 as described in [Turn Office 365 audit log search on or off](https://docs.microsoft.com/office365/securitycompliance/turn-audit-log-search-on-or-off#turn-on-audit-log-search).

## Run an audit

For instructions on running a search of the activity log, see 
[Search the audit log](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#search-the-audit-log).

### (Optional) Use case
<!-- Might remove this section -->
Admin Bob is asked to check on Patients app activity for a specific date where some sort of activity went wrong. Step through the creation of the audit  of the activity logs that answers the question.

This is a simple illustration of how to do this, with a vertical-centered example.

## Logged activities for Patients app

Logged activities for Microsoft Teams are described in [Microsoft Teams activities](https://docs.microsoft.com/office365/securitycompliance/search-the-audit-log-in-security-and-compliance#microsoft-teams-activities).

The Patients app has its own logged activities, listed in the following table:

|Friendly name |Operation|Description|
|:---|:---|:---|
| Viewed list of patients |PatientListViewed| A user viewed a patient list.|
| Viewed patient record  | PatientViewed|A user viewed a patient record. |
| Looked up patient record| PatientLookedup | A user looked up a patient record.|
| Created a patient list|PatientListCreated |A user created a list of patients. |
| Deleted patient list | PatientListDeleted |A user deleted a list of patients. |
| Added a patient to a list| PatientListPatientAdded |A patient was added to a list of patients. |
| Removed a patient from a list|PatientListPatientRemoved |A patient was removed from a list of patients. |
| Renamed a patient list |PatientListRename | A list of patients was renamed. |
|Edited a list column|PatientListColumnEdited | A column in a list of patients was edited (added or removed). |
|Added a note |PatientNoteAdded | A note was added to a patient record. |
|Edited a detail | PatientDetailEdited | |
||PatientDataExported | |
||PatientSchemaCreated | |
||PatientSchemaUpdated| |
||EMRConnectionSet ||
||||



## Related topics

[Integrating Electronic Healthcare Records into Microsoft Teams](../expand-teams-across-your-org/healthcare/patients-app.md)
