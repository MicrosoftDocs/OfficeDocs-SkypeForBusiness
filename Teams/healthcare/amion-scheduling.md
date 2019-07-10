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

Admins in a healthcare environment can choose to restrict access to third party apps, but if you wish to use the patients app and shifts you will probably want to enable this app as well.

## Overview

AMiON is a popular hospital scheduling system used to assign physicians to on-call schedules and shifts. This app is used by over 250,000 healthcare providers. It enables schedulers to set preferences for each employee, date range, and department, and ensure there is coverage for each department. Typically, a department or hospital sets the schedule for multiple weeks or a month and then employees can trade or swap shifts after it is published. Changes to the schedule after it is published are not usually written back to AMiON. One challenge clinicians face is that not every clinician has access to the AMiON schedule and so clinicians need to call the operator to know who is filling a specific role (such as: who is the on-call cardiologist right now?).  

Hospitals can now put AMiON schedules into Shifts so that employees can reference the schedule. Once the data from AMiON is in Shifts  clinicians will be able to chat or @mention users in Teams to quickly find the right resource in the hospital. For example, in a channel mentioning @OnCallCardiologist, or directly sending a chat to the role of OnCallCardiologist.

## [OPTIONAL] Planning for feature

Some features would require careful pre-planning before deployment can begin. For those features, cover what planning tasks customers should complete.

## Configure feature

How do you configure this feature? Cover these points: 

- Are there any prerequisites?

- Is this feature per org or per user? 

- Use PowerShell or UI?

- Short instructions on how to turn on the feature for the organization or for individual users. 

## Manage feature

- Add subsections with basic management tasks that would be required or that we expect customer to perform. 

### Management task 1

### Management task 2

## Security & Compliance

List any security or compliance impact of this feature here. Cover the following:

- Where is the data associated with this feature stored?

- Include any other data implications such as GDPR compliance.


## Related topics

[Manage app setup policies in Microsoft Teams](../teams-app-setup-policies.md)
