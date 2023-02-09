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

You can try [Teams Premium](enhanced-teams-experience.md) for free by adding the Teams Premium trial to your organization. The Teams Premium trial provides 25 licenses for 30 days.

Before you start the trial, it's important to plan who will be provided with licenses and what use cases you want to validate during the trial, as well as how you'll collect feedback while the trial is underway.

The following are the basic steps involved in the trial:

1. **Pre-trial planning** including defining test cases, choosing users, and deciding which feature settings and policies you want to use
1. **Add trial to your tenant** including assigning licenses
1. **Administrative setup** including creating meeting templates and sensitivity labels, uploading logos and backgrounds, and assigning policies to users
1. **Start the trial** including notifying the trial participants to begin testing the use cases you defined and providing feedback to stakeholders

This article covers pre-trial planning and how to add the trial to your tenant and assign licenses. Specific steps for administrators to set up features for the trial are covered in other Teams Premium articles which we link to in the sections below.

## Determine trial participants and stakeholders

Teams Premium provides a variety of enhancements to Teams meetings. We recommend that you find participants from around your organization who can make use of the Teams Premium features in the normal course of their work, as well as stakeholders and specialists who can validate the features for your business, branding, and compliance needs.

The following table lists some of the people to consider including in the trial.

|Who|Their role in the trial|Trial license?|
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



## Define use cases

Create post-meeting surveys for participants


## Find a pilot group

Look for the following types of people in your organization:

- People who need to present sensitive information in meetings
- Branding and corporate communications specialists
- Compliance and governance specialists
- People who present to large audience

Create a team in Teams for trial participants.

Teams admin / liaison who can make updates to policies, upload new themes, etc.

Decision makers who can evaluate the feedback and sit in on some meetings to see how things work. They may not need a license unless they're testing features themselves.

Give licenses to organizers
Have a feedback line for meeting participants

Not all pilot group members get a license. Some may be business stakeholders who help define use cases, some may be users with licenses.

You can create a team in Microsoft Teams to gather all the pilot participants and stakeholders in one place where they can communicate and share ideas and feedback. Use channels to organize participants around the different use cases that you want to test.

Beyond Teams chat, there are several options for gathering feedback from trial participants, including [polling attendees during a Teams meeting](https://support.microsoft.com/office/9923b7d4-ea97-4aa2-b8b8-b45fefe7d454) and [adding a poll to your Teams channel or chat](https://support.microsoft.com/office/a3f9112c-01e1-4ee4-bd88-25e4e243b80b).



## Get started

Global admin to assign licenses. They don't need one.
License for Teams admin so they can set things up
License for compliance admin so they can set up labels
Upload images
Assign policies
Create label and publish to security group
Assign licenses to the preview users


## Compliant meetings

To help meet your compliance requirements for meetings, Teams Premium provides sensitivity label controls and custom meeting templates that you can use to define the meeting experience.

By using sensitivity labels in Microsoft Purview and Teams meeting templates, you can enforce meeting features such as watermarks and encryption, and control many of the meeting settings that are available to meeting organizers.

You can create a combination of sensitivity labels and meeting templates to define meeting experiences for meetings with different sensitivity levels. For ideas on how to use labels and meeting templates for different types of meetings, read [Configure Teams meetings with three tiers of protection](/microsoftteams/configure-meetings-three-tiers-protection).

For the trial, you'll want to define the different types of meeting experiences that you want to validate and then determine how you want to use sensitivity labels and meeting templates to make these meeting experiences available to trial participants.

We suggest creating temporary sensitivity labels for the trial and publishing them to your trial participants. This way you don't need to update production labels that are available widely within the organization.

For your trial group, you may want to include people who need to present sensitive information in meetings as well as compliance specialists who can validate the features and settings used against your business requirements.

For more information about using Teams Premium for meeting compliance, see the following references:

- [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md)
- [Require a watermark for sensitive Teams meetings](watermark-meeting-content-video.md)
- [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

## Custom meetings

Teams meetings allows organizations to extend their visual identities across the meeting experience by adding logos and backgrounds that are displayed in the meeting lobby background and other places in Teams.

There are three primary ways to customize meetings in Teams Premium:
- **Themes** - logos and colors that represent your organization
- **Backgrounds** - images that people can use when they attend Teams meetings
- **Templates** - preset lists of meeting options for different meeting types

Each of these must be set up and maintained by a Teams administrator.

Upload images that people can use when they attend Teams meetings. Select up to 50 images that you'd like to add. These images will appear on users' interfaces in order of upload. 

Add a theme to customize the look of your organization's Teams meetings with images and colors that represent your organization. Meeting organizers with a Teams Premium license can create meetings using the theme you add, which will be visible to all meeting participants.


1 theme per policy
work with Teams admin to swap out materials
create multiple policies and assign to different participants


Meeting themes
Use logos, images, and colors from your organization to create a meeting theme. You can apply the theme to all meetings now, or save your work to apply it later. Preview the theme before applying.
Logos appear in the meeting lobby and other places in Teams.
Accepted file formats are PNG and JPEG. File must be less than 5 MB, and must be at least 576 by 576 pixels.
Images appear in the meeting lobby background and other places in Teams.
set the color of the buttons and other details in meetings.

Use templates, backgrounds, and themes
- Template types needed and the settings for each

- [Custom meeting backgrounds for Teams Meetings](custom-meeting-backgrounds.md)
- [Meeting themes for Teams meetings](meeting-themes.md)
- [Use meeting themes for Teams meetings](https://support.microsoft.com/office/fbfd826d-1112-4790-918a-5a82cac8250e)



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
