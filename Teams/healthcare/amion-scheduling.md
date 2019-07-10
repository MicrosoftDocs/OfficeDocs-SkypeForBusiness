---
title: "AMiON scheduling app with Teams "
author: jambirk
ms.author: jambirk 
manager: serdars
audience: ITPro
ms.topic: article 
ms.service: msteams 
search.appverid: MET150
localization_priority: Normal
MS.collection: Teams_ITAdmin_PracticalGuidance
appliesto:
- Microsoft Teams
ms.reviewer: vanido, acolonna
description: scheduling interop with shifts
---

# AMiON scheduling app for Teams 

The [AMION scheduling app](http://amion.com) displays on-call data for hospitals and gives users an option to import that data into Shifts. This import happens seamlessly using the Graph APIs without further user input.

Admins in a healthcare environment can choose to restrict access to third party apps, but if you wish to use the patients app and shifts you will probably want to enable this app as well. We strongly recommend enabling this app and making it prominent in your organization's [app setup policies](../teams-app-setup-policies.md).

## Overview

AMiON is a popular hospital scheduling system used to assign physicians to on-call schedules and shifts. This app is used by over 250,000 healthcare providers. It enables schedulers to set preferences for each employee, date range, and department, and ensure there is coverage for each department. Typically, a department or hospital sets the schedule for multiple weeks or a month and then employees can trade or swap shifts after it is published. Changes to the schedule after it is published are not usually written back to AMiON. One challenge clinicians face is that not every clinician has access to the AMiON schedule and so clinicians need to call the operator to know who is filling a specific role (such as: who is the on-call cardiologist right now?).  

Hospitals can now put AMiON schedules into Shifts so that employees can reference the schedule. Once the data from AMiON is in Shifts  clinicians will be able to chat or @mention users in Teams to quickly find the right resource in the hospital. For example, in a channel mentioning @OnCallCardiologist, or directly sending a chat to the role of OnCallCardiologist.

## Role-Based Dynamic Tags with Targeting  

 AMiON  already has defined roles, these flow through to Shifts as a Shift Group, making it addressable from within Teams. For example, Daniel, a nurse scheduler runs an import from AMiON to Shifts and has the option to pull tags in from Shifts selected. One of the shifts imported is for Dr Trish, who is the on-call cardiologist Tuesday from 6am-6pm. On Tuesday, Chris, a new nurse arrives at work and needs to page the on-call cardiologist. Chris @mentions the @on-call-cardiologist, which sends Trish a message.  

## Enable AMiON scheduling

AMiON is enabled or disabled for a healthcare organization the same as any other app. See [Manage app setup policies in Microsoft Teams](../teams-app-setup-policies.md) for specifics.


## Related topics

[Manage app setup policies in Microsoft Teams](../teams-app-setup-policies.md)
