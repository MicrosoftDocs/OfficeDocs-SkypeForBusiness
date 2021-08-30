---
title: Export a ServiceNow instance to the Teams Rooms managed service portal
author: cazawideh
ms.author: czawideh
manager: serdars
ms.reviewer: 
ms.topic: article
ms.service: msteams
audience: Admin
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
localization_priority: Normal
description: Learn about exporting a ServiceNow instance to the Teams Rooms managed service portal
f1keywords: 
---

# Export a ServiceNow instance to the Teams Rooms Managed Services

This article will provide the prerequisites and configuration steps to integrate ServiceNow IT service management into the Microsoft Teams Rooms Managed Services portal.

## Prerequisites

To integrate ServiceNow into the Teams Rooms Managed Services portal, you must meet the following prerequisites:

**For Teams Rooms, you need**

- Service Administrator role set up. For more information on roles, see [Role-based access control with the Microsoft Teams Rooms Managed Services](microsoft-teams-rooms-premium-rbac.md).

**For ServiceNow, you need**

- A Basic Authorization sign-in, OR sign in through OAuth
- A service now instance and its Instance Host name and API URI
  - For customers with customized URL/API endpoints....
- A role of incident_manager or higher
- A software version that supports Table API

## Configure your environment

How your environment is configured highly customizable and will depend on your business needs. The following steps walk through how to copy your existing configuration in ServiceNow to the Teams Rooms Managed Services portal.

1. Open the ServiceNow instance you want to export. You'll need to reference this as you complete the configuration form in the Teams Rooms Managed Services portal.
2. In a new browser tab, go to the Teams Rooms Managed Services portal and go to **Settings**. Then, select **ServiceNow** in the left navigation menu to open the Configuration Form.
3. Select an authentication method to sign in and enter your ServiceNow Instance Host and API URI.
4. All required items in the ServiceNow Field column of the Field Mapping section should be pre-filled. The table below contains each ServiceNow field and its corresponding Microsoft Teams Rooms field. Complete the action for each row of the Field Mapping section. For definitions of each ServiceNow field, see ServiceNow field definitions

| **ServiceNow field** | **Microsoft Teams Rooms field** | **Action** |
| --- | --- | --- |
| Short description | Incident description | No action needed. The Teams Rooms field is auto-filled. |
| Description | First Message | No action needed. The Teams Rooms field is auto-filled. |
| Assignment group | Room group | Copy the assignment\_group value in your ServiceNow instance and paste it into the ServiceNow Value field in the Configuration Form. If you have more than one assignment\_group, select **Add Room Group** for each additional custom value. |
| Severity | Rings | Severity is a custom value in ServiceNow. It will be the fourth item in the second column of your ServiceNow instance. Copy the value and paste it into the ServiceNow value field in the Configuration Form. If you have more than one severity value, select **Add Ring** for each additional custom value. |
| Comments (optional) | Custom value* | To add a comments field to the Configuration Form, select **Add** at the top of the Field Mapping section. Copy the comment value in your ServiceNow instance and paste it to the ServiceNow field in the configuration form. Assign it a Microsoft Teams Room field from the dropdown menu, and copy and paste the ServiceNow value. |
| State (resolved) | Custom value* | Copy the resolution state from your ServiceNow instance and paste it into the ServiceNow value field in the configuration form. |
| Close code | Custom value* | In the Resolution Information tab of your ServiceNow instance, copy the close code and paste it into the ServiceNow value field into the configuration form. |

*Select custom values from the dropdown menu

>[!NOTE]
>If you're having trouble locating custom values, contact your ServiceNow administrator.

To add additional required fields to Resolve Incident section, select **Add**.

## Test and enable your ServiceNow configuration

After completing the configuration form, select **Test** at the bottom of the page. Testing is required to submit your configuration.

Once your test passes successfully, select **Submit** to save your changes. Once you're ready to enable service now for your organization, switch the **Do you want to enable ServiceNow?** toggle to **On**.
