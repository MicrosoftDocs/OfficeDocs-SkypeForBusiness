---
title: Configure Teams meetings with protection for sensitive data
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
  - m365initiative-meetings
  - highpri
appliesto: 
  - Microsoft Teams
description: Learn how to configure Teams meetings for protection for sensitive information by using templates and sensitivity labels.
---

# Configure Teams meetings with protection for sensitive data

For the *sensitive* level of protection, we'll restrict who can bypass the lobby, who can present, and who can record. You can restrict additional actions as well if your organization requires it.

The following table describes which actions we'll restrict for sensitive meetings and where those settings are configured.

|Feature|Setting|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow camera for attendees|**On**|Template|No|
|Allow mic for attendees|**On**|Template|No|
|Apply a watermark to everyone's video feed|**Off**|Template|No|
|Apply a watermark to shared content|**Off**|Template|No|
|End-to-end encryption|**Off**|Template|No|
|Manage what attendees see|**On**|Template|No|
|Meeting chat|**On**|Template|No|
|People dialing in can bypass the lobby|**Off**|Template|Yes|
|Prevent copying chat content to clipboard|**Off**|Label|No|
|Record automatically|**Off**|Template|No|
|Who can bypass the lobby|**Only people who were invited**|Label|Yes|
|Who can present|**People in my organization and guests**|Label|Yes|
|Who can record|**Organizer and co-organizers**|Label|Yes|

Settings that are listed as enforced are enforced by the sensitivity label or meeting template. Settings that are not enforced can be changed by the meeting organizer.

> [!Note]
> Meeting settings in sensitivity labels and custom meeting templates require Teams Premium.

## Presentation options for sensitive meetings

For the *sensitive* level of protection we're enforcing specific settings for who can present, as well as how content is shared.

By turning on **Manage what attendees can see**, we ensure that meeting organizers can vet shared content before it's brought on screen for participants. In this example, we're using a template to turn this on by default, but you can also enforce it on in the template if you need to.

By setting **Who can present** to **People in my organization and guests** in the sensitivity label, we remove the chance of anonymous participants presenting in the meeting. You can further restrict this to **Only organizers and co-organizers** if you need to. (We'll do that for the *highly sensitive* level of protection.)

We'll also restrict recording to organizer and co-organizers by using the sensitivity label.

## Lobby options for sensitive meetings

We'll use the sensitivity label to prevent anyone other than invited attendees (people directly invited by the organizer, or to whom an invitation was forwarded) from bypassing the lobby. This gives an extra level of protection by letting the organizer vet anyone not directly sent an invite before admitting them to the meeting. You can further restrict this setting by choosing **Only organizers and co-organizers**. (We'll do that for the *highly sensitive* level of protection.)


## Sensitivity labels

For the sensitive level of protection, we'll be using a sensitivity label that you can use directly in a meeting or as part of a meeting template. Depending on the configuration you choose, this label can also be used to classify teams and individual files.

If you already have sensitivity labels deployed in your organization, consider how this label fits with your overall label strategy. You can change the name or settings if needed to meet the needs of your organization. If you already have a label that you use for sensitive information, you can edit the label and add Teams meetings to it.

To create a sensitivity label
1. Open the [Microsoft Purview compliance portal](https://compliance.microsoft.com).
1. Under **Solutions**, click **Information protection**.
1. Click **Create a label**.
1. Give the label a name. We suggest **Sensitive**, but you can choose a different name if that one is already in use.
1. Add a display name and description, and then click **Next**.
1. On the **Define the scope for this label** page, select **Items** and **Include meetings**. (Note that you can select other options if you want to use this label for other purposes.)
1. Select **Next**.
1. Continue to select the options that you want to use with this label, and then on the **Settings for Teams meetings and chats** page, choose the following values:
    1. Select **Control who can bypass the lobby** and choose **Only people who were invited** from the dropdown list.
    1. Select **Control who can present** and choose **People in my organization and guests** from the dropdown list.
    1. Select **Who can record** and choose **Organizers and co-organizers** from the dropdown list.
    1. Configure any other settings that you need for your organization.
    <!--:::image type="content" source="media/teams-meeting-sensitivity-label-sensitive-small.png" alt-text="Screenshot of sensitivity label meeting settings." lightbox="media/teams-meeting-sensitivity-label-sensitive-large.png":::-->
1. Select **Next**.
1. Complete the wizard with any additional settings you want to use, and then select **Create label**, and then select **Done**.

Once you've created the label, you need to publish it to the users who will use it. For sensitive protection, we'll make the label available to all users. You publish the label in the Microsoft Purview compliance portal, on the **Label policies** tab of the **Information protection** page. If you have an existing policy that applies to all users, add this label to that policy. If you need to create a new policy, see [Publish sensitivity labels by creating a label policy](/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy).

For additional information about using sensitivity labels with meetings, see [Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings).

## Meeting templates

An advantage of using templates is that you can create multiple templates that use the same sensitivity label which lock different settings. For example, if some of your sensitive meetings are presentations where there is minimal interaction from attendees, you can create a template that turns off attendee video and even chat, and another template that leaves those options to the meeting organizer. Both templates would use the *Sensitive* label.

In the *sensitive* level of protection, we'll use the template to prevent people dialing in by phone from bypassing the lobby. If there are certain types of meetings where you want to allow people calling in by phone to bypass the lobby, consider using a separate template with the same label for those meetings.

To create a custom meeting template

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. Make sure **People calling in my phone can bypass the lobby** is set to **Off**, then select it and select **Lock**.
1. Change any additional settings if desired.
1. To prevent the meeting organizer from changing a setting, select the setting and then select **lock**.
1. To prevent the meeting organizer from seeing a setting, select the setting and then select **Hide**.
1. Select **Save**.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)
