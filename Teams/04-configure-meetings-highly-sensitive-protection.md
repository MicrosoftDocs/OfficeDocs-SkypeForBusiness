---
title: Configure Teams meetings with protection for highly sensitive data
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
appliesto: 
  - Microsoft Teams
description: 
---

# Configure Teams meetings with protection for highly sensitive data

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

For the *highly sensitive* level of protection, we'll look at two different scenarios:
- Highly sensitive meetings where attendees participate and interact with the presenters
- Highly sensitive presentations where attendees don't interact and are just viewing the presentation


restrict who can bypass the lobby, who can present, and who can record. You can restrict additional actions as well if your organization requires it.




The following table describes which actions we'll restrict for sensitive meetings and where those settings are configured.

Highly sensitive meetings

|Feature|Setting|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow chat|**In-meeting only**|Template|Yes|
|Allow dial-in users to bypass the lobby|**Off**|Label|Yes|
|Disable camera for attendees|**Off**|Template|No|
|Disable mic for attendees|**Off**|Template|No|
|End-to-end encryption|**On**|Label|Yes|
|Manage what attendees see|**On**|Template|Yes|
|Prevent copying chat content to clipboard|**On**|Label|Yes|
|Record automatically|**Off**|Label|No|
|Watermark camera streams|**On**|Label|Yes|
|Watermark screenshare|**On**|Label|Yes|
|Who can bypass the lobby|**Only me and co-organizers**|Label|Yes|
|Who can present|**Only me and co-organizers**|Label|Yes|
|Who can record|(Disabled due to watermarking)|N/A|N/A|


Highly sensitive presentations

|Feature|Setting|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow chat|**Disabled**|Template|Yes|
|Allow dial-in users to bypass the lobby|**Off**|Label|Yes|
|Disable camera for attendees|**On**|Template|Yes|
|Disable mic for attendees|**On**|Template|Yes|
|End-to-end encryption|**On**|Label|Yes|
|Manage what attendees see|**On**|Template|Yes|
|Prevent copying chat content to clipboard|**On**|Label|Yes|
|Record automatically|**Off**|Label|No|
|Watermark camera streams|**On**|Label|Yes|
|Watermark screenshare|**On**|Label|Yes|
|Who can bypass the lobby|**Only me and co-organizers**|Label|Yes|
|Who can present|**Only me and co-organizers**|Label|Yes|
|Who can record|(Disabled due to watermarking)|N/A|N/A|

Settings that are listed as enforced are enforced by the sensitivity label or meeting template. Settings that are not enforced can be changed by the meeting organizer.

## Options for recording meetings

In the *highly sensitive* tier, we use watermarking for both meetings and presentations. However, using a watermark prevents recording the meeting. If you have a need to record highly sensitive meetings, we recommend not configuring watermarks as part of the sensitivity label. Watermarks can still be applied by meeting organizers for meetings they don't need to record.

## Sensitivity labels

For the sensitive level of protection, we'll be using a sensitivity label that you can use directly in a meeting or as part of a meeting template. Depending on the configuration you choose, this label can also be used to classify teams and individual files.

If you already have sensitivity labels deployed in your organization, consider how this label fits with your overall label strategy. You can change the name or settings if needed to meet the needs of your organization. If you already have a label that you use for sensitive information, you can edit the label and add Teams meetings to it.

To create a sensitivity label
1. Open the [Microsoft Purview compliance portal](https://compliance.microsoft.com).
1. Under **Solutions**, click **Information protection**.
1. Click **Create a label**.
1. Give the label a name. We suggest **Highly sensitive**, but you can choose a different name if that one is already in use.
1. Add a display name and description, and then click **Next**.
1. On the **Define the scope for this label** page, select **Items** and **Include meetings**. (Note that you can select other options if you want to use this label for other purposes.)
1. Select **Next**.
1. Continue to select the options that you want to use with this label, and then on the **Settings for Teams meetings and chats** page, choose the following values:
    1. **Who can bypass the lobby** - Only me and co-organizers
    1. **Allow dial-in users to bypass the lobby** - Unchecked
    1. **Who can present** - Only me and co-organizers
    1. **End-to-end encryption for meeting video and audio** - On
    1. **Record meetings with this label automatically** - Off
    1. **Video watermark - Apply to screenshare** - On
    1. **Video watermark - Apply to camera streams** - On
    1. **Allow chat** - Let the meeting organizer select from meeting options
    1. **Prevent copying chat content to clipboard** - Unchecked
    :::image type="content" source="media/teams-meeting-sensitivity-label-highly-sensitive-small.png" alt-text="Screenshot of sensitivity label meeting settings." lightbox="media/teams-meeting-sensitivity-label-highly-sensitive-large.png":::    
1. Select **Next**.
1. Complete the wizard with any additional settings you want to use, and then select **Create label**, and then select **Done**.

Once you've created the label, you need to publish it to the users who will use it. For highly sensitive protection, we'll make the label available to all users. You publish the label in the Microsoft Purview compliance portal, on the **Label policies** tab of the **Information protection** page. If you have an existing policy that applies to all users, add this label to that policy. If you need to create a new policy, see [Publish sensitivity labels by creating a label policy](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## Meeting templates

In the *sensitive* level of protection, we're not enforcing any settings by using a meeting template. You can use the label only for sensitive meetings if you want.

An advantage of using templates is that you can create multiple templates that use the same sensitivity label which lock different settings. For example, if some of your sensitive meetings are presentations where there is minimal interaction from attendees, you can create a template that turns off attendee video and even chat, and another template that leaves those options to the meeting organizer. Both templates would use the *Sensitive* label.

To create a meeting template for highly sensitive meetings

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. In the **Meeting engagement** sections, set **Attendees can chat** to **Enabled only in meeting**.
1. Select **Attendees can chat**, and then select **Lock**.
1. Change any additional settings if desired.
1. To prevent the meeting organizer from changing a setting, select the setting and then select **lock**.
1. To prevent the meeting organizer from seeing a setting, select the setting and then select **Hide**.
1. Select **Save**.



To create a meeting template for highly sensitive presentations

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. In the **Audio and video** section, set **Disable mic for attendees** and **Disable camera for attendees** to **On**.
1. Select **Disable mic for attendees** and **Disable camera for attendees** in turn and then select **Lock**.
1. In the **Meeting engagement** sections, set **Attendees can chat** to **Enabled only in meeting**.
1. Select **Attendees can chat**, and then select **Lock**.
1. Change any additional settings if desired.
1. To prevent the meeting organizer from changing a setting, select the setting and then select **lock**.
1. To prevent the meeting organizer from seeing a setting, select the setting and then select **Hide**.
1. Select **Save**.




**Attendees can chat**
**Manage what attendees see**



## Related topics

[Configure Teams meetings with three tiers of protection](01-configure-meetings-three-tiers-protection.md)

[Overview of custom meeting templates in Microsoft Teams](12-custom-meeting-templates-overview.md)

[Use Teams meeting templates with sensitivity labels](11-meeting-templates-with-sensitivity-labels.md)

## Highly sensitive presentations


