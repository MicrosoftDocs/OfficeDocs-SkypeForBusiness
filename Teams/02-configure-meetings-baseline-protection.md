---
title: Configure Teams meetings with baseline protection
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
description: Learn how to configure Teams meetings for a baseline level of protection by using templates and sensitivity labels.
---

# Configure Teams meetings with baseline protection

[!INCLUDE[Teams Premium ECM](includes/teams-premium-ecm.md)]

For the *baseline* level of protection, we'll restrict who can bypass the lobby and set a default value for who can present. You can restrict additional actions as well if your organization requires it.

The following table describes which actions we'll restrict for baseline meetings and where those settings are configured.

|Feature|Setting|Location|Enforced|
|:------|:------|:-------|:-------|
|Allow chat|**Enabled**|Label|No|
|Allow dial-in users to bypass the lobby|**Off**|Label|Yes|
|Disable camera for attendees|**Off**|Template|No|
|Disable mic for attendees|**Off**|Template|No|
|End-to-end encryption|**Off**|Label|No|
|Manage what attendees see|**Off**|Template|No|
|Prevent copying chat content to clipboard|**Off**|Label|No|
|Record automatically|**Off**|Label|No|
|Watermark camera streams|**Off**|Label|No|
|Watermark screenshare|**Off**|Label|No|
|Who can bypass the lobby|**People in my organization, people in trusted domains, and guests**|Label|Yes|
|Who can present|**Everyone in the organization, but user can override**|Teams admin center|No|
|Who can record|**Organizers and presenters**|Label|No|

Settings that are listed as enforced are enforced by the sensitivity label or meeting template. Settings that are not enforced can be changed by the meeting organizer.

## Default values for **Who can present**

The default value for **Who can present** is **Everyone**. For the baseline protection tier, we'll set a more secure default of **Everyone in the organization** which meeting organizers can change if they want.

We can set this value with a sensitivity label, but the value will be enforced for any meetings with that label. This setting isn't available in meeting templates, so we'll set it in the Teams admin center.

To configure who can present in meetings
1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to update.
1. Under **Participants & guests**, set **Who can present in meetings** to **Everyone in the organization, but user can override**.
1. Select **Save**.

## Sensitivity labels

For the baseline level of protection, we'll be using a sensitivity label that you can use directly in a meeting or as part of a meeting template. Depending on the configuration you choose, this label can also be used to classify teams and individual files.

If you already have sensitivity labels deployed in your organization, consider how this label fits with your overall label strategy. You can change the name or settings if needed to meet the needs of your organization. If you already have a label that you use for baseline or general protection, you can edit the label and add Teams meetings to it.

To create a sensitivity label
1. Open the [Microsoft Purview compliance portal](https://compliance.microsoft.com).
1. Under **Solutions**, click **Information protection**.
1. Click **Create a label**.
1. Give the label a name. We suggest **Sensitive**, but you can choose a different name if that one is already in use.
1. Add a display name and description, and then click **Next**.
1. On the **Define the scope for this label** page, select **Items** and **Include meetings**. (Note that you can select other options if you want to use this label for other purposes.)
1. Select **Next**.
1. Continue to select the options that you want to use with this label, and then on the **Settings for Teams meetings and chats** page, choose the following values:
    1. **Who can bypass the lobby** - People in my organization, people in trusted domains, and guests
    1. **Allow dial-in users to bypass the lobby** - Unchecked
    1. **Who can present** - Let the meeting organizer select from meeting options
    1. **Who can record** - Organizers and presenters
    1. **End-to-end encryption for meeting video and audio** - Off
    1. **Record meetings with this label automatically** - Off
    1. **Video watermark - Apply to screenshare** - Off
    1. **Video watermark - Apply to camera streams** - Off
    1. **Allow chat** - Enabled
    1. **Prevent copying chat content to clipboard** - Unchecked
    :::image type="content" source="media/teams-meeting-sensitivity-label-baseline-small.png" alt-text="Screenshot of sensitivity label meeting settings." lightbox="media/teams-meeting-sensitivity-label-baseline-large.png":::    
1. Select **Next**.
1. Complete the wizard with any additional settings you want to use, and then select **Create label**, and then select **Done**.

Once you've created the label, you need to publish it to the users who will use it. For baseline protection, we'll make the label available to all users. You publish the label in the Microsoft Purview compliance portal, on the **Label policies** tab of the **Information protection** page. If you have an existing policy that applies to all users, add this label to that policy. If you need to create a new policy, see [Publish sensitivity labels by creating a label policy](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## Meeting templates

In the *baseline* level of protection, there aren't any values that need to be restricted with a meeting template. You can still create a template if there are values that you need to set for your organization or if you want your users to always use a template when creating a meeting.

To create a custom meeting template

1. In the Teams admin center, expand **Meetings** and select **Meeting templates**.
1. Select **Add**
1. Type a name and description for the template.
1. In the **Apply sensitivity label** section, choose the label you created above.
1. Select **Apply sensitivity label**, and then select **Lock**.
1. Change any additional settings if desired.
1. To prevent the meeting organizer from changing a setting, select the setting and then select **lock**.
1. To prevent the meeting organizer from seeing a setting, select the setting and then select **Hide**.
1. Select **Save**.

## Related topics

[Configure Teams meetings with three tiers of protection](configure-meetings-three-tiers-protection.md)

[Overview of custom meeting templates in Microsoft Teams](custom-meeting-templates-overview.md)

[Use Teams meeting templates with sensitivity labels](meeting-templates-with-sensitivity-labels.md)

