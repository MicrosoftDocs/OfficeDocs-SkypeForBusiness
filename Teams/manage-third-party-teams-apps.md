---
title: Manage access to Teams apps across Microsoft 365
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-apps
audience: Admin
ms.date: 10/24/2022
ms.collection: 
  - M365-collaboration
f1.keywords: 
  - NOCSH
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
search.appverid: MET150
description: Learn how to manage access to Teams apps across Microsoft 365.
---

# Manage access to Teams apps across Microsoft 365

App developers can enhance their Microsoft Teams apps to work in Outlook and on Office.com, in addition to the app working in Teams. The end-users can use the enhanced apps on Teams, in Microsoft Outlook and Microsoft Office.com after the enhancement. Currently, only the end-users in [Targeted release](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true) can view and use these specific apps in Teams, Outlook, and Office.com. A notification about this change is available in the [message center](https://admin.microsoft.com/AdminPortal/Home#/MessageCenter/:/messages/MC334280).

## Manage user's access to the enhanced apps

The existing Teams admin experience applies to govern access to these apps. Teams admins use the Teams admin center to manage app access. As a Teams administrator, you can allow specific end-users to use the enhanced apps or manage their access to the enhanced apps in Teams, in Outlook, and on Office.com.

For use in Outlook and Office.com, an enhanced app continues to use the existing permissions granted in Teams. There's no change in the permissions of the enhanced app. Users who have installed existing in-market add-ins of the same app in Outlook and Office will continue to use that app. The add-ins are not Teams apps and Teams admins cannot govern the access.

Office Apps admins can contact the Global admin or the Teams admin to manage access of the enhanced apps. For more information, see [admin roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true).

You can control end-user access using the following methods.

| Options to manage access |Portal|Global admin|Teams administrator|
|--|---|---|--|
| Only the end-users in Targeted release can access the new app. Move the users to Standard release. See [Set up the Standard or Targeted release options](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true) | Microsoft 365 admin center | Yes | No |
| Manage access to the new app for specific end-users. See [Add a custom permission policy](teams-app-permission-policies.md#create-an-app-permission-policy) and [assign the custom policy to a user](policy-assignment-overview.md). | Teams admin center | Yes | Yes |
| Manage access to the new apps for all end-users across your organization. See [Allow or block apps](manage-apps.md#allow-and-block-apps). | Teams admin center | Yes | Yes |

> [!NOTE]
> We recommend using [the Standard release option](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true) to manage end-user access. The other options remove the end-user access and they will no longer be able to use the existing app in Teams.

## List of enhanced apps

The list of enhanced apps is below:

* [Adobe Acrobat Sign](https://teams.microsoft.com/l/app/0f56a9d1-f502-40f9-a9e8-816d7adbb68b)
* [Bigger Brains eLearning](https://teams.microsoft.com/l/app/12345514-afee-abcd-acde-c5b34109abcd)
* [Bookings](https://teams.microsoft.com/l/app/4c4ec2e8-4a2c-4bce-8d8f-00fc664a4e5b)
* [e2e-assure](https://teams.microsoft.com/l/app/8bdf3437-e038-4a93-abdc-00461630f6c3)
* [ESi-Tik](https://teams.microsoft.com/l/app/fe9627db-f23e-42b1-b454-d4d1ca5af33e)
* [Go1](https://teams.microsoft.com/l/app/c859de61-8a6b-42e6-ba88-f639df33bc72)
* [Lens](https://teams.microsoft.com/l/app/cfaeb687-adc7-4e36-a847-39bb35bfb631)
* [Monday.com](https://teams.microsoft.com/l/app/eab2d3ce-6d6a-4415-abc4-5f40a8317b1f)
* [Mural](https://teams.microsoft.com/l/app/c738b607-88dd-4f16-aefe-6a824c65d25d)
* [My Stickers](https://teams.microsoft.com/l/app/46fae4d0-faf5-11e9-80f3-53ad33b77bce)
* [PDF Tools](https://teams.microsoft.com/l/app/ca4b5141-5c46-47bc-a05e-2733d9bd69aa)
* [Power BI](https://teams.microsoft.com/l/app/1c4340de-2a85-40e5-8eb0-4f295368978b)
* [Priority Matrix](https://teams.microsoft.com/l/app/5be2b320-a5b7-4221-893c-dee506e4e365)
* [Smart Connect for Jira](https://teams.microsoft.com/l/app/6402de97-ce33-4386-bf28-b37e9e139c09)
* [Soon scheduling](https://teams.microsoft.com/l/app/bf280b0d-b87d-4158-9f2a-70b63674cd27)
* [Streamline](https://teams.microsoft.com/l/app/aa6e7fb6-34ac-4947-9c13-3565c66e368b)
* [SurveyMonkey](https://teams.microsoft.com/l/app/0fd925a0-357f-4d25-8456-b3022aaa41a9)
* [Transcription Assistant TNA2](https://teams.microsoft.com/l/app/32c31ccd-b878-470e-9259-98c079ae5528)
* [Umbiko](https://teams.microsoft.com/l/app/23fc1de6-dda0-4043-9ebb-a555e845843d)
* [Waldo](https://teams.microsoft.com/l/app/1d041f16-ab49-4627-bfda-6b60ad2cab6a)
* [YouTube](https://teams.microsoft.com/l/app/com.microsoft.teamspace.tab.youtube)
* [Zoho Projects](https://teams.microsoft.com/l/app/4a39aea9-8537-4c2f-b66d-ca364eb3b80d)

## Related articles

* [Microsoft Teams apps designed for Microsoft 365 coming in Preview to Outlook and Office.com](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-teams-apps-designed-for-microsoft-365-coming-in/ba-p/3269538)
* [Understand admin roles in Microsoft 365](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide&preserve-view=true)  
* [About Outlook add-ins](/office/dev/add-ins/outlook/outlook-add-ins-overview)
* [How developers extend Teams apps to work across Microsoft 365](/microsoftteams/platform/m365-apps/overview)
