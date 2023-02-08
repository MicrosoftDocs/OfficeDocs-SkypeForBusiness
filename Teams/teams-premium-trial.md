---
title: Roll out a Teams Premium trial
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365solution-overview
  - m365initiative-meetings
  - highpri
appliesto: 
  - Microsoft Teams
description: Learn how to set up a Teams Premium trial to understand and test premium capabilities in your organization.
---

# Roll out a Teams Premium trial

You can try Teams Premium in your organization for free by adding the Teams Premium trial to your organization.

The Teams Premium trial provides 25 licenses for 30 days. Before you start the trial, it's important to plan who will be provided with licenses and what use cases you want to validate during the trial, as well as how feedback will be collected while the trial is underway.

The following table lists some of the people to consider including in the trial.

|Who|Role|Trial license|
|:--|:---|:--------------------|
|Microsoft 365 global administrator|Assign Teams Premium trial licenses to trial participants.|No|
|Teams administrator|Configure Teams Premium settings and policies|No|
|Compliance administrator|Set up and publish sensitivity labels|No|
|Meeting organizers|Schedule meetings where participants can test Teams Premium features|Yes|
|Meeting participants|People in the organization who can attend meetings that use Teams Premium features and give feedback on them|No|
|Compliance specialists|Compliance or governance specialists who can validate use cases for compliant meetings|Yes|

We recommend creating security groups with
- **Compliance testers** - Users who will be testing sensitivity labels and meeting templates in meetings. Sensitivity lables can be published to this group in Microsoft Purview and meeting templates can be made available to this group with a meeting template policy in Teams.
- **Custom meetings testers** - Users who will be testing templates, backgrounds, and themes. Themes, backgrounds, and templates can be assigned to this group by using meetings customization policies.


Before starting the trial:
- Review the [features available in Teams Premium](enhanced-teams-experience.md)
- Define the use cases you want to test and validate
- Assemble a pilot group



1. **Pre-trial planning** including defining test cases, choosing users, and deciding which feature settings and policies you want to use
1. **Add trial to your tenant** including assigning licenses
1. **Administrative setup** including creating meeting templates and sensitivity labels, uploading logos and backgrounds, and assigning policies to users
1. **Start trial**




Figure out:
- Label settings for temporary label
- Template types needed and the settings for each



- Images for custom meeting backgrounds
- Logo and images for custom meeting theme
- 

[Configure Teams meetings with three tiers of protection](/microsoftteams/configure-meetings-three-tiers-protection)


## Define use cases

Create post-meeting surveys for participants
[Poll attendees during a Teams meeting](https://support.microsoft.com/office/9923b7d4-ea97-4aa2-b8b8-b45fefe7d454)

[Add a poll to your Teams channel or chat](https://support.microsoft.com/office/a3f9112c-01e1-4ee4-bd88-25e4e243b80b)


## Find a pilot group

- People who hold sensitive meetings
- Branding or comms people

Create a team in Teams for trial participants.

Teams admin / liaison who can make updates to policies, upload new themes, etc.

Decision makers who can evaluate the feedback and sit in on some meetings to see how things work. They may not need a license unless they're testing features themselves.

Give licenses to organizers
Have a feedback line for meeting participants

Not all pilot group members get a license. Some may be business stakeholders who help define use cases, some may be users with licenses.

## Get started

Global admin to assign licenses. They don't need one.
License for Teams admin so they can set things up
License for compliance admin so they can set up labels
Upload images
Assign policies
Create label and publish to security group
Assign licenses to the preview users


## Compliant meetings

Find people who need to organize sensitive meetings
Create a temporary label

Use labels and templates together

## Custom meetings

Use templates, backgrounds, and themes

## Premium events


## Advanced Virtual Appointments

## Add the Teams Premium trial and assign licenses

The Teams Premium trial is added from the Microsoft 365 admin center.

To add the Teams Premium trail to Microsoft 365
1. In the Microsoft 365 admin center, expand **Billing**, and then select **Purchase services**.
1. Search for *Teams Premium*.
1. Under **Microsoft Teams Premium Trial**, select **Details**.
1. Select **Start free trial**.
1. On the checkout page, select **Try now**.
1. Select **Continue**.

Note that it may take up to 72 hours for Teams Premium sensitivity label settings to be available in the Microsoft Purview compliance portal.


## Related topics

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)
