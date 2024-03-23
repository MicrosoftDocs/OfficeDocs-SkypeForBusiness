---
title: Configure Teams meetings with protection for sensitive data
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
description: Learn how to configure Teams meetings for protection for sensitive information by using templates and sensitivity labels.
---

# Configure Teams meetings with protection for sensitive data

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

For the *sensitive* level of protection, we'll restrict who can bypass the lobby, who can present, and who can record. You can restrict other actions as well if your organization requires it.

The following table describes which actions we'll restrict for sensitive meetings and where those options are configured.

|Feature|Option|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow camera for attendees|**On**|Template|No|
|Allow mic for attendees|**On**|Template|No|
|Apply a watermark to everyone's video feed|**Off**|Template|No|
|Apply a watermark to shared content|**Off**|Template|No|
|End-to-end encryption|**Off**|Template|No|
|Manage what attendees see|**On**|Template|Yes|
|Meeting chat|**On**|Template|No|
|People dialing in can bypass the lobby|**Off**|Label|Yes|
|Prevent copying chat content to clipboard|**Off**|Label|No|
|Record automatically|**Off**|Template|No|
|Who can bypass the lobby?|**People who were invited**|Label|Yes|
|Who can present|**People in my org and guests**|Label|Yes|
|Who can record|**Organizer and co-organizers**|Label|Yes|

Options that are listed as enforced are enforced by the sensitivity label or meeting template. Options that are not enforced can be changed by the meeting organizer.

> [!NOTE]
> Meeting options in sensitivity labels and custom meeting templates require Teams Premium.

## Video demonstration

Watch this video for a walkthrough of the procedures described in this article.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1c0sf]

## Presentation options for sensitive meetings

For the *sensitive* level of protection we're enforcing specific options for who can present, and how content is shared.

By turning on **Manage what attendees can see**, we ensure that meeting organizers can vet shared content before it's brought on screen for participants. In this example, we're using a template to turn this on by default, but you can also use the template to enforce the value if you need to.

By setting **Who can present** to **People in my organization and guests** in the sensitivity label, we remove the chance of anonymous participants presenting in the meeting. You can further restrict this to **Only organizers and co-organizers** if you need to. (We do that for the *highly sensitive* level of protection.)

We also restrict recording to organizer and co-organizers by using the sensitivity label.

## Lobby options for sensitive meetings

We use the sensitivity label to prevent anyone other than invited attendees (people directly invited by the organizer, or to whom an invitation was forwarded) from bypassing the lobby. This gives an extra level of protection by letting the organizer vet anyone not directly sent an invite before admitting them to the meeting. You can further restrict this option by choosing **Only organizers and co-organizers**. (We do that for the *highly sensitive* level of protection.)

## Sensitivity labels

For the sensitive level of protection, we use a sensitivity label that you can use directly in a meeting or as part of a meeting template. Depending on the configuration you choose, this label can also be used to classify teams and individual files.

If you already have sensitivity labels deployed in your organization, consider how this label fits with your overall label strategy. You can change the name or settings if needed to meet the needs of your organization. If you already have a label that you use for sensitive information, you can edit the label and add Teams meetings to it.

To create a sensitivity label
1. Open the [Microsoft Purview compliance portal](https://compliance.microsoft.com).
1. Under **Solutions**, expand **Information protection**, and then select **Labels**.
1. Select **Create a label**.
1. Give the label a name. We suggest **Sensitive**, but you can choose a different name if that one is already in use.
1. Add a display name and description, and then select **Next**.
1. On the **Define the scope for this label** page, make sure **Items**, **Files**, **Emails**, and **Meetings** are selected. (Note that you can select other options if you want to use this label for other purposes.)
1. Select **Next**.
1. On the **Choose protection settings for labeled items** page, select **Protect Teams meetings and chats** and then select **Next**
1. On the **Settings for Teams meetings and chats** page, choose the following values:
    1. Select **Control who can bypass the lobby** and choose **People who were invited** from the dropdown list.
    1. Clear the **People dialing in can bypass the lobby** check box.
    1. Select **Control who can present** and choose **People in my org and guests** from the dropdown list.
    1. Select **Control who can record** and choose **Only organizers and co-organizers** from the dropdown list.
    1. Configure any other settings that you need for your organization.

       :::image type="content" alt-text="Screenshot of meeting sensitivity label settings showing configuration in this procedure." source="media/teams-meeting-sensitivity-label-sensitive-small.png":::

1. Select **Next**.
1. Complete the wizard with any other settings you want to use, select **Create label**, and then select **Done**.

Once you've created the label, you need to publish it to the users who will use it. For sensitive protection, we make the label available to all users. You publish the label in the Microsoft Purview compliance portal, on the **Label policies** page under **Information protection**. If you have an existing policy that applies to all users, add this label to that policy. If you need to create a new policy, see [Publish sensitivity labels by creating a label policy](/purview/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy).

For more information about using sensitivity labels with meetings, see [Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings).

## Meeting templates

An advantage of using templates is that you can create multiple templates that use the same sensitivity label but which lock different options. For example, if some of your sensitive meetings are presentations where there is minimal interaction from attendees, you can create a template that turns off attendee video and even chat, and another template that leaves those options to the meeting organizer. Both templates would use the *Sensitive* label.

In the *sensitive* level of protection, we use the template to set **Manage what attendees see** to **On** and enforce that value. (This option isn't available in sensitivity labels.) This will give the meeting organizer the ability to manage how content is shown to meeting participants. If there are certain types of meetings where you want to allow the organizer to change this option, consider using a separate template with the same label for those meetings.

To create a custom meeting template

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. Under **Meeting engagement**, set **Manage what attendees see** to **On**, then select it and select **Lock**.
1. Change any additional options if desired.
1. To prevent the meeting organizer from changing an option, select the option and then select **lock**.
1. To prevent the meeting organizer from seeing an option, select the option and then select **Hide**.
1. Select **Save**.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)
