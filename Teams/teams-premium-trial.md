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

1. **Pre-trial planning** - including defining test cases, choosing users, and deciding which feature settings and policies you want to use
1. **Add trial to your tenant** - including assigning licenses
1. **Administrative setup** - including creating meeting templates and sensitivity labels, uploading logos and backgrounds, and assigning policies to users
1. **Start the trial** - including notifying the trial participants to begin testing the use cases you defined and providing feedback to stakeholders

This article covers pre-trial planning and how to add the trial to your tenant and assign licenses. Specific steps for administrators to set up features for the trial are covered in other Teams Premium articles which we link to in the sections below.

## Determine trial participants and stakeholders

Teams Premium provides a variety of enhancements to Teams meetings. We recommend that you find participants from around your organization who can make use of the Teams Premium features in the normal course of their work, as well as stakeholders and specialists who can validate the features for your business, branding, and compliance needs. These may include:

- People who need to present sensitive information in meetings
- Branding and corporate communications specialists
- Compliance and governance specialists
- People who present to large audiences

Not all trial participants need a Teams Premium license. Some people, such as business stakeholders who help define use cases, may not need to test the features themselves.

The following table lists potential trial participants and their roles.

|Who|Their role in the trial|Trial license?|
|:--|:---|:--------------------|
|Microsoft 365 global administrator|Assign Teams Premium trial licenses to trial participants.|No|
|Teams administrator|Configure Teams Premium settings and policies|No|
|Compliance administrator|Set up and publish sensitivity labels|No|
|Meeting organizers|Schedule meetings where participants can test Teams Premium features|Yes|
|Meeting participants|People in the organization who can attend meetings that use Teams Premium features and give feedback on them|No|
|Compliance specialists|Compliance or governance specialists who can validate use cases for compliant meetings|Yes|



You can use security groups to easily assign policies in Teams and to specify who can use specific sensitivity labels. We recommend creating security groups for the following trial participants:

- **Compliance testers** - Users who will be testing sensitivity labels and meeting templates in meetings. Sensitivity labels can be published to this group in Microsoft Purview and meeting templates can be made available to this group with a meeting template policy in Teams.
- **Custom meetings testers** - Users who will be testing templates, backgrounds, and themes. Themes, backgrounds, and templates can be assigned to this group by using meetings customization policies.



### Collect feedback from trial participants

We recommend creating a team in Microsoft Teams to gather all the trial participants and stakeholders in one place where they can communicate and share ideas and feedback. You can use channels to organize participants around the different use cases that you want to test.

Beyond Teams chat, there are several options for gathering feedback from trial participants, including [polling attendees during a Teams meeting](https://support.microsoft.com/office/9923b7d4-ea97-4aa2-b8b8-b45fefe7d454) and [adding a poll to your Teams channel or chat](https://support.microsoft.com/office/a3f9112c-01e1-4ee4-bd88-25e4e243b80b).

## Define use cases

The sections below describe the areas where Teams Premium offers enhanced meeting capabilities for your organization. As you prepare for the trial, review each area and determine the use cases that you want to test.

#### Compliant meetings

To help meet your compliance requirements for meetings, Teams Premium provides sensitivity label controls and custom meeting templates that you can use to define the meeting experience.

By using sensitivity labels in Microsoft Purview and Teams meeting templates, you can enforce meeting features such as watermarks and encryption, and control many of the [meeting settings that are available to meeting organizers](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e).

You can create a combination of sensitivity labels and meeting templates to define meeting experiences for meetings with different sensitivity levels. For ideas on how to use labels and meeting templates for different types of meetings, read [Configure Teams meetings with three tiers of protection](/microsoftteams/configure-meetings-three-tiers-protection).

For the trial, you'll want to define the different types of meeting experiences that you want to validate and then determine how you want to use sensitivity labels and meeting templates to make these meeting experiences available to trial participants.

We suggest creating temporary sensitivity labels for the trial and publishing them to your trial participants. This way you don't need to update production labels that are available widely within the organization.

For your trial group, you may want to include people who need to present sensitive information in meetings as well as compliance specialists who can validate the features and settings used with respect to your business requirements.

For more information about using Teams Premium for meeting compliance, see the following references:

- [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md)
- [Require a watermark for sensitive Teams meetings](watermark-meeting-content-video.md)
- [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

#### Custom meetings

Teams meetings allows organizations to extend their visual identities across the meeting experience by adding logos and backgrounds that are displayed in the meeting lobby background and other places in Teams.

There are three primary ways to customize meetings in Teams Premium:
- **Themes** - logos, images, and colors that represent your organization
- **Backgrounds** - images that people can use as meeting backgrounds when they attend Teams meetings
- **Templates** - preset lists of meeting options for different meeting types

Meeting themes and backgrounds are made available to users through meeting customization policies. Each policy includes:

- One theme with an image, logo, and color selection
- Up to 50 custom background images

As you test themes, you may want to change images, colors, and logos as you go. We recommend that you have a Teams administrator available who can change theme settings quickly throughout the trial. You can also test multiple themes by creating additional meeting customization policies and assigning them to different trial participants.

Meeting organizers with a Teams Premium license can create meetings using the theme you add, which will be visible to all meeting participants.

For more information about using custom themes and backgrounds in Teams Premium meetings, see the following references:

- [Custom meeting backgrounds for Teams Meetings](custom-meeting-backgrounds.md)
- [Meeting themes for Teams meetings](meeting-themes.md)
- [Use meeting themes for Teams meetings](https://support.microsoft.com/office/fbfd826d-1112-4790-918a-5a82cac8250e)

Custom meeting templates can be used to preset many of the options that are available to meeting organizers, including security, audio and video, recording and transcription, and meeting engagement settings. Settings can be enforced by the templates or meeting organizers can be allowed to change them. Review the options in [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md) as you determine what meeting templates that you want to create for the trial.

#### Premium events

Premium events

#### Advanced Virtual Appointments

Advanced virtual appointments

## Get started with the trail

When you've completed your pre-trial planning, the next step is to add the Teams Premium trial to your Microsoft 365 subscription.

Once you've added the trial, you can do the administrative setup steps to get the trial ready for your users:

- Create the sensitivity labels that you want to test and publish them to the trial participants.
- Create the meeting templates that you want to test, both for compliance and custom meetings.
- Create the meeting customization policies that you want to use to test your themes and backgrounds.
- Assign the template and customization policies to the appropriate trial participants.

Once the administrative setup is complete, notify your trial participants that the trial is underway and have them start testing their use cases.

### Add the Teams Premium trial to your organization and assign licenses

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
