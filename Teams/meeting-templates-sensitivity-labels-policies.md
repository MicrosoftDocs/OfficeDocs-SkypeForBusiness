---
title: Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 12/11/2023
audience: admin
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.collection: 
  - m365solution-compliantmeetings
  - m365initiative-meetings
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
description: Learn how to use Teams admin policies together with sensitivity labels and meeting templates to enhance security and compliance for sensitive meetings.
---

# Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

In Teams meetings, meeting organizers can configure [a variety of settings](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e) that determine which features are available in the meeting. As an administrator, you can disable or enforce specific values for these settings by using a combination of admin policies, sensitivity labels, and meeting templates.

[Meeting templates](custom-meeting-templates-overview.md) are created and managed in the Teams admin center. Sensitivity labels are created and manged in the Microsoft Purview compliance portal.

> [!Note]
> Meeting options in sensitivity labels and custom meeting templates require Teams Premium.

By using admin policies, templates, and labels together you can make possible a variety of meeting scenarios to help meet the compliance and business needs for the different departments in your organization.

## Policies, labels, templates, and meetings settings

The following table shows a list of Teams features that may be useful for managing meetings with different compliance needs in your organization and where they can be configured.

|Feature|Teams admin policy|Sensitivity label|Meeting template|Meeting organizer|
|:----|:----|:----|:----|:----|
|Allow camera for attendees|The **Video conferencing** and **Mode for IP video** admin policy settings determine which participants can use their cameras.|No setting|Can prevent or allow camera for attendees. Setting can be enforced or meeting organizer can be allowed to change.|Can prevent or allow camera for attendees if not locked by a template.|
|Allow mic for attendees|The **Mode for IP audio** setting determines which participants can use their mics.|No setting|Can prevent or allow mic for attendees. Setting can be enforced or meeting organizer can be allowed to change.|Can prevent or allow mic for attendees if not locked by a template.|
|Apply a watermark to everyone's video feed|Can be set to **On** or **Off**. If set to **Off**, then not available in meeting options.|Can enforce or prevent watermarks on participants' video feeds, or leave the setting uncontrolled. Can enforce watermarks even if the admin policy is **Off** for the organizer.|Can enforce or prevent watermarks on participants' video feeds unless the setting is controlled by a sensitivity label. If watermarks are **Off** in the organizer's admin policy, watermarks aren't used in meetings regardless of the template setting.|Meeting organizer can turn **On** or **Off** unless the setting is disabled by admin policy or enforced **On** or **Off** by a meeting template or sensitivity label.|
|Apply a watermark to shared content|Can be set to **On** or **Off**. If set to **Off**, then not available in meeting options.|Can enforce or prevent watermarks on content shared on screen or leave the setting uncontrolled. Can enforce watermarks even if the admin policy is **Off** for the organizer.|Can enforce or prevent watermarks on content shared on screen unless the setting is controlled by a sensitivity label. If watermarks are **Off** in the organizer's admin policy, watermarks aren't used in meetings regardless of the template setting.|Meeting organizer can turn **On** or **Off** unless the setting is disabled by admin policy or enforced **On** or **Off** by a meeting template or sensitivity label.|
|End-to-end encryption|Can be set to **Not enabled, but users can enable** or **Not enabled**. If set to **Not enabled**, then not available in meeting options.|Can enforce or prevent end-to-end encryption or leave the setting uncontrolled. Can enforce end-to-end encryption even if the admin policy is **Not enabled** for the user.|Can enforce or prevent end-to-end encryption unless the setting is controlled by a sensitivity label. If end-to-end encryption is **Not enabled** in the organizer's admin policy, end-to-end encryption isn't used in meetings regardless of the template setting.|Meeting organizer can turn **On** or **Off** unless the setting is set to **Not enabled** by admin policy or enforced **On** or **Off** by a meeting template or sensitivity label.|
|Manage what attendees see|No setting|No setting|Can be set to **On** or *Off* and can enforce the setting or allow the meeting organizer to change it.|Meeting organizer can turn **On** or **Off** unless the setting is enforced **On** or **Off** by a meeting template.|
|Meeting chat|Can be set to **On**, **Off**, or **On for everyone except anonymous participants**. If set to **Off**, then the chat setting is disabled for all meeting the user organizes.|If enabled by admin policy, can enforce chat to be **On**, **Off**, or **In-meetingonly**, or leave the setting uncontrolled.|If enabled in admin policy and not controlled by a sensitivity label, can be set to **On**, **Off**, or **In-meeting only**. Setting can be enforced or meeting organizer can be allowed to change.|If enabled by admin policy and not enforced by a sensitivity label or template, meeting owner can set to **On**, **Off**, or **In-meeting only**.|
|People dialing in can bypass the lobby|Sets the default setting for new meetings.|If the label is controlling who can bypass the lobby, this setting is enforced **On** or **Off**, otherwise it's uncontrolled.|If not controlled by a sensitivity label, can be set to **On** or **Off**. Setting can be enforced or meeting organizer can be allowed to change.|If not enforced by a sensitivity label or template, meeting owner can set to **On** or **Off**.|
|Prevent copying chat content to clipboard*|Copy prevention can be disabled (but not enforced) by admin policy. Admin policy is overridden by sensitivity label if used.|Can prevent the meeting chat from being copied or forwarded. |If enabled in admin policy and not controlled by a sensitivity label, can be set to **On** or **Off**. Setting can be enforced or meeting organizer can be allowed to change.|Meeting organizer can turn **On** or **Off** unless setting is disabled by admin policy or enforced by sensitivity label or template.|
|Record automatically|Meeting recording can be disabled completely using a meeting policy, but there's no admin policy for *Record automatically*.|Can enforce or prevent automatic meeting recording or be left uncontrolled. Can enforce automatic recording even if admin policy for recording is **Off**.|If meeting recording is allowed by admin policy and automatic recording isn't controlled by a sensitivity label, can be set to **On** or **Off** and can enforce the setting or allow the meeting organizer to change it.|Meeting organizer can turn **On** or **Off** unless the setting is enforced **On** or **Off** by a meeting template or sensitivity label or admin policy prevents recording.|
|Who can bypass the lobby|Sets the default setting for new meetings.|Can enforce a particular option for who can bypass the lobby, or can be left uncontrolled.|If not controlled by a sensitivity label, selects a setting for who can bypass the lobby. Setting can be enforced or meeting organizer can be allowed to change.|Meeting organizer can choose who can bypass the lobby unless the setting is enforced by a label or template.|
|Who can present|Sets the default setting for new meetings. Available values are **Everyone**, **People in my org and guests**, and **Only organizers and co-organizers**.|Can enforce settings of **Everyone**, **People in my org and guests**, **Let meeting organizer select specific people**, or **Only organizers and co-organizers**, or can be left uncontrolled.|No setting|Meeting organizer can select who can present unless enforced by a sensitivity label.|
|Who can record|Meeting recording can be disabled completely using a meeting policy, but there's no admin policy for *Who can record*.|Can enforce settings of **Organizers and co-organizers** or **Organizers and presenters**, or can be left uncontrolled.|If not controlled by a sensitivity label, selects a setting of **Organizers and co-organizers** or **Organizers, co-organizers, and presenters**. Setting can be enforced or meeting organizer can be allowed to change.|Meeting organizer can choose who can record—**Organizers and co-organizers** or **Organizers, co-organizers, and presenters**—unless the setting is enforced by a label or template.|

**Prevent copying chat content to clipboard* doesn't apply to anonymous participants.

## Admin policies' effect on sensitivity labels and meeting templates

While some admin policies—such as lobby settings and who can present—specify defaults that the meeting organizer can change, most admin policies determine if a given feature is available to users at all.

Sensitivity labels can enforce end-to-end encryption, watermarks, and automatic recording even if the related admin policy is turned off for the meeting organizer. Templates can't do this, however. Admin policies take precedence over template settings.

For example, if you create a *highly sensitive* label and configure it to enforce watermarking and end-to-end encryption, that enforcement will take place even if watermarking and end-to-end encryption are disabled for the meeting organizer in the admin policy. However, if you use a template to turn on watermarking and end-to-end encryption for that same meeting organizer, those features won't be available in the meeting because the admin policy takes precedence over them.

As you plan for your meeting templates and sensitivity labels, ensure that the settings that you want to control with them are enabled in admin policies where required.

## Sensitivity labels and templates together

Some settings are only available in sensitivity labels and some are only available in templates. The following are available in both:

- Chat
- End-to-end encryption
- Lobby settings
- Meeting recording
- Watermarking

Whenever a sensitivity label is used, the settings configured in the label take precedence over any template or meeting organizer settings.

The settings in a sensitivity label can be left uncontrolled when the label is created, allowing a template or the meeting organizer to control these settings.

Sensitivity labels are often used for multiple purposes—labeling documents, sites, and emails, as well as meetings. You can avoid creating additional labels that are just for meetings by using templates along with the labels to account for variations within a particular type of meeting.

For example your marketing department might have different requirements than the research department for sensitive meetings. You can configure the settings that are common to both in a sensitivity label and then make separate templates available to the two groups which further refine the meeting settings for that group. Both templates could use the same label.

## User-based policies and meeting-based policies

Teams policies—including meeting policies—apply at the user or group level. Sensitivity label and template settings apply at the individual meeting level where those labels and templates are used. Consider where it makes sense to configure settings in Teams admin policies versus sensitivity labels or templates.

Here are a few examples:

If you want different default lobby settings for the research department and the marketing department, you can configure these defaults using admin policies and further modify them with labels or templates.

If you want watermarks available only for governance officials, you can enable them only for those people using an admin policy. You can then have templates that enforce watermarking, but the watermarking will only be used in meetings organized by governance officials.

## Different meeting types with the same sensitivity

Using templates and labels together can be useful if you have different types of meetings that have the same sensitivity. For example, if some of your sensitive meetings are interactive and some are presentations where there's minimal interaction from attendees, you can create two templates:

- One to use for presentations that turn off attendee video and audio.
- One to use for interactive meetings that leave video and audio at the discretion of the meeting organizer.

Both templates could use the *Sensitive* label which would control additional settings such as who can bypass the lobby and who can present.

## Specify default values that meeting organizers can change

While labels generally enforce a particular setting, templates can either enforce a setting or allow the meeting organizer to change it. This allows you to implement default settings that meet your compliance needs while giving meeting organizers the option to override the setting if appropriate.

For example, for a baseline level of protection, you might want to use a sensitivity label to turn off watermarking. At the same time, you can use a template to set the default for who can bypass the lobby, but allow the meeting organizer to change the setting if they need to.

You can assign your baseline protection label to the template so that both are used when a meeting organizer chooses that template.

Some admin policies can also be used to set a default value that can be changed by a meeting organizer. These include lobby controls and who can present.

## Related topics

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)
