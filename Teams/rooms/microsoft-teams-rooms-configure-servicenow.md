---
title: Configure ServiceNow for Teams Rooms
author: donnah007
ms.author: v-donnahill
manager: serdars
ms.reviewer: ronmart
ms.topic: article
ms.service: msteams
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
description: Learn about configuring ServiceNow in the Teams Rooms Premium portal
f1keywords: 
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_MTRP
---

# Configure ServiceNow for Teams Rooms

This article describes the prerequisites and steps to configure your ServiceNow environment in the Teams Rooms Premium portal.

## Watch: Microsoft Teams Rooms — Managed Services Service Now Integration

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4ZK4B]


### Teams Rooms prerequisites

- You must have an assigned Service Administrator role. For more information, see [Role-based access control with the Microsoft Teams Rooms Managed Services](microsoft-teams-rooms-premium-rbac.md).

### ServiceNow prerequisites

- A Basic Authorization sign-in, OR an [OAuth](https://docs.servicenow.com/bundle/rome-platform-administration/page/administer/security/concept/c_OAuthApplications.html) sign-in. For more information, see [Creating Credentials](https://developer.servicenow.com/dev.do#!/training/learning-plans/rome/servicenow_application_developer/app_store_learnv2_rest_rome_creating_credentials) in ServiceNow.
- A ServiceNow instance and its instance host name and API URI
- A role of incident_manager or higher
- A software version of ServiceNow that supports Table API

## Configure your environment

How your environment is configured is highly customizable and will depend on your organization's needs. The following steps walk through how to copy your existing configuration in ServiceNow to the Teams Rooms Premium portal.

1. Open the ServiceNow instance you want to copy. You'll need to reference this as you complete the configuration form in the Teams Rooms Premium portal.
2. In a new browser tab, go to the [Teams Rooms Premium portal](https://portal.rooms.microsoft.com/) and go to **Settings**. Then, select **ServiceNow** in the left navigation menu to open the configuration form.
3. Select an authentication method to sign in and enter your ServiceNow Instance Host and API URI.
4. All required items in the ServiceNow Field column of the Field Mapping section should be pre-filled. The table below contains each ServiceNow field and its corresponding Microsoft Teams Rooms field. Complete the action for each row of the Field Mapping section. For definitions of each ServiceNow field, see [ServiceNow field definitions](#servicenow-field-definitions).

| ServiceNow field | Microsoft Teams Rooms field | Action |
| --- | --- | --- |
| short_description | Incident description | No action needed. The Teams Rooms field is auto-filled. |
| description | First Message | No action needed. The Teams Rooms field is auto-filled. |
| assignment_group | Room group | Copy the assignment_group value in your ServiceNow instance and paste it into the ServiceNow value field in the configuration form. If you have more than one assignment_group, select **Add Room Group** for each additional custom value. |
| severity | Rings | Severity is a custom value in ServiceNow. It's the fourth item in the second column of your ServiceNow instance. Copy the value and paste it into the ServiceNow value field in the configuration form. If you have more than one severity value, select **Add Ring** for each additional custom value. |
| Comments (optional) | Custom value* | To add a comments field to the configuration form, select **Add** at the top of the field  mapping section. Copy the comment value in your ServiceNow instance and paste it to the ServiceNow field in the configuration form. Assign it a Microsoft Teams Room field from the dropdown menu, and copy and paste the ServiceNow value. |
| state (resolved) | Custom value* | Copy the resolution state from your ServiceNow instance and paste it into the ServiceNow value field in the configuration form. |
| close_code | Custom value* | In the **Resolution Information** tab of your ServiceNow instance, copy the close code and paste it into the ServiceNow value field into the configuration form. |

*Select custom values from the dropdown menu

>[!NOTE]
>If you can't locate your custom values, contact your ServiceNow administrator.

To add additional required fields to Resolve Incident section, select **Add**.

## Test and enable

After completing the configuration form, select **Test** at the bottom of the page. Testing is required to submit your configuration.

Once your test passes successfully, select **Submit** to save your changes. Once you're ready to enable ServiceNow for your organization, switch the **Do you want to enable ServiceNow?** toggle to **On**.

## ServiceNow field definitions

- **short_description**: The short description field in ServiceNow is a brief, 160-character alphanumeric value that provides a summary of the incident. Short description is equivalent to incident description in the Teams Rooms Premium portal.

- **description**: The description field in ServiceNow is the first value in the conversation history of a ServiceNow incident. Description is equivalent to First message in the Teams Rooms Premium portal.

- **assignment_group**: The assignment group field in ServiceNow is used to organize incidents. Assignment groups are equivalent to Room groups in the Teams Rooms Premium portal. By default, there is one room group, and more can be added. You decide how many groups there are and how to group your incidents. For example, you might choose to organize your incidents by location.

- **severity**: The severity field in ServiceNow is used to organize incidents by priority. The values that designate priority are customizable. Severity is equivalent to the Ring field in the Teams Rooms Premium portal. To customize rings in the Teams Rooms Premium portal, go to **Updates** in the left navigation menu. Then go to the **Rings** tab and select **Add ring**.

- **comments**: Comments is an optional field in ServiceNow that is used to include custom required fields from your ServiceNow instance in your Teams Rooms Premium portal configuration. The equivalent of comments is a custom value in the Teams Rooms Premium portal.

- **state (resolved)**: The state (resolved) field in ServiceNow is used to designate how an incident was resolved and is required to close an incident. The state (resolved) value is customizable. The equivalent of state (resolved) is a custom value in the Teams Rooms Premium portal.

- **close_code**: A close code must be assigned to an incident once it's completely resolved. This value is customizable in ServiceNow. The equivalent of close code is a custom value in the Teams Rooms Premium portal.
