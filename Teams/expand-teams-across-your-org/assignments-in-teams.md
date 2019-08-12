---
title: Assignments for Teams
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
ms.reviewer: jastark
f1keywords: ms.teamsadmincenter.assignments.overview
description: Learn how to manage assignments in the Microsoft Teams admin center in Teams for Education.   
localization_priority: Normal
appliesto: 
- Microsoft Teams
---

# Assignments in Teams for Education

Assignments are tasks or units of work assigned to a student or team member in a class as part of their study. You can create assignments within your Teams class.

[Learn more about Assignments](https://support.office.com/article/microsoft-teams-5aa4431a-8a3c-4aa5-87a6-b6401abea114?ui=en-US&rs=en-IE&ad=IE#ID0EAABAAA=Assignments)

## Assignments in the Microsoft Teams admin center

With the admin settings in Microsoft Teams admin center you can turn the following features on or off to be available for students and teachers within your organization. The following are settings related to Assignments:

<a name="#bkemaildigest"> </a>
### Weekly guardian email digest
[!INCLUDE [preview-feature](../includes/preview-feature.md)]

Guardian emails are weekly emails sent to students' parents or guardians. The emails will contain information about assignments from the previous week and for the upcoming week, and will be sent over the weekend. The emails need to be updated by the admins using the School Data Sync feature.

This setting is off by default.

<a name="bkmakecode"> </a>
### MakeCode
MakeCode is a block-based coding platform that brings computer science to life for all students. 

This is a third party product or service that is subject to its own terms and privacy policy. You are responsible for your use of any third party products and services.

This setting is off by default.

[Learn more about MakeCode](https://www.microsoft.com/makecode)

<a name="#turnitin"> </a>
### Turnitin
[!INCLUDE [preview-feature](../includes/preview-feature.md)]

Turnitin is a plagiarism detection service. This is a third party product or service that is subject to its own terms and privacy policy. You are responsible for your use of any third party products and services.

This setting is off by default.

In order to successfully enable Turnitin for your organization, you will need to already have a Turnitin subscription. You will need to input the following additional information, which can be found in your Turnitin admin console:

  * _TurnitinApiKey_: This is a 32-character GUID found in the admin console under Integrations.
  * _TurnitinApiUrl_: This is the HTTPS URL of your Turnitin admin console.

Here are some instructions to help you obtain this information.

The TurnitinApiUrl is the host address of your admin console.
Example. `https://your-tenant-name.turnitin.com`

The admin console is where you can create an integration and an API key associated with the integration.

Select **Integrations** from the side menu, then select **Add Integration** and give the integration a name.
![Screen shot showing adding a new integration](./educationImages/Assignments_mopo_turnitin2.png)

The TurnitinApiKey will be given to you after you follow the prompts. 
Copy the API key and paste it into the Microsoft Teams admin center.  This is the only time you can view the key.
![Screen shot showing copying the API key](./educationImages/Assignments_mopo_turnitin3.png)

Upon clicking the **Save** button in the admin center for this setting, please allow up to 24 hours for these settings to take effect.

[Learn more about the integration between Turnitin and Microsoft Teams](https://www.turnitin.com/products/feedback-studio/microsoft-teams-integration)

[Learn more about Turnitin](https://www.turnitin.com/)
