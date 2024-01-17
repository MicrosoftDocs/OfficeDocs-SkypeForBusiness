---
title: User requests for admins
author: ashishguptaiitb
ms.author: guptaashish
manager: prkosh
ms.topic: how-to
ms.service: msteams
ms.subservice: teams-apps
audience: admin
ms.date: 12/07/2023
ms.collection: 
  - M365-collaboration
  - tier2
  - highpri
ms.reviewer: eddieqiao
search.appverid: MET150
f1keywords: 
  - ms.teamsadmincenter.manageapps.overview
description: Learn how to manage and configure user request for approval of the apps that are blocked in an organization.
appliesto: 
- Microsoft Teams
ms.localizationpriority: high
---
# View and manage user requests

The apps that are blocked in your organization may affect user productivity and collaboration. Users can't use blocked apps but can view such apps and app information in the Teams store. Teams lets users request an approval from admins to allow the usage of blocked apps. After you evaluate an app, you can either allow it or dismiss the requests.

This functionality provides you with a signal about the demand for an app within your organization. You can easily view the aggregate number of requests for each requested app. It helps you make an informed decision about which apps to evaluate for allowing.

You can't hide blocked apps, but you retain complete control of the apps that users can or can't use. If you choose to allow an app, the controls and user interface to manage apps remain the same.

* The default option sends the user requests to Teams admin center. You can [view user requests](#view-user-requests-in-teams-admin-center) and [allow the requested apps](#act-on-the-user-requests-to-allow-apps).

   :::image type="content" source="media/user-request-blocked-apps.png" alt-text="Screenshot showing the option to request an admin to approve a blocked app.":::

* Admin center lets you [configure the user request experience](#receive-user-requests-on-your-custom-webpage) that is best suited for your organization. You can provide an instruction or a custom message that displays for each blocked app and user requests are made on an org-specific URL.

   :::image type="content" source="media/user-request-blocked-apps-redirected.png" alt-text="Screenshot showing the user experience for apps in store when an admin redirects the allow app request URL to an org-specific URL.":::

>[!NOTE]
> The feature isn't supported in Government Community Cloud (GCC), GCC-High, and Department of Defense (DoD) tenants. It isn't supported for custom apps.

## View user requests in Teams admin center

You can view the user requests at the following UIs:

* To quickly see a list of up to three most requested apps, see the notification in the [Teams admin center dashboard](https://admin.teams.microsoft.com/dashboard).

   :::image type="content" source="media/tac-dashboard-user-requests.png" alt-text="Screenshot showing the user request review option on the admin center dashboard." lightbox="media/tac-dashboard-user-requests-large.png":::

* To know the number of requests received for each app, see the [Manage apps page](https://admin.teams.microsoft.com/policies/manage-apps?category=userAppRequest). You can sort the **Requests by users** column or use the **App requests** category filter.

   :::image type="content" source="media/user-requests-tac.png" alt-text="Screenshot showing the column for user requests in Teams admin center and that it can be sorted." lightbox="media/user-requests-tac-expanded.png":::

* To view email contact of each requester of an app, see the **User requests** tab in the app details page.

   :::image type="content" source="media/user-request-allow-apps-options.png" alt-text="Screenshot showing the user requests tab in the app details page and the admin actions needed to allow an app.":::

We recommend a regular triage to check for user requests. To view and manage the requests and to allow a requested app, follow these steps:

1. Sign into the Teams admin center and go to **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps).

1. Choose to display the **Requests by users** column if the Manage apps page doesn't display it. You can sort the column.

1. To view details of the requests of a specific app, use any one of the following methods:

   * On the admin center dashboard, select **Review** in the widget.
   * On the Manage apps page, click the number of requests in **Requests by users** column.
   * On the app details page, select the **User requests** tab.

## Act on the user requests to allow apps

After you evaluate an app, you can either allow it or ignore the requests. To allow an app, follow these steps:

1. Sign into the Teams admin center and go to **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps).

1. Open the app details page for the requested app.

1. Select **Manage requests** or select the **User requests** tab.

1. Follow the options that are displayed to allow the app. These options vary based on the method you used to block it as admin center displays only the relevant options. Follow one or more of the following steps to allow the app:

   * If the app is blocked using permission policies, [modify the permission policies](teams-app-permission-policies.md).
   * If the app is blocked for all users, [allow the app](manage-apps.md#allow-or-block-apps).
   * If third-party apps are blocked for the entire organization, [modify Org-wide app settings](manage-apps.md#manage-org-wide-app-settings).

   :::image type="content" source="media/user-request-allow-apps-options.png" alt-text="Screenshot showing the user requests tab in the app details page and the admin actions needed to allow an app.":::

After you allow an app, the following happens:

* Users can see the **Add** option for the allowed app in the Teams app store.
* Teams doesn't inform requesters when admins act on their requests. We recommend manually letting the requesters know of your decision and action, especially if you approve an app for use. Use the requesters' contact email before you [dismiss the requests](#dismiss-user-requests).
* The request counter doesn't reset after you approve an app. To reset it and remove all requests, you can [dismiss the requests](#dismiss-user-requests).

## Receive user requests on your custom webpage

Teams provides a default message for users to request approval to an app. You can modify the default setting to add a custom message with instructions, org-specific URL, or both. The modifications are displayed for each app in Teams store.

To configure a custom message and redirect users to an org-specific URL, follow the steps:

1. Sign into the Teams admin center and go to **Teams apps** > [**Manage apps**](https://admin.teams.microsoft.com/policies/manage-apps).

1. At the upper-right corner, select **Org-wide app settings**.

1. To display a custom message or instruction in Teams store, enter a text message in text field under **User requests configuration**. The field has a limit of 300 characters.

1. To provide an org-specific URL to collect user requests, follow the steps:

   1. Turn on the **Redirect requests to external link** toggle.
   1. Provide your org-specific URL.

      :::image type="content" source="media/user-request-config-org-wide-setting.png" alt-text="Screenshot to toggle the customization of URL for the user requests in the Org-wide app settings UI.":::

1. Select **Save**.

If you choose to use this custom method to receive requests, the methods to evaluate apps and govern the requested apps remain the same.

## Dismiss user requests

To dismiss the requests, select the **Dismiss all** option available in the **User requests** tab in the app details page. 

When you dismiss requests for an app, the following happens:

* You can't view the name and email or the requesters.
* Teams doesn't inform the requesters that their request is acted upon.
* Requests count in the admin center resets to zero.
* Users can again request the same app to be allowed, after a few hours of you dismissing requests.

## Related article

* [Overview of how to manage third-party apps](manage-apps.md)
