---
title: Configure Teams meetings with protection for highly sensitive data
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: vivek.mohan
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
description: Learn how to configure Teams meetings for protection for highly sensitive information by using templates and sensitivity labels.
---

# Configure Teams meetings with protection for highly sensitive data

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

For the *highly sensitive* level of protection, we'll look at two different scenarios:

- Highly sensitive meetings where attendees participate and interact with the presenters
- Highly sensitive presentations where attendees don't interact and are just viewing the presentation

> [!NOTE]
> Meeting options in sensitivity labels and custom meeting templates require Teams Premium.

## Highly sensitive meetings

For highly sensitive meetings, we'll restrict who can bypass the lobby, who can present, when participants can chat, and we'll block copying from the meeting chat. We'll also enable end-to-end encryption and watermarking for shared video and content.

The following table describes which actions we'll restrict for highly sensitive meetings and where those options are configured.

|Feature|Option|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow camera for attendees|**On**|Template|No|
|Allow mic for attendees|**On**|Template|No|
|Apply a watermark to everyone's video feed|**On**|Label|Yes|
|Apply a watermark to shared content|**On**|Label|Yes|
|End-to-end encryption|**On**|Label|Yes|
|Manage what attendees see|**On**|Template|Yes|
|Meeting chat|**In-meeting only**|Template|Yes|
|People dialing in can bypass the lobby|**Off**|Label|Yes|
|Prevent copying chat content to clipboard|**On**|Label|Yes|
|Record meetings automatically|**Off**|Template|Yes|
|Who can bypass the lobby?|**Only organizers and co-organizers**|Label|Yes|
|Who can present|**Only organizers and co-organizers**|Label|Yes|
|Who can record|**Only organizers and co-organizers**|Template|No|

Options that are listed as enforced are enforced by the sensitivity label or meeting template. Options that are not enforced can be changed by the meeting organizer.

## Highly sensitive presentations

For highly sensitive presentations - where we don't expect interaction with the meeting attendees - we'll turn off attendees' mics and cameras, and turn off the meeting chat.

If you want to allow attendees to ask questions of the presenter, meeting organizers can turn on the Q&A feature. (Be sure it's enabled in Teams admin meeting policies.)

The following table describes which actions we'll restrict for highly sensitive presentations and where those options are configured.

|Feature|Options|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow camera for attendees|**Off**|Template|Yes|
|Allow mic for attendees|**Off**|Template|Yes|
|Apply a watermark to everyone's video feed|**On**|Label|Yes|
|Apply a watermark to shared content|**On**|Label|Yes|
|End-to-end encryption|**On**|Label|Yes|
|Manage what attendees see|**On**|Template|Yes|
|Meeting chat|**Off**|Template|Yes|
|People dialing in can bypass the lobby|**Off**|Label|Yes|
|Prevent copying chat content to clipboard|**On**|Label|Yes|
|Record meetings automatically|**Off**|Template|Yes|
|Who can bypass the lobby?|**Only organizers and co-organizers**|Label|Yes|
|Who can present|**Only organizers and co-organizers**|Label|Yes|
|Who can record|**Only organizers and co-organizers**|Template|No|

Options that are listed as enforced are enforced by the sensitivity label or meeting template. Options that are not enforced can be changed by the meeting organizer.

## Video demonstration

Watch this video for a walkthrough of the procedures described in this article.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1bXYL]

## Presentation options for highly sensitive meetings

For *highly sensitive* meetings we're enforcing specific options for who can present, as well as how content is shared.

By turning on **Manage what attendees can see**, we ensure that meeting organizers can vet shared content before it's brought on screen for participants. In this example, we're using a template to turn this on by default, but you can also use the template to enforce the value if you need to.

By setting **Who can present** to **Only organizers and co-organizers** in the sensitivity label, we ensure that the only people who can present are those the meeting organizer intends.

## Lobby options for sensitive meetings

We use the sensitivity label to prevent anyone other than meeting organizers from bypassing the lobby. This allows organizers to vet each attendee and ensure that they should be admitted.

## Who can admit from lobby

You can choose to keep the default for **Who can admit from lobby** as **Organizers and presenters** or change it to **Organizers and co-organizers**. This per-organizer policy sets a default that your organizers can change through their **Meeting options**. You must manage this setting through the Teams admin center. Meeting templates and sensitivity labels don't support this policy.

To configure who can admit from lobby:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
2. Select the policy that you want to update.
3. Under **Meeting join & lobby**, for **Who can admit from lobby**, choose either **Organizers and presenters**(default value) or **Organizers and co-organizers**.
4. Select **Save**

## Participation options for highly sensitive meetings

While chat can be controlled with the sensitivity label, we use templates in this case so that the meeting and presentation templates can share the same label. We restrict chat to in-meeting only for meetings and turn it off completely for presentations. (Organizers can use the Q&A feature in presentations to allow audience comments or questions.)

For both meetings and presentations, we also prevent copying chat content to the clipboard.

While we leave attendee mic and camera enabled for meetings, we turn them off for presentations.

## Sensitivity labels

For the *highly sensitive* level of protection, we use a sensitivity label that you can use directly in a meeting or as part of a meeting template. Depending on the configuration you choose, this label can also be used to classify teams and individual files.

If you already have sensitivity labels deployed in your organization, consider how this label fits with your overall label strategy. You can change the name or settings if needed to meet the needs of your organization. If you already have a label that you use for sensitive information, you can edit the label and add Teams meetings to it.

> [!IMPORTANT]
> If a sensitivity label that restricts copying from the chat is specified as the default channel label in a container label, then teams with that container label will restrict copying from the chat for all channels in the team, both in and out of channel meetings.

To create a sensitivity label:

1. Open the [Microsoft Purview compliance portal](https://compliance.microsoft.com).
1. Under **Solutions**, expand **Information protection**, and then select **Labels**.
1. Select **Create a label**.
1. Give the label a name. We suggest **Highly sensitive**, but you can choose a different name if that one is already in use.
1. Add a display name and description, and then select **Next**.
1. On the **Define the scope for this label** page, make sure **Items**, **Files**, **Emails**, and **Meetings** are selected. (Note that you can select other options if you want to use this label for other purposes.)
1. Select **Next**.
1. On the **Choose protection settings for labeled items** page, select **Protect Teams meetings and chats** and then select **Next**
1. On the **Settings for Teams meetings and chats** page, choose the following values:
    1. Select **Control who can bypass the lobby** and select **Only organizers and co-organizers** from the dropdown list.
    1. Ensure that **People dialing in can bypass the lobby** is unchecked
    1. Select **Control who can present** and select **Only organizers and co-organizers** from the dropdown list.
    1. Select **Control end-to-end encryption for meeting video and audio** and then select **Apply end-to-end encryption**.
    1. Select **Control watermarks** and then select **Apply watermark to shared content** and **Apply watermark to everyone's video feed**.
    1. Select **Prevent copying chat content to clipboard**.
    1. Configure any other settings that you need for your organization.

       :::image type="content" alt-text="Screenshot of meeting sensitivity label settings showing configuration in this procedure." source="media/teams-meeting-sensitivity-label-highly-sensitive-small.png":::

1. Select **Next**.
1. Complete the wizard with any additional settings you want to use, select **Create label**, and then select **Done**.

Once you've created the label, you need to publish it to the users who will use it. For highly sensitive protection, we make the label available to all users. You publish the label in the Microsoft Purview compliance portal, on the **Label policies** page under **Information protection**. If you have an existing policy that applies to all users, add this label to that policy. If you need to create a new policy, see [Publish sensitivity labels by creating a label policy](/purview/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy).

For additional information about using sensitivity labels with meetings, see [Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings).

## Meeting templates

In the *highly sensitive* level of protection, we're configuring the following options by using a meeting template:

- **Enable camera for attendees** - **On** but not enforced for meetings and enforced **Off** for presentations.
- **Enable mic for attendees** - **On** but not enforced for meetings and enforced **Off** for presentations.
- **Manage what attendees can see** - Enforced **On** for both meetings and presentations.
- **Meeting chat** - Enforced to **In-meeting only** for meetings and enforced to **Off** for presentations.

Since these options differ between meetings and presentations, we'll create one template for meetings and another for presentations. Both templates can use the sensitivity label that we create above.

### Highly sensitive meetings template

To create a meeting template for highly sensitive meetings

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. Set **Record meetings automatically** to **Off** and then select the option and select **Lock**.
1. Set **Who can record** to **Only organizers and co-organizers**.
1. Set **Meeting chat** to **In-meeting only** and then select the option and select **Lock**.
1. Set **Manage what attendees see** to **On** and then select the option and select **Lock**.
1. Change any additional options if desired.
1. To prevent the meeting organizer from changing an option, select the option and then select **lock**.
1. To prevent the meeting organizer from seeing an option, select the option and then select **Hide**.
1. Select **Save**.

### Highly sensitive presentations template

To create a meeting template for highly sensitive presentations

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. Set **Allow mic for attendees** to **Off** and then select the option and select **Lock**.
1. Set **Allow camera for attendees** to **Off** and then select the option and select **Lock**.
1. Set **Record meetings automatically** to **Off** and then select the option and select **Lock**.
1. Set **Who can record** to **Only organizers and co-organizers**.
1. Set **Meeting chat** to **Off** and then select the option and select **Lock**.
1. Set **Manage what attendees see** to **On** and then select the option and select **Lock**.
1. Change any additional options if desired.
1. To prevent the meeting organizer from changing an option, select the option and then select **lock**.
1. To prevent the meeting organizer from seeing an option, select the option and then select **Hide**.
1. Select **Save**.

## Related topics

- [Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)
- [Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)
- [Use Teams meeting templates, sensitivity labels, and admin policies together for sensitive meetings](meeting-templates-sensitivity-labels-policies.md)
- [Use sensitivity labels to protect calendar items, Teams meetings and chat](/microsoft-365/compliance/sensitivity-labels-meetings)
