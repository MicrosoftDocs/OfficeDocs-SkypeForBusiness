---
title: Manage the registration form for webinars in Microsoft Teams
author: wlibebe
ms.author: wlibebe
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: justle
ms.date: 7/29/2024
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to manage the registration form for webinars in Microsoft Teams for admins. Require attendees to answer required questions, custom questions, and standard questions.
appliesto: 
  - Microsoft Teams
---
# Manage the registration form for webinars

**APPLIES TO:** ✖️Meetings ✔️Webinars ✖️Town halls

## Overview

The registration form allows organizers to collect information from attendees when they register for webinars. As an admin, you can manage whether organizers can require attendees to answer standard and custom questions on the registration form.
There are three categories of questions on the registration form:

1. **Required questions** - All attendees are required to answer these questions; default questions can't be removed.
   - First name
   - Last name
   - Microsoft consent field
2. **Standard questions** - These preset questions can't be edited by organizers. Attendees aren't required to answer predefined questions, but you can allow organizers to make them required.
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

## Manage the registration form

You can use the Teams admin center or PowerShell to manage the registration form.

|Teams admin center policy option |Parameter value in PowerShell | Behavior |
|---------|---------|---------------|
|Required only|DefaultOnly | Organizers with this assigned policy can only require attendees to answer required questions on the registration form. |
|Standard and required only |DefaultAndPredefinedOnly | Organizers with this assigned policy can only require attendees to answer standard and required questions on the registration form.|
|Custom, standard, and required |AllQuestions | **This is the default value**. Organizers with this assigned policy can require attendees to answer standard, required, and custom questions on the registration form.|

### Use the Teams admin center to manage the registration form

You can use the Teams admin center to manage the types of questions an organizer can require attendees to answer when registering for webinars in your organization.

Follow these steps in the Teams admin center to manage the registration form:

1. Open the Teams admin center.
2. Expand **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Use the dropdown for the **Webinar registration form questions** setting to select your choice from the following options:

   - Required only
   - Standard and required only
   - Custom, standard, and required
6. Select **Save**

## Use PowerShell to manage the registration form

You can use PowerShell to manage the types of questions an organizer can require attendees to answer when registering for webinars. To manage the registration form questions, use the **`-AllowedQuestionTypesInRegistrationForm`** parameter in the **CsTeamsEventsPolicy** cmdlet.

To only allow organizers to require required questions on the registration form, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedQuestionTypesInRegistrationForm DefaultOnly
```

To only allow organizers to require standard and required questions on the registration form, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedQuestionTypesInRegistrationForm DefaultAndPredefinedOnly
```

To allow organizers to require standard, required, and custom questions on the registration form, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedQuestionTypesInRegistrationForm AllQuestions
```

## Related articles

- [Issues that affect Teams webinars](/microsoftteams/troubleshoot/meetings/issues-with-webinars)
- [Set up webinars](set-up-webinars.md)
- [Plan webinars](plan-webinars.md)
