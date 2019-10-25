---
title: "Patients app for Teams admins "
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

# Patients app overview

The Patients application is a Microsoft Teams store app available to all Teams users. The app enables patient care teams consisting of clinical workers (e.g. Nurses, physicians, social workers) can curate and review lists of patients for scenarios ranging from rounds and interdisciplinary team meetings to general patient monitoring.   

The app has two modes: 

- The EMR Connected mode that connects to EMRs through FHIR. The EMR Connected mode app stays in private preview and interested customers or admins may request access to the app by dropping Microsoft an email at teamsforhealthcare@service.microsoft.com with information about their Office 365 tenant. 
- The manual mode that enables care teams to manually add/bring in patient information. The application is available in the Teams app store for end users to download by default and is in public preview. The app can be restricted to certain sections of users using [app setup policies in Microsoft Teams](../../teams-app-setup-policies.md)



## Usage example

During rounding sessions on every shift in medical wards, clinicians gather at the nursing station to discuss the latest updates on the progress with patients in the ward.  They highlight the key critical metrics (not necessarily medical or that its explicit on the patients’ medical records) and ensure the patient is on the right glide path to discharge based on their diagnosis. In order to round around these patients, the charge nurse sets up the patient app in a team where all the clinicians are added and adds patients to a patient list. During the rounds, the nurses and the other care givers for the patient access Microsoft Teams and the Patients app on their mobile devices and update relevant patient information on their device and then everyone else in the care team can see those updates and notes and stay in sync. Twice a day, at the start and end of a shift, they also have multi-displicinary team meetings to go over the patient list and use the Patients App to ground themselves and share information about each patient using the Patients app on a large display screen. Often times, certain clinicians may also dial in to these Teams meetings remotely and still be part of the discussion. 

## Configure Patients app

For information on how to prepare your environment to use the EMR mode Patients app, see [Integrating Electronic Healthcare Records into Microsoft Teams](patients-app.md). You will also need to see [Manage app setup policies in Microsoft Teams](../../teams-app-setup-policies.md) to enable Patients app for your organization.

<!-- For information on how your end users can access and install the Patients App to a team that they own or manage, you will need to see [End user documentation for the Patients App]() -->

<!-- add link out to client doc, doesn't seem to be available yet, Grant is finalizing -->

## Related topics

[Integrating Electronic Healthcare Records into Microsoft Teams](patients-app.md)
