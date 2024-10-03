---
title: Roll out a Teams Premium trial
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: margidesai
audience: admin
ms.date: 2/26/2024
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
description: Learn how to set up a Teams Premium trial to understand and test premium capabilities in your organization.
---

# Roll out a Teams Premium trial

You can try [Teams Premium](enhanced-teams-experience.md) for free by adding the Teams Premium trial to your organization's Microsoft 365 subscription. The Teams Premium trial provides 25 licenses for 30 days.

Before you start the trial, it's important to plan who will be provided with licenses and what use cases you want to validate during the trial, as well as how you'll collect feedback while the trial is underway.

The following are the basic steps involved in a trial:

1. **Pre-trial planning** - including defining test cases, choosing users, and deciding which feature settings and policies you want to use
1. **Add the trial to your tenant** - including assigning licenses
1. **Administrative setup** - including creating meeting templates, uploading logos and backgrounds, and assigning policies to users. If your organization uses sensitivity labels, this also includes creating meeting sensitivity labels in Microsoft Purview.
1. **Start the trial** - including notifying the trial participants to begin testing the use cases you defined and providing feedback to stakeholders

To better assist with planning for your Teams Premium trial, you can download the [Teams Premium Trial Guide](https://adoption.microsoft.com/files/microsoft-teams/teams-premium-trial-guide.pdf) from Microsoft Adoption and watch [Running a Successful Teams Premium Trial on YouTube](https://www.youtube.com/watch?v=b7z3re0GPd4).

This article covers pre-trial planning and how to add the trial to your tenant and assign licenses. Specific steps for administrators to set up features for the trial are covered in other Teams Premium articles which we link to in the sections below.

## Determine trial participants and stakeholders

Teams Premium provides a variety of enhancements to Teams meetings. We recommend that you find participants from around your organization who can make use of the Teams Premium features in the normal course of their work, as well as stakeholders and specialists who can validate the features for your business, branding, and compliance needs. These may include:

- People who need to present sensitive information in meetings
- Branding and corporate communications specialists
- Compliance and governance specialists
- People who present to large audiences

Not all trial participants need a Teams Premium license. Some people, such as business stakeholders who help define use cases, may not need to test the features themselves.

The following table lists potential trial participants and their roles. For details on roles, see [About admin roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles#commonly-used-microsoft-365-admin-center-roles).

|Who|Their role in the trial|Trial license needed?|
|:--|:---|:--------------------|
|License or User Administrator|Assign Teams Premium trial licenses to trial participants.|No|
|Teams Administrator|Configure Teams Premium settings and policies|If using the Advanced Virtual Appointments activity report|
|Compliance Administrator|Set up and publish sensitivity labels if needed|No|
|Meeting organizers|Schedule meetings where participants can test Teams Premium features|Yes|
|Meeting participants|People in the organization who can attend meetings that use Teams Premium features and give feedback on them|No|
|Compliance specialists|Compliance or governance specialists who can validate use cases for compliant meetings|Yes|

Note that you can use security groups to easily specify who can use specific sensitivity labels.

### Collect feedback from trial participants

We recommend creating a team in Microsoft Teams to gather all the trial participants and stakeholders in one place where they can communicate and share ideas and feedback. You can use channels to organize participants around the different use cases that you want to test.

Beyond Teams chat, there are several options for gathering feedback from trial participants, including [polling attendees during a Teams meeting](https://support.microsoft.com/office/9923b7d4-ea97-4aa2-b8b8-b45fefe7d454) and [adding a poll to your Teams channel or chat](https://support.microsoft.com/office/a3f9112c-01e1-4ee4-bd88-25e4e243b80b).

## Define use cases

The sections below describe the areas where Teams Premium offers enhanced meeting capabilities for your organization. As you prepare for the trial, review each area and determine the use cases that you want to test.

#### Compliant meetings

To help meet your compliance requirements for meetings, Teams Premium provides the following options for meeting organizers:

- Watermarks for attendee video and content shared on screen
- End-to-end encryption
- Options for who can record the meeting

These options are available to meeting organizers with a Teams Premium license.

Teams Premium also includes custom meeting templates and additional options for sensitivity labels that can be used to control many of the [meeting settings that are available to meeting organizers](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e), including those listed above.

If your organization uses sensitivity labels, you can create a combination of sensitivity labels and meeting templates to define meeting experiences for meetings with different sensitivity levels. For ideas on how to use labels and meeting templates for different types of meetings, read [Configure Teams meetings with three tiers of protection](/microsoftteams/configure-meetings-three-tiers-protection).

Sensitivity labels are defined in Microsoft Purview and you can use them in meetings directly or specify them as part of a meeting template.

If your organization doesn't use sensitivity labels, you can control many of the same features by using custom meeting templates alone.

For the trial, you'll want to define the different types of meeting experiences that you want to validate and then determine how you want to use sensitivity labels (if applicable) and meeting templates to make these meeting experiences available to trial participants.

If you use sensitivity labels, we suggest creating temporary labels for the trial and publishing them to your trial participants. This way you don't need to update production labels that are available widely within the organization.

For your trial group, you may want to include people who need to present sensitive information in meetings as well as compliance specialists who can validate the features and settings used with respect to your business requirements.

For more information about using Teams Premium for meeting compliance, see the following references:

- [Require end-to-end encryption for sensitive Teams meetings](end-to-end-encrypted-meetings.md)
- [Require a watermark for sensitive Teams meetings](watermark-meeting-content-video.md)
- [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)

#### Custom meetings

Teams Premium allows organizations to extend their visual identities across the meeting experience by adding logos and backgrounds that are displayed in the meeting lobby background and other places in Teams.

There are three primary ways to customize meetings in Teams Premium:
- **Themes** - logos, images, and colors that represent your organization
- **Backgrounds** - images that people can use as meeting backgrounds when they attend Teams meetings
- **Templates** - preset lists of meeting options for different meeting types

Meeting themes and backgrounds are made available to users through meeting customization policies. Each policy includes:

- One theme with an image, logo, and color selection
- Up to 50 custom background images

As you test themes, you may want to change images, colors, and logos as you go. We recommend that you have a Teams Administrator available who can change theme settings quickly throughout the trial. You can also test multiple themes by creating additional meeting customization policies and assigning them to different trial participants.

Meeting organizers with a Teams Premium license can create meetings using the theme you add, which will be visible to all meeting participants.

For more information about using custom themes and backgrounds in Teams Premium meetings, see the following references:

- [Custom meeting backgrounds for Teams Meetings](custom-meeting-backgrounds.md)
- [Meeting themes for Teams meetings](meeting-themes.md)
- [Use meeting themes for Teams meetings](https://support.microsoft.com/office/fbfd826d-1112-4790-918a-5a82cac8250e)

Custom meeting templates can be used to preset many of the options that are available to meeting organizers, including security, audio and video, recording and transcription, and meeting engagement settings. Settings can be enforced by the templates or meeting organizers can be allowed to change them. Review the options in [Create a custom meeting template in Microsoft Teams](create-custom-meeting-template.md) as you determine what meeting templates you want to create for the trial.

#### Premium events

With premium events, meeting organizers have additional features to help them organize meetings webinars, and town halls, including analytics, enhanced registration, custom emails, and enhanced controls for presenter and attendee video.

Many of these features don't have administrative controls, so you don't need a Teams Administrator to set them up. They're automatically available to meeting organizers who have a Teams Premium license.

The following meeting and webinar features are available in Teams Premium:

- **[Enhanced registration capabilities](https://support.microsoft.com/office/923f382a-0cca-433a-b38d-7461971192d1)** - Additional webinar registration options, including manual registration approval, waitlist, and registration start and end time.

- **Enhanced video feed controls** - Options to decide whose avatars or video feeds to spotlight during a Teams meeting. Available for both meetings and webinars.

- **[Live translated captions](https://support.microsoft.com/office/4be2d304-f675-4b57-8347-cbd000a21260)** - Allows users to see captions translated into the language they're most comfortable with. Available for both meetings and webinars.

- **[Town hall insights in Microsoft Teams](https://support.microsoft.com/office/def99575-61bf-4ea2-ad0e-c6e75dce7741)** - See real-time data during a town hall, including the viewer count and which countries or regions people are joining from.

- **[Manage email communications for Teams town halls and webinars](manage-email-communications.md)** - Administrators can manage whether organizers and co-organizers can edit email templates for their webinars and town halls.

- **[Hide the names of attendees](hide-attendee-names.md)** - Allow meeting and webinar organizers to hide the names and photos of attendees from other attendees in the stage, roster, and chat.

As you determine which users will get trial licenses, consider which of your meeting and webinar organizers can best test these features.

For more information about setting up webinars and town halls, see [Plan for Teams webinars](plan-webinars.md) and [Plan for Teams town halls](plan-town-halls.md).

#### Advanced Virtual Appointments

Teams Premium includes additional features to help your workforce get the most out of the [Virtual Appointments app](/microsoft-365/frontline/virtual-appointments-app). These include:
- SMS notifications to remind attendees of meetings.
- Meeting organizers can view and manage both scheduled and on-demand appointments in the queue.
- Organizational and departmental analytics help you see and understand how your users are working with Virtual Appointments.

Consider which of your meeting organizers should get a license to test SMS notifications and managing appointments in the queue.

Use the [Virtual Appointments usage report](/microsoft-365/frontline/virtual-appointments-usage-report) to understand how your team members are using basic Virtual Appointments features. You can compare this with the [Advanced Virtual Appointments activity report](/microsoft-365/frontline/advanced-virtual-appointments-activity-report), which shows how much your users are utilizing the features in Virtual Appointments that are only available with Teams Premium. You can use these two reports to understand which features are the most useful for your team, and gain insight into the adoption of advanced features within your  organization.

Note that the Teams Administrator requires a trial license to access the Advanced Virtual Appointments activity report.

#### Custom policy packages

A policy package is a collection of predefined policies that you can assign to users or groups who have similar roles in your organization. Teams includes several pre-defined policy packages and Teams Premium allows you to create your own.

If you want to test custom policy packages as part of your trial, see [Managing policy packages in Teams](manage-policy-packages.md) for information.

## Get started with the trial

When you've completed your pre-trial planning, the next step is to add the Teams Premium trial to your Microsoft 365 subscription.

Once you've added the trial, you can do the administrative setup steps to get the trial ready for your users:

- Create the meeting templates that you want to test, both for compliance and custom meetings.
- Create the meeting customization policies that you want to use to test your themes and backgrounds.
- Assign the template and customization policies to the appropriate trial participants.
- If you're using sensitivity labels, create the labels that you want to test and publish them to the trial participants.

Once the administrative setup is complete, notify your trial participants that the trial is underway and have them start testing their use cases.

### Add the Teams Premium trial to your organization and assign licenses

The Teams Premium trial is added from the Microsoft 365 admin center.

To add the Teams Premium trial to Microsoft 365

1. In the Microsoft 365 admin center, expand **Billing**, and then select **Purchase services**.
1. Search for *Teams Premium*.
1. Under **Microsoft Teams Premium Introductory Pricing**, select **Details**.
1. Select **Start free trial**.
1. On the checkout page, select **Try now**.
1. Select **Continue**.

For information about how to assign the licenses to your users, see [Assign Microsoft 365 licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

Note that it may take up to 72 hours for Teams Premium sensitivity label settings to be available in the Microsoft Purview compliance portal.

## Related topics

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)

[Teams Premium deployment guide](https://aka.ms/TeamsPremiumDeployment)

[Teams Premium user guide](https://adoption.microsoft.com/files/microsoft-teams/Microsoft-Teams-Premium-user-guide.pptx)

