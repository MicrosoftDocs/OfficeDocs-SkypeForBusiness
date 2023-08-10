---
title: Manage the registration form for webinars in Microsoft Teams
author: wlibebe
ms.author: wlibebe
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: justle
ms.date: 07/31/2023
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
description: Learn how to manage the registration form for webinars in Microsoft Teams for admins. You can manage default questions, custom questions, and predefined questions.
appliesto: 
  - Microsoft Teams
---
# Manage the registration form for webinars

## Overview

The registration form allows organizers to collect information from attendees when they register for webinars. As an admin, you can manage whether organizers can require attendees to answer predefined and custom questions on the registration form.
There are three categories of questions on the registration form:

1. **Default questions** - All attendees are required to answer these questions; default questions can't be removed.
   - First name
   - Last name
   - Microsoft consent field
2. **Predefined questions** - These preset questions can't be edited by organizers. Attendees aren't required to answer predefined questions, but you can allow organizers to make them required.
    - Address
    - City
    - State
    - Zip or postal code
    - Country/region
    - Industry
    - Job title
    - Organization
    - Legal terms
3. **Custom questions** - Organizers write these customized questions. Attendees aren't required to answer custom questions, but you can allow organizers to make them required.
   - Text input
   - Multiple Choice
   - Checkbox

## Use PowerShell to manage the registration form

To manage the types of questions an organizer can require attendees to answer when registering for webinars, use the **`-AllowedQuestionTypesInRegistrationForm`** parameter in the **CsTeamsEventsPolicy** cmdlet.
The following table shows the behaviors of the settings for the **`-AllowedQuestionTypesInRegistrationForm`** parameter:

|Setting value | Behavior |
|---------|---------------|
|DefaultOnly | Users with this policy can only require attendees to answer default questions on the registration form. |
|DefaultAndPredefinedOnly | Users with this policy can only require attendees to answer default and predefined questions on the registration form.|
|AllQuestions | **This is the default value**. Users with this policy can require attendees to answer default, predefined, and custom questions on the registration form.|

To only allow organizers to require default questions on the registration form, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedQuestionTypesInRegistrationForm DefaultOnly
```

To only allow organizers to require default and predefined questions on the registration form, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedQuestionTypesInRegistrationForm DefaultAndPredefinedOnly
```

To allow organizers to require default, predefined, and custom questions on the registration form, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedQuestionTypesInRegistrationForm AllQuestions
```

## Related articles

- [Set up webinars](set-up-webinars.md)
